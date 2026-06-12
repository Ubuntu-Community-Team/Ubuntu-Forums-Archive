---
title: "Formatted Windows Partion - how do i link it to my home drive?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by pinkpajamafairy on 2007-01-22
Ive been trying to delete the windows partion on my harddisk and make a datadrive as im running out of space.

Using gparted i deleted the windows partion and made a new partion thats ext3.

I changed the boot partion using cfdisk /dev/hda

The printout using sudo fdisk -l shows:

> Disk /dev/hda: 20.0 GB, 20003880960 bytes
16 heads, 63 sectors/track, 38760 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         606      305203+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       20146       37920     8958600   83  Linux
/dev/hda3           37921       38760      423360    5  Extended
/dev/hda4             606       20145     9847845   83  Linux
/dev/hda5           37921       38760      423328+  82  Linux swap / Solaris

Partition table entries are not in disk order

From what i can tell, hda2 is my current used disk space, and hda4 is the one i just created.

Is there any way i can link hda4 to hda2 without having to reinstall everything?

---

### Post by housam on 2007-01-22
You can read this guide ,it may help.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by seshomaru samma on 2007-01-22
I think what you want is to mount the new partition you created , right?
If so ,read[ this ]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by pinkpajamafairy on 2007-01-22
Thanks!

That second page was exactly what i needed to do.

---

