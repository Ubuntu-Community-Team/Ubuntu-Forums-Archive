---
title: "ruby on rails install issue"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by butthash on 2008-03-20
I'm trying to get a ruby on rails install going. 

I followed the instructions on this page
[https://help.ubuntu.com/community/RubyOnRails#head-f0e27fe7ff8b6ff099541a7b80d8dee9c8f6880b](https://help.ubuntu.com/community/RubyOnRails#head-f0e27fe7ff8b6ff099541a7b80d8dee9c8f6880b)

but ran into a problem with gems not installing properly.  That problem and the solution I used can be found here. 
[http://ubuntuforums.org/showthread.php?t=649881](http://ubuntuforums.org/showthread.php?t=649881)

I was able to get everything install properly, but now I have a different problem. When I go to start webrick I get the following error.

```
Missing the Rails 2.0.2 gem. Please `gem install -v=2.0.2 rails`, update your RAILS_GEM_VERSION setting in config/environment.rb for the Rails version you do have installed, or comment out RAILS_GEM_VERSION to use the latest version installed.
```

2.02 is the only version of rails installed. I tried doing
```
gem install -v=2.0.2 rails
```
but that didn't help.

I tried commenting out the line in config/environment.rb, that just changes the error to this
```
Missing the Rails  gem. Please `gem install -v= rails`, update your RAILS_GEM_VERSION setting in config/environment.rb for the Rails version you do have installed, or comment out RAILS_GEM_VERSION to use the latest version installed.
```

I know I have that version of rails installed but for some reason webrick can't see it.

```
# gem query

*** LOCAL GEMS ***

actionmailer (2.0.2)
actionpack (2.0.2)
activerecord (2.0.2)
activeresource (2.0.2)
activesupport (2.0.2)
rails (2.0.2)
rake (0.8.1)
rubygems-update (1.0.1)

```


The first time I installed everything webrick would start but I would get errors because everything didn't install properly.

any ideas?

---

