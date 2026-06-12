---
title: "NDISwrapper, network-manager-gnome problems"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Chris Kupka on 2008-01-23
Hello all:

I'm extremely new to Ubuntu (first time using the CLI), so please bear with me.

I am trying to get my Atheros wireless to work on my acer 3680. After dicking around with ndiswrapper for a while, I found a post which suggested deleting the packages for network-manager-gnome through synaptic, and reinstalling.

When I try reinstalling, however, I encounter the following problem when I attempt
$ ./configure

chris@chris-laptop:~/Desktop/nm-applet-0.6.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Now I don't even have network-manager-gnome on my computer.

My previous problem with ndiswrapper (1.51) was that I couldn't detect wlan0.  I got to the iwconfig step, but it just wouldn't locate wlan0.

Help with either problem would be appreciated.  I'm currently plugged into my desktop's LAN connection, otherwise I have to access the internet through winblows vista.

Thanks,
Chris

---

### Post by ctswhole on 2008-01-23
Do you have "build-essential" installed?  Try installing that and see if it corrects your problem.

---

### Post by Chris Kupka on 2008-02-03
After reinstalling ubuntu I installed build-essential, which got NDISwrapper working.  Still didn't get my wireless up and running, until I followed a post explaining how to get it working through Mad Wifi.  Wireless is now up and running - on to creating a fat32 partition, then installing beryl and automatix2.

Thanks!

---

