---
title: "Problems installing rubygems"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by JukeJoke on 2007-12-25
Hi!

First of all: I'm new to the whole linux thing, so please be patient with me ;-)


I installed all the packages needed for rubygems through apt-get (followed some tutorial), but when it comes to the prompt "ruby setup.rb" the problems start. This is what i get:


```


[...]

Removing old RubyGems RDoc and ri...
rm -rf /usr/lib/ruby/gems/1.8/doc/rubygems-1.0.1
Installing rubygems-0.9.5 ri into /usr/lib/ruby/gems/1.8/doc/rubygems-0.9.5/ri...

lib/rubygems/command_manager.rb:138:61: Skipping require of dynamic string: "rubygems/commands/#{command_name}_command"

lib/rubygems/dependency_installer.rb:37:5: Unrecognized directive 'env_shebang'

lib/rubygems/install_update_options.rb:22:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:28:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:34:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:40:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:46:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:52:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:57:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:63:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:69:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:74:32: ':' not followed by identified or operator

lib/rubygems/installer.rb:42:5: Unrecognized directive 'env_shebang'

lib/rubygems/local_remote_options.rb:29:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:34:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:39:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:52:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:64:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:75:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:89:30: ':' not followed by identified or operator
Installing rubygems-0.9.5 rdoc into /usr/lib/ruby/gems/1.8/doc/rubygems-0.9.5/rdoc...

lib/rubygems/command_manager.rb:138:61: Skipping require of dynamic string: "rubygems/commands/#{command_name}_command"

lib/rubygems/dependency_installer.rb:37:5: Unrecognized directive 'env_shebang'

lib/rubygems/install_update_options.rb:22:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:28:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:34:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:40:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:46:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:52:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:57:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:63:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:69:32: ':' not followed by identified or operator

lib/rubygems/install_update_options.rb:74:32: ':' not followed by identified or operator

lib/rubygems/installer.rb:42:5: Unrecognized directive 'env_shebang'

lib/rubygems/local_remote_options.rb:29:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:34:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:39:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:52:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:64:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:75:30: ':' not followed by identified or operator

lib/rubygems/local_remote_options.rb:89:30: ':' not followed by identified or operator
As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.
```

So, gems is not installed and ist seems that no one has an answer for me (tried google, etc.) ... :(

---

### Post by blueridgedog on 2007-12-27
Trivial reply, but:

Did you run this as a sudo command?

Have you considered posting the problem here:

[www.ruby-forum.com](www.ruby-forum.com)

---

### Post by uptime461 on 2008-01-18
Hi,
I also had the same error and found no helpful clues on google.
However I have fixed the problem, and this may help you.

I am using Ubuntu Dapper Drake 6.06 LTS.
The Ruby version installed through apt-get was 1.8.4.
It didn't recognise that version 1.8.6 was available.
The Gem install failed with the env_shebang message as you described.

I uninstalled Ruby through "apt-get remove ruby".
Then downloaded "ruby-1.8.6-p110.tar.gz" from Rubyforge into my home folder, using Firefox.
Then from terminal as root:
(If you can't log in as root, put "sudo" before each of these commands)
"gzip -d ruby-1.8.6-p110.tar.gz" to unzip it.
"tar xvf ruby-1.8.6-p110.tar" to untar to a folder.

Go into the folder and open the README file e.g. "cat README | pg"
This has instructions for compiling from the source.
You need to run "apt-get install build-essential" first if you don't already have the build stuff.

After the final "make install", Ruby version 1.8.6 was working.
I ran the Gems 1.0.1 install again "ruby setup.rb" in the unpacked Gems folder.
The install was successful.

So I guess there is a bug that affects Ruby 1.8.4 and Gems 1.0.1.
Anyway, it is probably better to have 1.8.6, being the one recommended by the Rails crew.

Good Luck...
Andrew

---

### Post by JukeJoke on 2008-01-19
Thanks! I will try.

---

### Post by Jemima on 2008-02-26
Just some feedback - I had this same problem and Andrew's fix worked for me. Thanks, Andrew!

---

