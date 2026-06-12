---
title: "grub versus bios?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-08-08
could someone please explain to me the difference between bios and grub? Wikipedia didn't help me.

thanks

---

### Post by Depressed Man on 2007-08-08
Grub is the bootloader for Linux. Though it can also handle Windows too. 

BIOS is what the computer goes to read its startup information (such as what HDD to check first, or what disc drive to check for an OS installation disc). 

So an example would be.

You turn on the computer, the computer reads the BIOS to see "ok I want to check the disc drive to see if there's a disc first then I want to check HDD1 for any directions, if not go to HDD2".

So it checks disc drive. Well is there a bootable disc in there (Windows install disc, Linux install disc, Linux Live CD?). Nope? Ok onto HDD1

HDD1. Oh look it contains the bootloader (say Grub). We'll load that up.

GRUB takes over now:

What do you want to load? 

Linux kernel whatever
Linux kernel whatever recovery
Windows whatever

etc..

Edit: BIOS also stores other important settings like your clockspeed (you can overclock from there if you know how) and other things such as what speeds the buses on your motherboard should use.

---

### Post by kozy6871 on 2007-08-08
I just had an experience with this.  I just turned my desktop into a dual boot machine - sort of.  I kind of botched the whole thing and created a mess to try and fix.  Right now I have to use the BIOS (by changing the boot drive; IDE0 for windows, and IDE1 for Ubuntu) in order to switch.

Once I get things straightened out, I hope to be able to dual boot the right way.

---

### Post by scholzilla on 2007-08-08
thanks for that info. :)

---

