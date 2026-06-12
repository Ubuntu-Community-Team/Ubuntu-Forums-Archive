---
title: "Rails script/server error"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by wastedtime on 2007-04-21
I am using feisty and I installed ruby and rails using this tutorial here 
[http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/](http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/)

Whenever is try and start my application this is the error i get.
The application used to work just fine in edgy. :(

=> Booting Mongrel (use 'script/server webrick' to force WEBrick)
=> Rails application starting on [http://0.0.0.0:3000](http://0.0.0.0:3000)
=> Call with -d to detach
=> Ctrl-C to shutdown server
** Starting Mongrel listening at 0.0.0.0:3000
** Starting Rails with development environment...
Exiting
/usr/local/lib/ruby/gems/1.8/gems/rails-1.2.3/lib/commands/servers/mongrel.rb:15: warning: already initialized constant OPTIONS
/usr/local/lib/ruby/gems/1.8/gems/rails-1.2.3/lib/commands/servers/mongrel.rb:18: undefined method `options' for []:Array (NoMethodError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:32:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:495:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
        from /usr/local/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:495:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/rails-1.2.3/lib/commands/server.rb:39
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb

Is there something wrong I am doing ??

---

### Post by wastedtime on 2007-04-22
I completely uninstalled ruby / and gems and tried again. The same result again.  :(

---

### Post by jiminycricket on 2007-04-22
Have you tried installing from feisty's repositories instead?

sudo aptitude install rails rubygems

---

### Post by wastedtime on 2007-04-22
> **jiminycricket said:**
> Have you tried installing from feisty's repositories instead?

sudo aptitude install rails rubygems

It seems to install fine but when i type gem list to list all the gems installed . It gives me this error

/usr/lib/ruby/1.8/rubygems.rb:9:in `require': no such file to load -- rbconfig (LoadError)
        from /usr/lib/ruby/1.8/rubygems.rb:9
        from /usr/bin/gem:9:in `require'
        from /usr/bin/gem:9

---

### Post by hasimir44 on 2007-06-21
did you install the ruby dev package? (it's hard to see in that tutorial due to bad css)

```
sudo apt-get install ruby1.8-dev
```

are you able to install anything with gem?  try an update:

```
sudo gem update
```

I had some problems with gem and periodically have to delete the source cache file before installs:

```
sudo rm /usr/lib/ruby/gems/1.8/source_cache
```

also, that tutorial doesn't cover the mongrel installation.. did you install with gem? 

```
sudo gem install mongrel
```

---

### Post by qiepenguin on 2008-03-07
> **wastedtime said:**
> 
** Starting Rails with development environment...
Exiting
/usr/local/lib/ruby/gems/1.8/gems/rails-1.2.3/lib/commands/servers/mongrel.rb:15: warning: already initialized constant OPTIONS
/usr/local/lib/ruby/gems/1.8/gems/rails-1.2.3/lib/commands/servers/mongrel.rb:18: undefined method `options' for []:Array (NoMethodError)

This error happens when the application requires a gem that is not installed.  Check config/environment.rb and make sure you have all the gems that are required there.

---

