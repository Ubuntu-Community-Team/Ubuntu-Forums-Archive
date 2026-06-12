---
title: "uninstall ubuntu"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by steve789 on 2006-06-18
ok so installed ubuntu on my laptop but i figure out that it runs too slow and i dont have much space on my harddrive  so now i want to uninstall ubuntu without erasing my Windows XP installation or any of my files

help please

---

### Post by nalmeth on 2006-06-18
Do you have a partitioning tool in Windows?
Because then you could delete the Ubuntu (EXT3) partition and resize the NTFS partition to fill the HD.

You should download the Gparted LiveCD to do this, it is a great CD.

BTW, have you tried xubuntu? I run it on my slower laptop, and it works great. It has the lighter XFCE desktop environment, and will take up less space.
[http://www.xubuntu.org/]("http://www.xubuntu.org/")

---

### Post by mlind on 2006-06-18
You should first wipe your MBR before doing anything else, removing partitions will
break GRUB and the ability to boot into windows. You can use XP's recovery console
and command FIXBOOT or download Windows98 bootdisk from bootdisk.com, boot
using the disk and do fdisk /mbr.

---

