---
title: "Grub error 17"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by cj2008 on 2008-03-16
I've got Unbuntu and Vista installed on my PC. It seemed to be working fine, but then I tried cleaning up what I thought were some unneccasary partions, and now I'm getting a grub error 17 when I boot.

I've looked at some similar posts in this forum, but not found anything that works so far. Could anybody help me?

I've pasted below the output of sudo fdisk -l i case this helps.

****************************************************
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca521328

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1558    12506112   27  Unknown
/dev/sda2   *        1558       11672    81245184    7  HPFS/NTFS
/dev/sda3           11672       20786    73210201+   f  W95 Ext'd (LBA)
/dev/sda4           20787       30402    77229056    7  HPFS/NTFS
/dev/sda5   *       16263       20595    34804791   83  Linux
/dev/sda6           20596       20786     1534176   82  Linux swap / Solaris

Disk /dev/sdb: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xe8e5cd2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         961     1981936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 128, 32) logical=(960, 31, 32)
****************************************************

---

### Post by bumanie on 2008-03-16
Boot up the live install cd
Then In terminal 
> sudo grub
grub>>  root (hd0,4)
grub> > setup (hd0)
grub> > quit
That should reinstall grub
If that doesn't work, try downloading super grub disc (live cd) or read this guide
users.bigpond.net.au/hermanzone/p15.htm

---

