---
title: "Installing RubyOnRails error"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-03-06
This is the second time that I have got the following error when
running gem install rails --include-dependencies

+++++
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
Successfully installed rails-1.2.2
Successfully installed rake-0.7.2
Successfully installed activesupport-1.4.1
Successfully installed activerecord-1.15.2
Successfully installed actionpack-1.13.2
Successfully installed actionmailer-1.3.2
Successfully installed actionwebservice-1.2.2
Installing ri documentation for rake-0.7.2...
Installing ri documentation for activesupport-1.4.1...
Installing ri documentation for activerecord-1.15.2...
Installing ri documentation for actionpack-1.13.2...

lib/action_controller/routing.rb:1061:30: ':' not followed by
identified or operator
+++++

When I run it again hoping that it will fix itself all I get is this
+++++
chris@chris-laptop:~$ sudo gem install rails --include-dependencies
Successfully installed rails-1.2.2
+++++

but of course it doesn't work, but doesn't seem to recognize that the
install was unsuccessful.

And what is the best way to remove all the installed files to do it
again.  I did mention this is the second time, and the first time is
kinda fuzzy since I did so many things that somehow in the end worked
out. 

The bad thing is that I was trying to copy the error from the terminal window with ctrl-shift-c, but accidantally hit ctrl-c, which then ended the install.  I am able to start the server and open the base localhost:3000 page, I am just a little wary to think that all will still work fine.

Thanks for the help

---

