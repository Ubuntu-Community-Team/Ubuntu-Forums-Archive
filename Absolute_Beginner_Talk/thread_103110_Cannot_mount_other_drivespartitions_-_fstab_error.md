---
title: "Cannot mount other drives/partitions - fstab error"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Pattycake on 2005-12-13
Rank newbie here.  I just installed Ubuntu Breezy and only my usb harddrive appears on the desktop.  Following directions to mount drives I open fstab in terminal to find an error msg where my other two harddrives should be.  The optical drives are all there though.

Where do I go from here, o linux gurus?

---

### Post by kori.mendocino on 2005-12-13
would you paste the error msgs?

---

### Post by Pattycake on 2005-12-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by nitricacid on 2005-12-13
I actually have a similar error dealing with my CDROM drive.

Here is my error:
Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount


It seems it only recently happen after I installed some of the updates.

---

### Post by kori.mendocino on 2005-12-13
pattycake, if ubuntu is installed and running, then your root partition (the first entry in your fstab) is mounted and working correctly. the other partition, hdd6, doesn't have a directory to be mounted at. issue $ sudo mkdir /media/part2 (or whatever you want to call this dir), edit your fstab accordingly, and issue $ sudo mount -a

---

