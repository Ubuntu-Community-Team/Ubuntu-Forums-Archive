---
title: "install gcc in hoary"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by aberriz on 2007-10-27
Hello, I´m new to the forum, and to linux still, hence I decided to post in this section. 

   I have a relatively old pentiumIII@1.10GHz-240MB laptop (cybercom is the brand, never heard of it until now) that a friend lend me. I run in it the "live-cd" for Ubuntu 5.04 (hoary hedgehog). I need it to do some basic C programming for my operative systems course, but I don't want to touch my friend's hard drive (that's why I rather use a live-cd).

   (I didn't use the latest 7.10 version because it said that I need a minimum of 256MB of ram, and I had this live-cd from a previous course some time ago, it seemed like a better idea)

   The live-cd works fine, and if I connect the Ethernet cable before loading the OS, I can surf the web without problems (otherwise, I couldn't manage to configure the eth0 interface myself, although I'm sure there's a proper way).

   The problem is that when I try to do **"sudo apt-get install build-essential"** so I can compile ".c" files doing "gcc -o xx.c xx" I get a series of "**Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/... 404 Not Found [IP: 91.189.88.46 80]**"s and "**Failed to fetch http..**."s. Then, as recommended by the application, I tried "apt-get update" and appending "--fix-missing", but it didn't work.

   Is this because hoary hedgehog is unsupported nowadays? With this in mind, I downloaded from this site: [https://launchpad.net/ubuntu/hoary/+source/gcc-3.4]("https://launchpad.net/ubuntu/hoary/+source/gcc-3.4")  the file "gcc-3.4_3.4.3.orig.tar.gz" and then tried to install it by my own means from a usb flash drive (which was in the directory under "/media/KINGSTON/gcc-3.4_3.4.3.orig.tar.gz") and tried dpkg -i, apt-get install, gunzip and other stuff that I found browsing forums on the web, but none of them ever worked.

   I can actually connect to the internet all right. I open firefox and surf around and is all cool. It's when I do the "sudo apt-get install" that I get those "404 Not Found [IP: 91.189.88.46 80]"

   Does anyboy know why I can't install the "build-essential" packet, and more important yet, how can I do to compile C programs in this machine using a live-cd?

   thanks for considering this post ;)

Greetings to all,

I have a relatively old pentiumIII@1.10GHz-240MB laptop (Cybercom is the brand, never heard of it until now) that a friend lend me. I run in it the "live-cd" for Ubuntu 5.04 (hoary hedgehog). I need it to do some basic C programming for my operative systems course, but I don't want to touch my friend's hard drive (that's why I rather use a live-cd).

(I didn't use the latest 7.10 version because it said that I need a minimum of 256MB of ram, and I had this live-cd from a previous course some time ago, it seemed like a better idea)

The live-cd works fine, and if I connect the Ethernet cable before loading the OS, I can surf the web without problems (otherwise, I couldn't manage to configure the eth0 interface myself, although I'm sure there's a more proper way).

**The problem is** that when I do "**# sudo apt-get install build-essential**" so I can compile ".c" files doing "# gcc filename.c -o execfile" I get a series of "**Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/... 404 Not Found [IP: 91.189.88.46 80]**" and "**Failed to fetch [http://archive.ubu](http://archive.ubu)...**" messages. Then, as recommended by the application, I tried "# apt-get update" and appending "--fix-missing", but it didn't do any good.

Is this because hoary hedgehog is unsupported nowadays? With this in mind, I downloaded from [this site]("https://launchpad.net/ubuntu/hoary/+source/gcc-3.4") the file "gcc-3.4_3.4.3.orig.tar.gz" and then tried to install it by my own means from a usb pen drive (which was in the directory under "/media/KINGSTON/gcc-3.4_3.4.3.orig.tar.gz") and tried several commands like dpkg -i, apt-get install, gunzip and other stuff that I found browsing forums on the web, but I did't manage to install the GCC compiler.

I can actually connect to the internet all right. E.g. I open firefox and surf around and is all cool. It's when I do the "sudo apt-get install" that I get those "404 Not Found [IP: 91.189.88.46 80]" messages.

when running 7.10 live in another friend's machine I saw it's perfectly possible to install the build-essential packet.

Does anyboy know why I can't install the "build-essential" packet on ubuntu 5.04? And even more important yet, **what can I do to be able to compile C programs in this machine (pentimIII@1.10GHz, 240MB of RAM) using a live-cd ?** (I have Ubuntu 5.04, but would get any other if it enables me to do this)

thanks in advance.

If you're running from the live cd, and don't want to touch your friend's hard disk, I don't see you you can install new packages.

The repositories for Hoary don't exist at that address anymore.  I don't remember what it is off the top of my head, but they've been archived because Hoary isn't supported anymore.

Any LiveCD requires at least 256MB of RAM to run, so it shouldn't matter what version of Ubuntu you use.

Your best option may be to run Ubuntu in Windows through a virtual machine.  It'll be a lot faster than a LiveCD at the very least.

> **aberriz said:**
> 
   Does anyboy know why I can't install the "build-essential" packet, and more important yet, how can I do to compile C programs in this machine using a live-cd?

   thanks for considering this post ;)

You can install on the live cd if, but it will be stored in RAM.

I don't think such a package existed for hoary, I'll look into it.

I can't find it on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), sorry.

The repositories for *Hoary* are down forever, because *Hoary* is not supported any more. You should try the *Gutsy (7.10)* Live CD. Your amount of RAM is very close to the required one so give it a try.

---

### Post by caffienefree on 2007-10-28
I'd say you might be better off with the Xubuntu 7.10 or 7.04 distribution with your memory requirement...

---

### Post by Incense on 2007-10-28
Hoary is not really supported anymore. You may want to consider running dapper. Yeah it has the 256 min as well, but it runs very well on 256 machines even in live mode, and the repos are still active. Any build of xubuntu live would do what you need as well. Hoary just does not get securty updates anymore, so you're running a risk just using it, and Dapper has a couple years of support left on it still. Not sure what to do about GCC in hoary though.

---

