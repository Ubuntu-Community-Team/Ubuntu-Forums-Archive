---
title: "[SOLVED] Dual Boot Installation Help..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-06-16
Here's the deal - I'm running 1 of my 8 computers on ubuntu right now.  I want to start installing on my other computers, but I can't figure out how to install in a dual boot comfiguration.

From the booted Live CD I select install, then a guided install to free space.  It proceeds then give me an error that it can't write to the disk.  I've tried on 2 different computers and get the same error.

Clean install of a single OS seems to go okay, but these systems require dual boot because I can't figure out how to get the wireless connections working at all - this makes windows a must so that the internet can be used.

Thanks...

---

### Post by floke on 2007-06-16
Live CD partitioner is crap (honestly).
Try the alternative installer. You'll love it.

---

### Post by crjackson on 2007-06-16
> **Steve.K said:**
> Live CD partitioner is crap (honestly).
Try the alternative installer. You'll love it.

I'll give it a try tomorrow I guess.

---

### Post by w4ett on 2007-06-16
It's also recommended that you defrag your drives before you use gparted...makes thing go smoother.

---

### Post by confused57 on 2007-06-16
> **crjackson said:**
> Here's the deal - I'm running 1 of my 8 computers on ubuntu right now.  I want to start installing on my other computers, but I can't figure out how to install in a dual boot comfiguration.

From the booted Live CD I select install, then a guided install to free space.  It proceeds then give me an error that it can't write to the disk.  I've tried on 2 different computers and get the same error.

Clean install of a single OS seems to go okay, but these systems require dual boot because I can't figure out how to get the wireless connections working at all - this makes windows a must so that the internet can be used.

Thanks...
I'm not sure if this is your problem or not, but there's a difference in free space on a partition and unallocated space, which isn't partitioned.  If you're referring to the former, you'll have to resize your Window's partition(defragment before resizing, as someone suggested).
The Ubuntu installer can resize NTFS partitions, but the gparted live cd has a later version of gparted and may be better able to resize NTFS:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

The Super Grub Disk is a handy utility to have, for booting problems:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mrphantastic on 2007-06-17
crjackson - I just PM'd you some idea's check out the links, I think they'll help...

---

### Post by crjackson on 2007-06-17
> **mrphantastic said:**
> crjackson - I just PM'd you some idea's check out the links, I think they'll help...

Thanks, I'll check it out...

---

### Post by crjackson on 2007-06-18
> **confused57 said:**
> I'm not sure if this is your problem or not, but there's a difference in free space on a partition and unallocated space, which isn't partitioned.  If you're referring to the former, you'll have to resize your Window's partition(defragment before resizing, as someone suggested).
The Ubuntu installer can resize NTFS partitions, but the gparted live cd has a later version of gparted and may be better able to resize NTFS:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

The Super Grub Disk is a handy utility to have, for booting problems:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The gparted CD won't boot on my machine, so I installed a 4th HD to install Linux on.  This is working out okay, but I can't do this on every single machine I own.  I haven't tried the alternative installer yet, so I'll try that and report back.

Thanks...

---

