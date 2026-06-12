---
title: "Kernel Panic! on iMac G3 install"
date: 2007-07-14
forum: Apple PPC Users
---

### Post by Conspyre on 2007-07-14
I'm trying to install Ubuntu on a venerable trayloading iMac.  It's specs are:
PPC G3 333mhz
32 megs RAM, 64 megs virtual
6 gig HDD

I initialized the disk with a minimum size MacOS partition for OS9, and the rest as what the system called a Linux Home Partition.  Then I booted off of the Ubuntu 6.06.1 alternate PPC install, since I'd read somewhere that the full installation doesn't work right with a machine this wimpy.  With both the default installation option and "install /ofonly", I get this:

[  53.182047]  RAMDISK:  incomplete write (-28 != 32768) 8388608
[  53.356164] RAMDISK: ran out of compressed data
[  53.356384] invalid compressed format (err=1)
[  53.360762] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[  53.361095]

After the last number, the cursor just sits there, not blinking.  I can't type anything, and after a couple of minutes (About just as long as it took me to copy the screen text), the machine reboots.  Do I have the disk formatted wrong or something?  This is my first time trying to install Linux, and after already spending a couple hours failing to install Gentoo on the same machine, I'm about ready to chuck it out the window.

---

### Post by Conspyre on 2007-07-14
Update: I tried with the minimal installer for 7.04 and got the same error messages, just different numbers on the left.

---

### Post by bodycoach2 on 2007-07-14
I've installed Xubuntu on two iMac 333 MHz machines. Same configurations, except I got more memory for them. One has 190 meg Ram, the other 128 - or somewhere in that range. I think the problem is the RAM. I've tried loading Xubuntu on a Pentium II with only 64 meg ram, and it's just not worth it. I'm not sure even DSL (Damn Small Linux) will work with 32meg. 

Checkout [LowEndMac]("http://lowendmac.com") for info on getting memory for that computer.
[ http://lowendmac.com]("http://lowendmac.com")
Also, I'd recommend trashing Mac OS9. If you can get that iMac's RAM up to about 256, Xubuntu will run fine on it.

---

