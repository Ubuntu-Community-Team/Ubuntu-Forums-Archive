---
title: "re-format drive to OS X?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by mph66 on 2006-10-11
No, this is NOT an Ubuntu flame.

I back up my data.  Wiped my PPC's HD and then installed Ubuntu.  I love it.  But I forgot that I still need to run one proprietary piece of Mac ware and so now I need away to bulldoze the drive to get Mac OS X back on there, and another partition for Ubuntu (which I'll use most of the time, I think).

Any help for this noob?

Thanks,

Marc

---

### Post by jordanmthomas on 2006-10-11
You can use the LiveCD and Gnome Partition Editor to create hfs+ partitions

At the very least, you can make some room for it and let OSX create the partition.

---

### Post by mph66 on 2006-10-11
OK...that's the part I'm not getting...

When I put in the Live CD and get booted in and ready to go, I run the partitioner and it won't let me create HFS+ partitions- only HFS.  Can't boot an OS X cd from that.  Then, how do I get the comp. to recognize the Mac OS X cd?  Is there something in the boot I have to reconfig?  I'm really lost on this.  Do I make the Mac partition extended?

-Marc

---

### Post by jordanmthomas on 2006-10-11
Are you saying you can't boot off your OSX CD?  
If you just make a blank partition, the OSX CD should be able to create a partition in it.

...Are you trying to install OSX on a non-Mac?

---

### Post by mph66 on 2006-10-12
Thanks for your reply.  I'll try to be clearer.  Sorry 'bout that.

I'm trying to install OS X on an eMac (G4, 1GHz, 512 RAM) that I wiped completely.  There is no HFS+ partition.  I'd like to make one.  When I pop in (and boot from) the PPC Live CD (the one I used to make this install) and open partition manager, I get the option to create an HFS partition, but not HFS+ (that's grayed-out).  I've tried the HFS partition, and no luck.  When I put the OS X cd in the tray and attempt to boot from that (holding down the "C" key) the machine gives me a text menu: 

press l to boot Linux
press c to boot from CD

When I press "C" with the OS X cd in the tray, the machine waits ("...") and then goes back to the above menu.  No boot.  I have to either boot into Ubuntu, or insert the Live CD and go through configuring the xorg.conf file for screen refresh rate before I can get it to boot.  But still, I can't get this machine to boot from the OS X cd.

Help?

-Marc

---

### Post by jordanmthomas on 2006-10-12
OK, I understand what's going on now...unfortunately I don't know anything about Macs.  
It seems like the lack of a partition to work with shouldn't cause a *PC* to not boot is what's messing with your Mac.

You'll either have to wait around for an answer here or take it over to the PPC forums.  :(

---

### Post by linear on 2006-10-12
> **mph66 said:**
> When I put the OS X cd in the tray and attempt to boot from that (holding down the "C" key) the machine gives me a text menu

Either something is wrong with your OS X CD (it's damaged and no longer readable) or your CD drive has gotten finicky.

With the CD in, try booting with the option key held down and see if the CD shows up as a bootable volume.

(This has nothing to do with what's currently on your hard disk.)

You can also try this ritual, from an Apple support article:

>                               Restart the computer and hold these keys: Command-Option-O-F . This asks the computer to start in Open Firmware.
Tip: If you don't start in Open Firmware, try again. Make sure you're using a USB keyboard, and that the keyboard is connected directly to one of the computer's USB ports.
type: boot cd:,\\:tbxi
Press Return.

---

