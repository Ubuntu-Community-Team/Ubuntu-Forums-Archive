---
title: "add a emtpy parition"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by adi82 on 2008-01-24
hi i want to add a partion to my hard disk and ad a boot of BackTrack3.
-what to take space from the partion of  Ubuntu.i think that i need 7MB

> adi@adi:~$ sudo fdisk -l
[sudo] password for adi:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60116011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3490    28033393+   7  HPFS/NTFS
/dev/sda2            6306        7296     7953088+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            3491        6183    21631522+  83  Linux
/dev/sda4            6184        6305      979965    5  Extended
/dev/sda5            6184        6305      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order



secend question :
what is this? (i have modified the boot menu) 
> Partition table entries are not in disk order

icant read from ubuntu the windows files(partion)! why?

---

### Post by mmb1 on 2008-01-24
You might want to use gparted to make a new partition.

Check your old thread, I give more detail there.

---

