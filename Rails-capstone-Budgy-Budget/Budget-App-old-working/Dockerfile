# Use the official Ruby image as the base image
FROM ruby:3.1.2

# Set the working directory inside the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    nodejs \
    npm \
    postgresql-client

# Copy the Gemfile and Gemfile.lock into the container
COPY Gemfile Gemfile.lock ./

# Install Ruby dependencies
RUN gem install bundler && bundle install --jobs 20 --retry 5

# Copy the Rails application into the container
COPY . .

# Install JavaScript dependencies
RUN npm install

# Set up the database
#RUN bundle exec rails db:prepare

# Start the Rails server
CMD bundle exec rails s -b 0.0.0.0
