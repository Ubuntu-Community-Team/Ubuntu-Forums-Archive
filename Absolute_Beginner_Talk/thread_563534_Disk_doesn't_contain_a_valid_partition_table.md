---
title: "Disk doesn't contain a valid partition table"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-30
Does anyone have any idea why I keep finding Disk /dev/sdd doesn't contain a valid partition table and the USB drive will not mount?  The drive can be working one day and fail the next.    Since this happens with two drives I do not think this is specific to the drive.

To fix the problem I have tried running fsck /dev/hdd but the message back is 

fsck /dev/sdd
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

which is a bit strange since the drive is formatted to ext3.


fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        2805     2048287+  82  Linux swap / Solaris
/dev/sda3            2806        9052    50179027+  83  Linux
/dev/sda4            9053        9729     5438002+   f  W95 Ext'd (LBA)
/dev/sda5            9053        9729     5437971   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12493   100349991   83  Linux
/dev/sdb2           12494       24321    95008410    f  W95 Ext'd (LBA)
/dev/sdb5           12494       19946    59866191   83  Linux
/dev/sdb6           19947       20711     6144831    b  W95 FAT32
/dev/sdb7           20712       24321    28997293+   b  W95 FAT32

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9023    72477216    c  W95 FAT32 (LBA)
/dev/sdc2            9024       24321   122881185    f  W95 Ext'd (LBA)
/dev/sdc5            9024       24321   122881153+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdd doesn't contain a valid partition table


So I would like to understand what is the problem.  I had thought from reading round google I got the idea that this was related to writing and deleting large amounts of data on a USB drive but I now think this is not  the case since on the latest failure the drive has not been used ... powered down and the following day powered up.

---

### Post by ryanVickers on 2007-10-03
Odd, This one time, I had this external drive on USB, and it suddenly just died - no read/write - gparted could find no partition, creating a disk label to create new partitions failed - I thought it just blew up or something! :)  I managed to unmount it, and plug it back in a couple of times, and then it worked perfectly!](*,):-k:???:

It could very well be bad, and it's just not noticed all the time - try formatting it completely and see if the problem goes away (if this is not too much trouble).  If not, then it could be bad hardware :(

---

