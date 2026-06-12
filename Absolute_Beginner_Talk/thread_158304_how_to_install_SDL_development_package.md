---
title: "how to install SDL development package??"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-10
I am trying to get an ipod situation set up, I am following this how to: 
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)
I am at this part:

Next, unpack it and configure it:

Code:

tar xzf mpeg4ip-1.4.1.tar.gz 
cd mpeg4ip-1.4.1 
./bootstrap --disable-server 
sudo mkdir /usr/local/include sudo cp mpeg4ip_config.h /usr/local/include 
sudo cp include/mpeg4ip.h include/mpeg4ip_version.h /usr/local/include ./configure cd lib/mp4v2 sudo gedit Makefile

when i type the ./bootstrap --disable-server  it says SDL does not appear tobe installed - install the SDL development package
You must have sdl-config in your path to continue.

i go to synaptic and search for libsdl, what one gets installed?  I tried libsdl1.2-dev but it says it depends on libartsc0-dev but it wont be installed, i looked at that one and it wont let me mar it for installation.  plus it looks like an older version of what is installed??  any help please?

---

### Post by Sef on 2006-04-21
> i go to synaptic and search for libsdl, what one gets installed? I tried libsdl1.2-dev but it says it depends on libartsc0-dev but it wont be installed, i looked at that one and it wont let me mar it for installation. plus it looks like an older version of what is installed?? any help please?

Check here to download it.

[http://packages.ubuntulinux.org/breezy/libdevel/libartsc0-dev]("http://packages.ubuntulinux.org/breezy/libdevel/libartsc0-dev")

---

