---
title: "Hard Drives are Gone"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by dover19 on 2008-04-19
I had customized my desktop and everything using images from the hard drives where my media is stored. Once I booted into windows, it did a scandisk and when i cane back to ubuntu all my custom setting we're gone.

I realized that when I went into my medi folder, my other hard drives don't even show up anymore, only my CD-ROMS show up.

---

### Post by frup on 2008-04-19
open terminal and type gedit /etc/fstab and post the contents

exit gedit and then type fdisk -l and post the contents

---

### Post by dover19 on 2008-04-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=459dc274-9665-4219-a7f0-257ec89b2b56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=43d815ab-ec9d-49ae-ac00-253b6812416d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...


I just noticed my widgets aren't there anymore either. How could that have anyhting to do with my hard drives? I don't understand why it wouldn't of kept all my settings.

---

### Post by maddog39 on 2008-04-19
If there are disk read or sector errors you could have all sorts of wonky things going on with your system that are probably related to a physical problem on the hard drive itself. You may want to consider purchasing a tool such as SpinRite and running it for recovering bad sectors and their data on the disk.

---

### Post by frup on 2008-04-19
> **dover19 said:**
>  [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)


sorry sudo fdisk -l (that's an L)

should output something like 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123        1338     9767520   83  Linux
/dev/sda3            1339       19457   145540867+  83  Linux

will help show if the drives are correct.

---

### Post by dover19 on 2008-04-19
Well, I had to remount my drives and put my settings back the way they were, but shouldn't my drive stay mounted even if i reboot?

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d340d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12988   104326078+   7  HPFS/NTFS
/dev/sda2           12989       24415    91787377+  83  Linux
/dev/sda3           24416       24792     3028252+   5  Extended
/dev/sda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67bd6faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3d24c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by frup on 2008-04-19
you need to add sdb1 and sdc1 to your fstab and set up a mount point for them on boot.

The fstab file is a table of what ubuntu mounts automatically and assigns where to mount the partitions. It would probably have done it by default if they weren't NTFS

this may be incorrect and you should wait until someone else verifies it but adding 
/dev/sdb1 /path/to/mount/ ntfs 0 0
/dev/sdc1 /path/to/mount/ ntfs 0 0

to the end of your fstab file should fix the problem when you reboot. you need to open fstab with sudo to edit it.

---

