---
title: "GRUB - triple booting 3 systems"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by thereallos on 2007-01-04
Hi ... I was wondering if anyone would have some advice for me. I've got two hard drives installed. I have Dapper on the first one and Edgy on the second one.  Each drive is split into 3 partitions. Here is the output of: ```
sudo fdisk -l
```

> Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2675    21486906   83  Linux
/dev/sda2            2676        2803     1028160   82  Linux swap / Solaris
/dev/sda3            2804       30401   221680935   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        1402     1020127+  82  Linux swap / Solaris
/dev/sdb3            1403       30401   232934467+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System


My two ubuntu installation are setup with 3 partitions each:

/
/home
and a swap partition

I'm assuming that GRUB is installed in /boot of each installation and therefore I have two menu.lst files. How does  the computer decide which one to use? Should I have created an independent /boot partition and used it for both installations? And if so how do I go about fixing it without ruining my current installations?

After I've fixed this I'm hoping to install XP on the 320 gig hard drive I've got. Is there anything I should know regarding GRUB before attempting this?

---

### Post by MasterOfDisaster on 2007-01-04
Well, if you install XP last, it will overwrite GRUB and automatically boot you into Windows.

The solution to this would be to reinstall GRUB, detailed in this thread:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Oh, yea, you only need one swap and one home partition for both Ubuntu's...  They both can use these unless you remove the hard drives occasionally.

---

### Post by geek_Man on 2007-01-04
You beat me to 'em... :mad:

---

