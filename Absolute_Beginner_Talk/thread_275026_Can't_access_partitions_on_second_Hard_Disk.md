---
title: "Can't access partitions on second Hard Disk"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-10-10
I'm trying to access partitions on my other hard disk from Ubuntu (I have two hard disks) but when I go to "Computer" in nautilus and double click on the partition it gives me this error message:

> 
Unable to mount the selected volume.
error: device /dev/hdb4 is not removable

error: could not execute pmount


Same for my other partition:

> 
Unable to mount the selected volume.
error: device /dev/hdb1 is not removable

error: could not execute pmount


I should also mention that these partitions do not show up in the GRUB menu at bootup.  However, I have successfully mounted one of these partitions in a folder on my Desktop...  Any help would be much appreciated.

---

### Post by taurus on 2006-10-10
What does your /etc/fstab look like and the partitions of your second harddrive?

```
more /etc/fstab
sudo fdisk -l
```

---

### Post by fatsheep on 2006-10-10
> **taurus said:**
> What does your /etc/fstab look like and the partitions of your second harddrive?

```
more /etc/fstab
sudo fdisk -l
```

Output of more /etc/fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Output of sudo fdisk -l:

> 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3835    30804606   83  Linux
/dev/hda2            9355        9729     3012187+   5  Extended
/dev/hda5            9355        9729     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2422    19454683+   7  HPFS/NTFS
/dev/hdb3            4819        4870      417690    f  W95 Ext'd (LBA)
/dev/hdb4            2423        4818    19245870   83  Linux
/dev/hdb5            4819        4870      417658+  82  Linux swap / Solaris

Partition table entries are not in disk order


In other words, yea the fstab file doesn't contain the partitions on my other hard drive.

---

### Post by PPAAUULL on 2006-10-10
Try ```
sudo mount /dev/'hda_or_whatever' /mnt/
``` that is how I mount my drives or partitions when I need them.

---

### Post by CatKiller on 2006-10-10
[ How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

and [this]("http://www.psychocats.net/ubuntu/mountlinux") should give you the information you need to get that ext3 partition mounted, too.

---

### Post by fatsheep on 2006-10-10
Thanks guys, I'll post back if I have any problems but I think it's working.

---

