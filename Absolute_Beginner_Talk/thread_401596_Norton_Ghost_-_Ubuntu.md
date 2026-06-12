---
title: "Norton Ghost - Ubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-04
I just wonder if there is possible to install Norton Ghost on ubuntu? or use a bootable disc to take backup of my linux disk? i would be great so that i can experiment more without needing to install the system everytime i fail completly :lolflag:<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by LaurelLynn on 2007-04-04
Dear U5tabil,

One thing about Linux is that there are several ways to do the same thing (usually without buying commercial software).

I´m an old dinosaur so I still use the old data dump utillity - dd (even for windows partitions):

dd  if=/dev/hda1 of=/dev/sda1/hda.dd

Will copy the first hard drive partition to a file on a USB drives first partition. To restore:

dd if=/dev/sda1/hda.dd  of=/dev/hda1

To backup the MBR:

dd if=/dev/sda   of=/dev/sda1/hda.mbr bs=512 count=1

The advantage of dd is that it works from any Live CD.

Partimage is a front end program to this command which may or may not be on your Live CD. It is a step up from dd and helps prevent you from accidentally mixing the filenames up (with dire consequences).

There are other partition backup options (such as ddd)  which I sure the next person to read these post will be able to share with us.

Note backing up whole partitions can take a long time.

Laurel Lynn

---

### Post by aum11 on 2007-04-04
There is a new tool - Clonezilla- which has just been released by the gparted team which does the job of cloning the whole disk.  [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

