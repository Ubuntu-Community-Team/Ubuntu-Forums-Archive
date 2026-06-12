---
title: "How to Install X11 and DDD?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Tekmoto on 2006-09-21
Hello everyone,

This is my first time using UBuntu. I don't have too much experience with Linux in general. 

I have already installed GCC and G++ from the build-essential package, which wasn't too hard to find.

Next, I would like to install DDD (data display debugger, the GUI front end for GDB). to debug my school assignments. However, I don't know how to do this in Ubuntu. 

I cannot locate the package needed for X11, which I hear is needed and includes DDD.

Can someone help?

---

### Post by andypaxo on 2006-09-21
Installing the package 'ddd' in the same manner as any other package works just fine for me. (ie. Using apt, synaptic or aptitude).
X11 is the basis for every Linux graphical environment - belive me, you already have it!

A couple of things to bear in mind:
- The package name is lowercase
- You may need to enable extra repositories, check the [Ubuntu guide]("http://ubuntuguide.org/")

---

### Post by Tekmoto on 2006-09-23
I downloaded the DDD package (ddd_3.3.9.orig.tar.gz), now what? I don't know what synaptic or aptitude is. Can someone tell me exactly what to do (ie, where do I put this file, do I uncompress it, etc.)?

---

### Post by andypaxo on 2006-09-25
Okay, sorry in being slow to come back to you...
You don't need to download the .tar.gz package, there is an easier way to install.
Either:
 Click System->Administration->Synaptic then search for and install ddd
Or:
 Type ```
sudo apt-get install ddd
``` at the command line (You will be asked for you password - just use the same one you use to log in.

Hope this helps

---

### Post by rob_x on 2006-12-10
Hi andypaxo,
  I tried the steps you mentioned above but I got an error msg:

 "E: Couldn't find package ddd"
 
how can I solve this problem ? 
thanks

---

### Post by steve.horsley on 2006-12-10
Start System->Administration->Synaptic Package Manager, pull down Settings->Preferences, make sure the Multiverse and Universe repos are enabled. Then use reload to make it read the extra repo info, then search for ddd again.

---

### Post by mcduck on 2006-12-10
This link might be helpful:
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by rob_x on 2006-12-18
thx alot guys !! xD

---

