---
title: "Hdd help"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by jorpe on 2007-06-22
I could use some help, becuse i cannot modifie any thing on my existing disk.. Only thing i can do is read the disks and watch the files. How to fix so you can do whatever you want on the disk?..

Greatfull for answers!,

---

### Post by mikewhatever on 2007-06-22
Can you post the output of the following command from the terminal and specify which disk you want to modify permissions for
> sudo fdisk -l

---

### Post by jorpe on 2007-06-22
jorpe@jorpe-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1153     9261441   83  Linux
/dev/hda2            1276        9963    69786360    f  W95 Ext'd (LBA)
/dev/hda3            1154        1275      979965   82  Linux swap / Solaris
/dev/hda5            1276        9963    69786328+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/hdb5               2       30401   244187968+   7  HPFS/NTFS

Would like to be able to modify both disks? =p

---

### Post by mikewhatever on 2007-06-22
It looks like you need to install ntfs-3g package from the repositories to be able to write to ntfs. Do you also have problems writing to FAT?

---

### Post by jorpe on 2007-06-22
Ahaa, well... don't got any FAT system ? how do i know if theres no problem to write to FAT btw?
whats that package ?

---

### Post by wormser on 2007-06-22
Applications> Accessories> Terminal

```
sudo apt-get install ntfs-3g ntfs-config
```

Then you go to Applications> System Tools> NTFS Configuration Tool

---

### Post by mikewhatever on 2007-06-22
> Ahaa, well... don't got any FAT system ?
What are these partitions then?
/dev/hda2 1276 9963 69786360 f W95 Ext'd (LBA)
/dev/hdb1 2 30401 244188000 f W95 Ext'd (LBA)

The ntfs-3g enables Linux to write to ntfs file system, something it can't do by default. Read more on their site [http://www.ntfs-3g.org/index.html](http://www.ntfs-3g.org/index.html)

---

### Post by jorpe on 2007-06-22
> **mikewhatever said:**
> What are these partitions then?
/dev/hda2 1276 9963 69786360 f W95 Ext'd (LBA)
/dev/hdb1 2 30401 244188000 f W95 Ext'd (LBA)

The ntfs-3g enables Linux to write to ntfs file system, something it can't do by default. Read more on their site [http://www.ntfs-3g.org/index.html](http://www.ntfs-3g.org/index.html)

That I don't know.. I've haven't done a fat disk.. but.. when I installed Ubuntu I only erased the windows C: partion and diden't formate the other disks..

maybe that 
/dev/hdb1 2 30401 244188000 f W95 Ext'd (LBA)
/dev/hdb1 2 30401 244188000 f W95 Ext'd (LBA)
is something that windows left behind it self?..

Wormser:
I've ran the command, but when I tried to configurate the disks this came up..

Mounting /media/hda5 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/BECC94F0CC94A465': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.


And when I ran that command the disks disappeared.

---

