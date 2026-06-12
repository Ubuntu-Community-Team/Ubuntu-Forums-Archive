---
title: "dual boot iMac OS 10.6"
date: 2016-11-17
forum: Apple Hardware Users
---

### Post by goodwell on 2016-11-17
I got my Dell running Ubuntu 16.4!  (See my last posting, "booting from USB trouble.")  Now I want to set up my brand new, 27" iMac as a duel boot device.  SCARRY!  At least it is for me.

How big a partition do I need?  I don't think I will be a heavy user.  Photos, Music and files I share with my wife will stay in Mac OS, but I want to be able to run a Unix CAD program and maybe do some 3-D printing.

What else do I need to know before I start?  What trouble do I need to avoid?  If at all possible, I don't want to go back to Apple, hat-in-hand and beg them to wipe my drive and reinstall my Mac OS.

---

### Post by QIII on 2016-11-17
Moved to Apple Hardware Users for a better shot at good responses.

---

### Post by g33zr on 2016-11-18
I recommend installing rEFInd (see: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)) in your OSX system first and then installing Ubuntu next to it. Before you install Ubuntu, you're going to have to re-partition your hard drive. You can use OSX's disk utility or a gparted CD to repartition the drive. When I dual-booted my MacBook and IMac, I kept ca. 200 GB for OSX and the rest for Linux, but that's up to you. You might want to research recent how-to dual-boot a Mac info before you begin.

---

### Post by goodwell on 2016-11-18
If I guess wrong on the partition, can I change it later, shift unused storage from one partition to the other?

---

### Post by g33zr on 2016-11-18
I suggest that you shouldn't "guess" about a partition, but plan ahead. The first three partitions in your partition table should be your efi partition, OSX partition, and restore partition. Your Ubuntu partitions could be / and swap, or /, swap, and /home, depending on the install method you choose. Again, do a little research before you proceed.

---

### Post by goodwell on 2016-11-19
Thanks.  I guess I have some reading to do before I start.

---

