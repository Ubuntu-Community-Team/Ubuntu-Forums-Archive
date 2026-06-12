---
title: "Drive not mountable"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-07
I have a Seagate FreeAgent Go 120 gb with a program called Ceedo installed. It allows you to download programs on the hard drive. It's NTFS. Ubuntu reads my other NTFS partition just fine, and Windows reads my external drive. When I had a Live CD, Ubuntu read my external HDD.
Here's what it gives me now:
Cannot mount volume.
Unable to mount the volume 'FreeAgent Drive'.
When I click details:
mount: wrong fs type, bad option, bad superblock on /dev/
sdb1,       missing codepage or other error    In some cases
useful info is found in syslog-try            dmesg | tail or so

What should I do?:(

Oh yeah, how do you do that code thing?:lolflag:

---

### Post by Inxsible on 2007-08-07
Since its and external drive use pmount to mount it.

Look at my signature to get a link. Also if the name of the drive is FreeAgent Drive (including the space) you will need to put quotes around it like so "FreeAgent Drive"

---

### Post by therunner on 2007-09-08
I have the same issues going on too.  Except my freeagent drive "squeeks" when it's hooked up to the machine(USB1).  It doesn't do this when hooked up to my XP laptop(USB2).  I don't know, but shouldn't make a difference, if having a USB2 device running through USB1.  

I have no clue on how to mount a device.
The machine doesn't even register the EHDD being connected. 

-Todd

---

