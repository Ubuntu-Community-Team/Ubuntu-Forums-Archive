---
title: "[SOLVED] Mounted partition desktop icon name"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bsh on 2007-10-04
I have Ubuntu 7.04, using XFCE.
I have had two ntfs partitions on the hard drive, which were mounted via ntfs3g. I decided to use ext3 instead of ntfs on the bigger partition (MSDOS label was "PART_D"), so I unmounted that partition, made an ext3 filesystem on it, and re-mounted.
Before i did that, the mounted partition's icon had the msdos label as a name "PART_D". Now with ext3, it just displays a generic name as "62G Volume", i guess 62G is the size of the volume.
I can not rename this "shortcut". Is there a way I could change this?
Thanks

---

### Post by benerivo on 2007-10-04
You could mount it in somewhere other than /media so that it does not appear on the desktop. You could put in /mnt, then make a real shortcut on the desktop that you can call whatever you like.

---

### Post by doncristobal on 2007-10-20
I have the same (or a similar) problem. 
A right mouse click on the partition in question gives me the option "Properties". There i have a field to enter the name, but it seems to be blocked (pressing keys just produces beeps). 
There must be a way to change the names through this properties dialog, isn't it?

Info:
I have three windows readable partitions (fat32, ntfs) that are automatically mounted and labeled in a strange way: 
* fat32 data partition is labeled "54G Volume". In the graphical installer i decided to mount it to /media/data
* the 2 ntfs partitions that windows/ibm need are called "IBM_PRELOAD" and "IBM_SERVICE". They are mounted as /media/win and /media/ibm

Anyone got an idea? Thank you in advance.

---

### Post by natsbar on 2007-10-24
Had the same question and found the answer in this thread.

[http://ubuntuforums.org/showthread.php?t=513168]("http://ubuntuforums.org/showthread.php?t=513168")

---

### Post by bsh on 2007-10-30
that only works with fat or ntfs drives, but i have ext3.

i have found the solution. after i created the ext3 filesystem, it had no label, that's why the window manager displayed "62G volume".
i assigned a label to this partition with E2LABEL, but it did not seem to work. but after a reboot, it did work. it just needed a reboot.
maybe it would have been sufficient to unmount and remount the filesystem, dunno.
but e2label is definitely the solution.

---

