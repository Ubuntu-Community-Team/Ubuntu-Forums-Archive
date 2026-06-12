---
title: "Help resizing partitions"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-25
Is there a free program for windows to resize NTFS partitions ? I tried google and all that stuff but everything is a trial.

---

### Post by taurus on 2006-03-25
Not sure about the freebie but Partition Magic can do that very well in Windows.  But if you already Ubuntu on that machine, you can also use gparted and of course, ALWAYS backup your important data before you resizing, no matter which OS you are in...

---

### Post by aysiu on 2006-03-25
Why does it have to be in Windows?

There are plenty of free programs for Linux that can resize NTFS--DiskDrake, QTParted, GParted.

---

### Post by WoodyMahan on 2006-03-25
Got to the gparted website and download the live cd.  It works great despite the OS.

---

### Post by xXx 0wn3d xXx on 2006-03-25
I've tried Knoppix and all that stuff but my touchpad won't work. I don't even have a port for a serial mouse :( I'm just going to install Ubuntu. I really like it and if it doesn't work then I'll just restore my system.

---

### Post by Omnios on 2006-03-25
The Ubuntu installer has a advanced manual partion option where I think you can type in the new partition size if I remember correctly however I have read stories where users get confused by it and deleate there win partition by accident so take your time and be carefull if you choose this option. After you change the partition size it will show you what changes are going to be made to the partion sdo just make shure your ntfs is still there.

---

### Post by Irony on 2006-03-25
See;

[http://ubuntuforums.org/showthread.php?t=142503&page=2&highlight=shrink+ntfs](http://ubuntuforums.org/showthread.php?t=142503&page=2&highlight=shrink+ntfs)

First you shrink the file system, then shrink the partition. I did this to my windows partition - shrinking it from 50 G to 10 G.

You'll have to install ntfstools via synaptic to resize the ntfs filesystem then use fdisk to shrink the partition.

---

