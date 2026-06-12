---
title: "USB Lacie repartitioned and now no read write"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-24
Hi all I have a Lacie Bigger disc 1Tb and I've been having heaps of problems..so I backed up and reformatted as a ext3 single partition drive (tried both primary and logical).
Anyway I now don't have any read write access....obviously for a drive this size this is a problem. I've looked at many threads chown commands etc and nothing really worked.
1 Thread got me read write options but it crashed ubuntu freezing me out so had to reformat drive again.

here is my fdisk -l readout

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045a7c70
[I]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14596   117242338+  83  Linux

Disk /dev/sdd: 1004.0 GB, 1004000772608 bytes
255 heads, 63 sectors/track, 122062 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      122062   980462983+   5  Extended
/dev/sdd5               1      122062   980462952   83  Linux[/I]

The drive mounts boot is owned by root.

Please help

Ta

Nigel

---

### Post by gn2 on 2007-11-24
What are you trying to do with the drive, file storage or bootable device?

---

### Post by hogwartsnigel on 2007-11-24
It is largely for archive retrieval....music files, video files, utility downloads image library font library etc

Thanks

Nigel

---

### Post by LinuxGuy1234 on 2007-11-24
> **hogwartsnigel said:**
> Hi all I have a Lacie Bigger disc 1Tb and I've been having heaps of problems..so I backed up and reformatted as a ext3 single partition drive (tried both primary and logical).
Anyway I now don't have any read write access....obviously for a drive this size this is a problem. I've looked at many threads chown commands etc and nothing really worked.
1 Thread got me read write options but it crashed ubuntu freezing me out so had to reformat drive again.

here is my fdisk -l readout

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045a7c70
[I]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14596   117242338+  83  Linux

Disk /dev/sdd: 1004.0 GB, 1004000772608 bytes
255 heads, 63 sectors/track, 122062 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      122062   980462983+   5  Extended
/dev/sdd5               1      122062   980462952   83  Linux[/I]

The drive mounts boot is owned by root.

Please help

Ta

Nigel

Ive found out that if unplug your USB stick and put it back in you can use:
```
sudo mount /dev/sdd1 /mnt/myusb
sudo chmod 777 /mnt/myusb
```

it'll work!

---

### Post by hogwartsnigel on 2007-11-24
Told me it didn't exist. It isn't a flash drive it is a 1TB USB drive.
Its really bugging me.

Thanks for the advice

Nigel

---

