---
title: Appendix - Sources
---


## Directory Structure

Full source code listings for the `how_i_start` gem v1.0:

```
|   Gemfile
|   how_i_start.gemspec
|   LICENSE.txt
|   Rakefile
|   README.md
|
+---bin/
|     how_i_start
|
+---lib/
|   |  how_i_start.rb
|   |
|   \---how_i_start/
|         version.rb
|
\---test/
      url_test.rb
```


## Gemfile

```ruby
source 'https://rubygems.org'

# Specify your gem's dependencies in how_i_start.gemspec
gemspec
```

## how_i_start.gemspec

```ruby
# coding: utf-8
lib = File.expand_path('../lib', __FILE__)
$LOAD_PATH.unshift(lib) unless $LOAD_PATH.include?(lib)
require 'how_i_start/version'

Gem::Specification.new do |spec|
  spec.name          = "how_i_start"
  spec.version       = HowIStart::VERSION
  spec.authors       = ["Steve Klabnik"]
  spec.email         = ["steve@steveklabnik.com"]
  spec.summary       = %q{A simple gem, to show you how I do things.}
  spec.description   = %q{A simple gem, to show you how I do things. If it were more complicated, I'd explain more about it here.}
  spec.homepage      = "https://steveklabnik.github.io/how_i_do_things"
  spec.license       = "MIT"

  spec.files         = `git ls-files -z`.split("\x0")
  spec.executables   = spec.files.grep(%r{^bin/}) { |f| File.basename(f) }
  spec.test_files    = spec.files.grep(%r{^(test|spec|features)/})
  spec.require_paths = ["lib"]

  spec.add_development_dependency "bundler", "~> 1.6"
  spec.add_development_dependency "rake"
end
```


## LICENSE.txt

```
Copyright (c) 2014 Steve Klabnik

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

## Rakefile

``` ruby
require "bundler/gem_tasks"

require "rake/testtask"

Rake::TestTask.new do |t|
  t.test_files = FileList['test/*_test.rb']
end

task default: :test
```

## README.md

```
# HowIStart

HowIStart is a very simple example gem to show you how I begin a Ruby project.

## Installation

Install it yourself as:

    $ gem install how_i_start

## Usage

Just run the executable:

```
$ how_i_start
```

And it will point you at the article.

## Contributing

1. Fork it ( https://github.com/[my-github-username]/how_i_start/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
```

## bin/how_i_start

``` ruby
#!/usr/bin/env ruby

require 'how_i_start'

puts HowIStart::Url
```

## lib/how_i_start.rb

``` ruby
require "how_i_start/version"

# All code in the gem is namespaced under this module.
module HowIStart

  # The URL of the article about how I start.
  Url = "http://howistart.org/posts/ruby/1"
end
```

## lib/how_i_start/version.rb

``` ruby
module HowIStart

  # The current version of HowIStart.
  VERSION = "1.0.0"
end
```

## test/url_test.rb

``` ruby
require "minitest/autorun"

require "how_i_start"

class UrlTest < Minitest::Test
  def test_url
    assert_equal "http://howistart.org/posts/ruby/1", HowIStart::Url
  end
end
```
