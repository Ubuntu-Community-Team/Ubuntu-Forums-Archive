---
title: "Ultra Mac Beginner-General Help"
date: 2005-09-27
forum: Apple PPC Users
---

### Post by walkingbeard on 2005-09-27
Hi!

The social centre I do work for has just acquired a Mac.  On the front it reads PowerPC Performa 6400/200.  It's currently running Mac OS 7.5, and has a whole load of stuff installed from when it was a university computer.

There is a USB keyboard, with a one button mouse attached.  There is also a floppy drive and CD drive.

Because of the kind of group it is that runs the centre, we would prefer to install Linux on this system.  I use Ubuntu on my PC, but I have no idea about how it would work on a Mac, especially one as ancient as this one.

Given that we have not much money to spend, what do you guys recommend? Can anybody with experience of Mac OS 7 tell me how to find out the details of the system's hardware?

Basically, is Ubuntu going to work as well on this as it does on my PC, if at all?

---

### Post by zxee on 2005-09-27
From the apple menu icon (upper left corner) choose "about this mac" That should give you the amount of ram, hard drive size, ect. The 6400 series had a 603e CPU-which is an old world mac. Installing ubuntu-while possible won't be easy. 
IMO linuxppc a discontinued linux distro, which I have installed on older macs similar to the 6400, might be your best bet. Although linuxppc is discontinued there are still links and cd's available [http://lowendmac.com/meta/2k1214.html](http://lowendmac.com/meta/2k1214.html)  Good luck.

---

### Post by walkingbeard on 2005-09-28
Thanks a lot!

---

### Post by stuporglue on 2005-09-29
The words you'll want to search for are "Old-world mac", and "bootx". Bootx is the bootloader you'll have to use as yaboot is new world only. You'll need to keep a Mac partition to load the bootloader from, but you can make it pretty small. 

Your best bets are probably going to Debian, Yellow Dog, Gentoo, or something that's been discontinued already.

---

