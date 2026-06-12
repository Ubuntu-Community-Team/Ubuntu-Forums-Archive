---
title: "Mongrel + Apache2 + SSL"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by nagileon on 2007-07-30
Jul 30, 2007 07:55:46 GMT   

--------------------------------------------------------------------------------
Hi there!
I have to install Mongrel + Apche2 + SSL the system is Ubuntu 6.10 
I did:

vim /etc/apt/sources.list 
apt-get update
apt-get dist-upgrade
apt-get install build-essential
apt-get install ruby1.8-dev 
apt-get install ruby 
wget [http://rubyforge.iasi.roedu.net/files/rubygems/rubygems-0.9.0.tgz](http://rubyforge.iasi.roedu.net/files/rubygems/rubygems-0.9.0.tgz)
tar xvzf rubygems*
cd rubygems*
ruby setup.rb

The next step is :

gem install deprec –include-dependencies

And then I get errors:


root@rails:~/rubygems-0.9.0# gem install deprec --include-dependencies
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
Need to update 1 gems from [http://gems.rubyforge.org](http://gems.rubyforge.org)
.
complete
Successfully installed deprec-1.9.0
Successfully installed capistrano-1.4.1
Successfully installed rake-0.7.3
Successfully installed net-ssh-1.1.2
Successfully installed needle-1.3.0
Successfully installed net-sftp-1.1.0
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- rdoc/rdoc (LoadError)
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
from /usr/local/lib/site_ruby/1.8/rubygems/doc_manager.rb:71:in `load_rdoc'
from /usr/local/lib/site_ruby/1.8/rubygems/doc_manager.rb:41:in `generate_ri'
from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:283:in `execute'
from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:282:in `execute'
from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:220:in `execute'
from /usr/local/lib/site_ruby/1.8/rubygems/command.rb:69:in `invoke'
from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:117:in `process_args'
from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:88:in `run'
from /usr/local/lib/site_ruby/1.8/rubygems/gem_runner.rb:29:in `run'

The next step should be:

gem install mongrel --include-dependencies

But I'm getting similar errors and mongrel is not being installed.

Does anybody know why ?

Cheers

---

### Post by DBStevens on 2007-07-30
I'm getting the same baloney when I try it with 7.04, and the 0.9.4 version of things however even after the messages here is what I have:

:~/rubygems-0.9.4$ gem list

*** LOCAL GEMS ***

capistrano (1.4.1)
    Capistrano is a framework and utility for executing commands in
    parallel on multiple remote machines, via SSH. The primary goal is
    to simplify and automate the deployment of web applications.

cgi_multipart_eof_fix (2.2)
    Fix an exploitable bug in CGI multipart parsing which affects Ruby
    <= 1.8.5 when multipart boundary attribute contains a non-halting
    regular expression string.

daemons (1.0.7)
    A toolkit to create and control daemons in different ways

deprec (1.9.0)
    deployment recipes for capistrano

fastthread (1.0)
    Optimized replacement for thread.rb primitives

gem_plugin (0.2.2)
    A plugin system based only on rubygems that uses dependencies only

mongrel (1.0.1)
    A small fast HTTP library and server that runs Rails, Camping, Nitro
    and Iowa apps.

needle (1.3.0)
    Needle is a Dependency Injection/Inversion of Control container for
    Ruby. It supports both type-2 (setter) and type-3 (constructor)
    injection. It takes advantage of the dynamic nature of Ruby to
    provide a rich and flexible approach to injecting dependencies.

net-sftp (1.1.0)
    Net::SFTP is a pure-Ruby implementation of the SFTP client protocol.

net-ssh (1.1.2)
    Net::SSH is a pure-Ruby implementation of the SSH2 client protocol.

rake (0.7.3)
    Ruby based make-like utility.

sources (0.0.1)
    This package provides download sources for remote gem installation

Looks like it complained but did the install ....

---

### Post by MatthewMetzger on 2007-11-14
I had similar problems when trying to get the dependencies for camping to work last night. I finally figured out the rdoc was not installed.

Try: apt-get install rdoc rdoc1.8 (I can't remember if rdoc1.8 is the exact package name).

-Matthew

---

