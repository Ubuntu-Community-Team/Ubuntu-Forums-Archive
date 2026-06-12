---
title: "new to ubuntu, just have a quick question regarding live cd installer"
date: 2008-08-18
forum: Apple Hardware Users
---

### Post by joshh1 on 2008-08-18
Hello.

I'm trying to install Ubuntu (the newest version) on my Powermac G4 (533mhz, 512 ram)
I get to step 5 and the installation has been sitting here for probably 20-30 minutes doing nothing. The cursor is spinning like it's loading but thats it?

Is this normal? This is the 2nd time it's done it, first time I restarted..

Thanks for any help!

---

### Post by stream303 on 2008-08-18
Normally I recommend the use of the "alternate" installer, but you may have issues beyond just being patient.

How many hard drives do you have, and are any of them larger than 128gB?  That machine has a 128gB partitioning limitation, which can be worked around, HOWEVER, you may also run into the dual-hd-controller issue with that model that might force one to use an openfirmware alias instead of a pathname in the yaboot.conf bootloader config file.

If you can get to any sort of commandline or terminal at all, you might be able to work out some of these issues.

Also, what are the monitor's specs, and also what video card are you using?

You may be fighting an uphill battle temporarily.

---

### Post by joshh1 on 2008-08-18
I'm actually having problems with OS X, and just planning to use Ubuntu as my main OS and not use OS X at all ( I have 2 macs)

Using 1 30 GB hdd and 1 40 GB hdd, 30 is my master and what I'm using for ubuntu 40 is just media and etc.

Monitor: 17'' CRT (just using until I get this installed )Resolution I believe is 1600x1200 

Graphics: I believe it's some sort of Nvidia with 32 mb vram. (I have a flashed for mac ATI radeon 9800 I can use as well, just wasn't sure if that work for ubuntu.)

I'm a total noob when it comes to the command line. haha.

---

### Post by stream303 on 2008-08-18
Great - I'd definitely try the "alternate" intaller, but hope you have some sort of osx install disk to fall back on in case this gets a bit too cumbersome.

I'd stick with the Nvidia graphics card for now just to make life a little bit easier.

You will want to gather up the horizontal and vertical frequencies of that monitor.

It isn't that Ubuntu isn't ppc friendly, it is actually more like the PPC hardware wasn't really designed for Linux in mind.  :)  It can be done, but you may have to do a bit of searching in the threads.

---

### Post by arranmc182 on 2008-08-18
also just remember adobe is a bitch and dont make Flash for PPC i had the same problem with any live CD i tryed on my Power Mac G3 Blue & White 450Mhz with a ATI Radeon 32MB try the non live CD seem to work a lot better just i was to lazy to configer every thing so i just reinstalled mac OS 9 (i know your all thinking :lolflag: OS 9 that sucked but i found OS 9.2 works just fine befor OS 9.2 yeah it did suck)

---

