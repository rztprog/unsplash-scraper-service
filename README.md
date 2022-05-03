# Unsplash-scraper-service

If you want a random unsplash url image scraper without the Unsplash API in Ruby, you can use this.

## Requirements

1. Gem open-uri
2. Gem nokogiri

## How to use

1. Change the keyword in the rb file to search wathever you want
2. Put the rb file in initializer and call him with UnsplashScraperService.new.call

## Example for seed in rails

```
require "faker"
require_relative "../config/initializers/unsplash_scraper_service"

puts "How much Flat(s) you want ?"
loop_n = STDIN.gets.chomp

loop_n.to_i.times do
  flat = Flat.new(
    name: "#{Faker::Address.community} in #{Faker::Address.city}",
    address: Faker::Address.full_address,
    description: Faker::GreekPhilosophers.quote,
    price_per_night: Faker::Number.within(range: 30..120),
    number_of_guests: Faker::Number.within(range: 2..10),
    picture: UnsplashScraperService.new.call
  )
  flat.save!
end
```
