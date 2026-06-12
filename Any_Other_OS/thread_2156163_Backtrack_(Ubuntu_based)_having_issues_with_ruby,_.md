---
title: "Backtrack (Ubuntu based) having issues with ruby, gem etc for Metasploit"
date: 2013-06-20
forum: Any Other OS
---

### Post by lewandowskid on 2013-06-20
Backtrack 5r3 (Ubuntu based linux) running Metasploit framework.  
Did a "msfupdate" command and msfconsole stopped working.  
I read some things online, tried to fix it and only ended up making things much worse.  
I am now having issues with Ruby, gem etc.    
I will post a bunch of info and hopefully someone can help me as a linux noob to fix things and get my machine back to working order.  

I followed the instructions here:  
[https://community.rapid7.com/thread/3289](https://community.rapid7.com/thread/3289)[1]  

I also tried to install gem manually.  
and got the following results.  

-#msfconsole  
Metasploit requires the Bundler gem to be installed  
$gem install bundler  

-#gem install bundler  
Successfully installed bundler-1.3.5 /usr/lib/ruby/1.8/rdoc/rdc.rb:280: warning: conflicting chdir during another chdir block  
/usr/lib/ruby/1.8/rdoc/rdc.rb:287: warning: conflicting chdir during another chdir block  
Done installing documentation for bundler after 13 seconds  
1 gem installed  

-#msfconsole 

still gets the Metasploit requires bundler installed message  

-#ruby -v  
ruby 1.9.2dev (2010-07-02) [i486-linux]  

-#gem -v  
2.0.3  

-#gem list   
LOCAL GEMS  
bundler (1.3.5)
  
dpkg WAS showing  


dpkg -l | grep ruby    
ii libopenssl-ruby 4.2-2~uorppa0 OpenSSL interface for Ruby    
ii libopenssl-ruby1.8 1.8.7.249-2ubuntu0.2 OpenSSL interface for Ruby 1.8  
ii libreadline-ruby1.8 1.8.7.249-2ubuntu0.2 Readline interface for Ruby 1.8  
ii libreadline-ruby1.9.2 1.9.2.z1-1ppa1~lucid Readline interface for Ruby 1.9.2  
ii libruby1.8 1.8.7.249-2ubuntu0.2 Libraries necessary to run Ruby 1.8  
ii libruby1.9.2 1.9.2.z1-1ppa1~lucid Libraries necessary to run Ruby 1.9.2  
ii rdoc 4.2-2~uorppa0 Generate documentation from ruby source files  
ii ruby 4.2-2~uorppa0 An interpreter of object-oriented scripting language Ruby  
ii ruby1.8 1.8.7.249-2ubuntu0.2 Interpreter of object-oriented scripting language Ruby 1.8  
ii ruby1.9.2 1.9.2.z1-1ppa1~lucid Interpreter of object-oriented scripting language Ruby 1.9.2  
ii rubygems 1.3.7-1~uorppa0 package management framework for Ruby libraries/applications  
ii rubygems1.8 1.3.7-1~uorppa0 package management framework for Ruby libraries/applications  
ii rubygems1.9.2 1.3.7-1~uorppa0 package management framework for Ruby libraries/applications  

someone told me to do the following-


-# update-alternatives --query ruby  
-# update-alternatives --config ruby  
-# apt-get --purge remove libruby1.8 ruby1.8 ruby1.8-dev rubygems1.8  
-# msfupdate  


which led to:


-#msfupdate  
updating gems...  
/opt/metasploit/msf3/msfupdate:198:in 'require' no such file to load --buffer (LoadError)  
from /opt/metaspoit/msf3/msfupdate:198:in '<main>'


[COLOR=#000000][FONT=verdana]now gem -v error  [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]gem -v /usr/local/lib/site_ruby/1.9.2/rubygems/gem_runner.rb:73:in <top (required)>': undefined methodload_plugins' for Gem:Module (NoMethodError) from /usr/bin/gem:9:in require' from /usr/bin/gem:9:in<main>'  

dpkg is now showing for ruby-

-#dpkg -l | grep ruby  
ii libreadline-ruby1.9.2 1.9.2.z1-1ppa1~lucid Readline interface for Ruby 1.9.2  
ii libruby1.9.2 1.9.2.z1-1ppa1~lucid Libraries necessary to run Ruby 1.9.2  
ii ruby1.9.2 1.9.2.z1-1ppa1~lucid Interpreter of object-oriented scripting language Ruby 1.9.2  
ii rubygems1.9.2 1.3.7-1~uorppa0 package management framework for Ruby libraries/applications  

[/FONT][/COLOR]

---

### Post by QIII on 2013-06-20
*Moved to **Other OS/Distro Support.***

Although based on Ubuntu, Backtrack is a distro in its own right.

This forum may get you some answers, but the best place to get help might be a dedicated Backtrack Forum.

Best wishes.

---

### Post by CharlesA on 2013-06-20
We don't support metasploit here, in any case/

Check the backtrack forums.

---

