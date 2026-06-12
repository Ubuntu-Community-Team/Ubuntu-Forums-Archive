---
title: "Problems mounting my drives"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-01-10
I have 4 drives (2 160GiG and 2 80GiG) ubuntu is installed on one of the 80's.

I'm trying to mount the other 3,

this is what I have in my fstab file: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0db9dac-b626-40a9-a1e8-892798f057d7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ecfd003-75d0-4f2a-835d-8cdc38ac11f4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# removed floppy drive
#/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#
#
# 80GB torrents drive
UUID=b72c9c61-18bb-4e17-904c-ddfb0d83cd78   /mnt/torrents   ext3    users,atime,noauto,rw,nodev,exec,suid  0   0
#
# 160GB documents drive
UUID=d1818eaa-1a1e-48d7-94d0-ec05221b058c   /mnt/documents  ext3    users,atime,noauto,rw,nodev,exec,suid  0   0
#
# 160GB media drive
UUID=bb5021b9-df97-4059-b522-5da25af830b0   /mnt/media      ext3    users,atime,noauto,rw,nodev,exec,suid  0   0
```

Which to me looks like it should work, but what do I know :)

Anyway problem is when I browse to /mnt/torrents, /mnt/documents or /mnt/media and save any files there they are being stored in the folder not on the drive the folder should be pointing to. I know this because I tried to copy 100GiG of music to one of the 160's and it said there wasn't enough space (which there should have been because they were freshly formatted).

I formatted the drives using gparted which saw all the drives but someone on another board suggested that I should use QTParted so I gave it a go just incase I had somehow messed up the partitioning with gParted.

Problem is QTParted doesn't register the drives.

Can anyone shed any light as to why one partitioning tool sees the drives and the other doesn't.

Just incase it's needed here's the results when I type sudo fdisk -l ```
Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9332    74959258+  83  Linux
/dev/sda2            9333        9730     3196935    5  Extended
/dev/sda5            9333        9730     3196903+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9726    78124063+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321   83  Linux

Disk /dev/sde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdf: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1          10       80293+   0  Empty
/dev/sdf2              11         497     3911824+   b  W95 FAT32

``` sde is my external USB drive and sdf is my iPod nano.

---

### Post by mohjlir on 2007-01-10
No biggie. You have the option 'noauto' for the three drives you can't see. You can leave those lines in fstab how they are and mount them manually like this:

sudo mount /mnt/torrents

However, I think you probably want this to happen at boot time. Edit your fstab, and remove 'users,atime,noauto,rw,nodev,exec,suid', changing it to 'defaults'. Should work then.

If you don't know how to do that, use:

sudo nano /etc/fstab

---

### Post by unabatedshagie on 2007-01-10
](*,) ](*,) I guess I should have seen that :)

Thanks :D

---

