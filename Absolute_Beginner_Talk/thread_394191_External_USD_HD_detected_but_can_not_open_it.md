---
title: "External USD HD detected but can not open it"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ajmmon on 2007-03-26
Hi guys i am new to linux trying to come into the free world out of windows.

So far everything has been fine i have installed kubuntu in my laptop a Gateway m320, and i am fascinated how fine she works with it.

But after testing the 6.1 version everything was up and running then i saw the new kubuntu beta version and came into it rightaway, so far everything is fine except that i cannot access my external USD IDE hard drive box. The machine works fine with all other USB devices, memory sticks, mouse, wireless mouse, except the external hard drive.

The system detects it and try to open it, but does not show anything. I go to /dev/disk/by-label with conkeror and it show the label of the hard drive, but i still can not have access to it. The hard drive is NTFS formatted.

Any ideas
Pls remember i am new to this, Thx.

This is a submission ID of my hardware to kubuntu 35afc7104324718a58094589010a9612

========================================
ajm@ajmkub705:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4688    37656328+  83  Linux
/dev/sda2            4689        4864     1413720    5  Extended
/dev/sda5            4689        4864     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

=============================================================
ajm@ajmkub705:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=af9d2ff7-8ad9-4fe5-aff9-4de7c463f0d7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=28944360-6063-4a34-bf07-0bc104af33f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

==============================================================

As you can see my USB drive is not there on shows in the fdisk -l

---

### Post by gh0st on 2007-03-26
Hi, welcome to the free world :) 

Check out this thread [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

The guy who started it is one of the developers of NTFS-3G, Ubuntu/Kubuntu doesn't ship with read/write drivers for NTFS, this should help a bit. If you can't get it working you could post a reply in the thread the guy promises to answer all questions himself. Can't say fairer than that.

It just occurred to me your drive should probably work in read-only mode anyway. Hmm :-k You might need to run a disk check on it, there could be minor errors stopping Linux from mounting it.  I have had to do that a couple of times to get NTFS drives playing with Ubuntu. If you have a Windows PC still then plug the USB disk in and do a disk check on it and fix any errors or bad sectors.

Sometimes when you remove a USB drive from a PC without properly unmounting it you are left with errors and irregularities on the disk. I found that a few times with Windows particuarly. 

You have to use "safely remove hardware" thing in windows or this happens. Luckily I managed to "safely remove windows" and now I don't get that problem :)

Good luck

---

### Post by ajmmon on 2007-03-26
Thx for the prompt reply my HD has not developed any problems, i could use it before the upgrade to kubuntu feisty 7.04 beta, is after i installed it when the no access issue began.

Any ideas?

---

### Post by gh0st on 2007-03-26
Ahh right, I 'm not sure what to suggest. Fiesty is still in Beta so maybe there is a bug in it or something. You could try reporting this in the Fiesty development forum and seeing if it's a common issue or if anyone else has seen it.

Other than I don't what to suggest. Sorry :( 

Good luck with it though, I'm sure one of the clever people around here will be able to help you out :)

---

