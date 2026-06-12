---
title: "Refind having trouble &quot;finding&quot; Ubuntu"
date: 2014-11-03
forum: Apple Hardware Users
---

### Post by theodore-r on 2014-11-03
I have a mac mini i5 hd4600. Had 14.04 on an external USB drive. 

Running out of space on internal drive, I cloned to a second USB drive, now the main mac drive. 

Since then, refined doesn't recognize there is a linux install on previous USB drive. The drive is intact, Linux is on separate partition.

Any one else run into this? Any clues how I could resolve this?

---

### Post by d4m1r on 2014-11-04
First off, year and exact model # of that mac mini? Just so we are clear.

Can you still manually boot to that Ubuntu version off the external USB? By manually boot, I mean access the pre-OSX recovery menu (holding mac button + alt?) and all your bootable items should be shown there including your external USB....

So it sounds like Refind just launches the new/cloned Ubuntu version now instead of your old one on the external USB, but that is not what you want? How many operating systems do you have installed and have you tried to use the integrated Refind boot repair tool?

---

### Post by theodore-r on 2014-11-04
Hi. I'm using the "Late 2012" model mac mini. I currently have three hard drives. 

The internal drive is MacOS 10.10. I have it installed for future reference but don't use it at this time. 

I have two external USB drives. 
     First is MacOS 10.9.x and is my main working system. 
     Second USB drive is partitioned: the main partition is for backups, and I have one ext4 partition for ubuntu, and a swap. 

I always seem to have to reinstall REFIND after MacOS system updates, but this time REFIND doesn't show any linux installs. Holding option at startup doesn't show it either. I'll try booting from a live CD to see if that does anything.

---

