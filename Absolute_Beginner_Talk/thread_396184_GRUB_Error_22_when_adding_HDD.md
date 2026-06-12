---
title: "GRUB Error 22 when adding HDD"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Lage on 2007-03-29
Hello. 
I have a problem with GRUB when adding a new hard drive to my system. I have been checking around but haven't found any post that describes just my problem.

I run a double-boot system with Ubuntu 6.10 and Windows XP. My HDD setup is thus:

* One IDE disk with a Windows partition, connected directly to motherboard
* One SATA disk connected directly to motherboard, containing one NTFS partition, one Linux swap and the partition with Ubuntu
* One IDE RAID controller with one disk attached to it (NTFS).

The problem arises when trying to add another IDE disk to the RAID controller. These two disks are identical, and each of them runs fine under Windows. Only when connecting both at once does GRUB give me "Error 22". GRUB loads fine no matter which of the two is connected, as long as not both are connected at once. Funny thing is, Ubuntu does not detect any drive attached to the RAID controller--which really doesn't matter since I intend to use these under Windows only. I have made sure master/slave jumper settings are correct, and even swapped the two.

At first I thought GRUB was installed on the SATA disk (where the Ubuntu partition is), but having disconnected this disk, thinking I might be able to start Windows XP without GRUB, GRUB still loaded. I hence conclude GRUB is installed on the same disk as Windows.

---

