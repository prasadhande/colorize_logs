# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

Installation
Add this line to your application’s Gemfile:

gem "colorize_logs"
If bundler is not being used to manage dependencies, install the gem by executing:

$ gem install colorize_logs
Usage
Create an initializer file config/initializers/colorize_logs.rb and add the following code:

# frozen_string_literal: true

colorize_logs_formatter = ColorizeLogs::Formatter.new

colorize_logs_formatter.configure do
  match(/Processing by/) do |msg|
    msg.red
  end

  match(/Rendering layout/) do |msg|
    msg.green
  end

  match(/Rendering.*within layouts/) do |msg|
    msg.green
  end
end

::Rails.logger.formatter = colorize_logs_formatter
That's it. Restart your server and you should see the logs in different colors.
