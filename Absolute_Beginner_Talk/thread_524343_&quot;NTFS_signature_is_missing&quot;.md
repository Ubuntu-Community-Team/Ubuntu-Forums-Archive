---
title: "&quot;NTFS signature is missing&quot;"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by NorvilleBarnes on 2007-08-13
When I try mounting my USB drive, which I haven't had problems with in the past, I get this message:> 

ntfs signature is missing.

failed to startup volume: invalid argument

failed to mount '/dev/sda1': invalid argument

the device '/dev/sda1' doesn't have a valid ntfs.

maybe you selected the wrong device? or the whole disk instead of a

partition (e.g. /dev/hda, not /dev/hda1)? or the other way around?

How do I get around this?

---

### Post by ddrichardson on 2007-08-13
Looks like the partition table on the device is wrong - if you don't need any data on the device use fdisk to repartition it and then format it.

---

### Post by schorsch on 2007-08-13
Type
```
sudo fdisk -l
```
in a terminal window and post the output here.
BTW, it is an lowercase L at the end ...

---

### Post by NorvilleBarnes on 2007-08-13
Here's my fdisk:

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9566    76838863+  83  Linux
/dev/hda2            9567        9729     1309297+   5  Extended
/dev/hda5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1956      500720    e  W95 FAT16 (LBA)


---

### Post by schorsch on 2007-08-13
According to the partition type of /dev/sda1 it could be a vfat-filesystem on the device, not a ntfs-filesystem. Have you tried to mount it this way:
```
 mount -t vfat /dev/sda1 /media/usbdisk
```
Just change /media/usbdisk to a mount point of your choice.

---

### Post by NorvilleBarnes on 2007-08-14
Works, thanks!

---

### Post by schorsch on 2007-08-14
Could you please mark this thread as solved then and in addition to that add "[SOLVED]" to the title of your first post? Thanks!

---

