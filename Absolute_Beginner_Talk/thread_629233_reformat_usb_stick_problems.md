---
title: "reformat usb stick problems"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by natman on 2007-12-02
When i run fdisk to reformat like this:> natman@natman-laptop:~$ sudo fdisk -l
[sudo] password for natman:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b1f584

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10248    82317028+   7  HPFS/NTFS
/dev/sda2           18771       19097     2626627+   f  W95 Ext'd (LBA)
/dev/sda3           10249       18770    68452965   83  Linux
/dev/sda5           18771       19097     2626596   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1046 MB, 1046214656 bytes
33 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 2013 * 2048 = 4122624 bytes
Disk identifier: 0x000e06c6

   Device Boot      Start         End      Blocks   Id  System
natman@natman-laptop:~$ fdisk /dev/sdb
Note: sector size is 2048 (not 512)

Command (m for help): d
No partition is defined yet!

Command (m for help): p

Disk /dev/sdb: 1046 MB, 1046214656 bytes
33 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 2013 * 2048 = 4122624 bytes
Disk identifier: 0x000e06c6

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-253, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-253, default 253): 
Using default value 253

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 13: Permission denied.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
natman@natman-laptop:~$ 

It never works, can anyone help?

---

### Post by uclalinux on 2007-12-03
When you plug in your USB stick make sure it does not auto mount. it if does you will need to un-mount it. the is should work, also after you fdisk it, you need to "mke2fs -j" if using ext3, but I would make the USB thumb  windows readable too, so FAT32, FAT16 or NTFS.

---

### Post by tarooooq on 2008-06-04
hello im also having the same issue with my IPOD i foramt it by misstake and now im trying to create the patition again using the fdisk 
but when i create the partitions and apply them i got error saying unable to mount volume
Details:( mount/dev/sdb2: cant read superblock )

please help

---

