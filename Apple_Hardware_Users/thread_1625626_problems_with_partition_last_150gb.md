---
title: "problems with partition last 150gb"
date: 2010-11-19
forum: Apple Hardware Users
---

### Post by OldAbe on 2010-11-19
I have some problems with my partitions on my driver. I cant add the last 150GB free space on my SSD drive to FAT32. 

Any one that find the time to help me solve the problem. please..
Hear is some information that my be to help what I have done wrong.

Thanks
/Abe

__________________________________________________  ____

skitgubbe@macbook-air:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb000ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        6713    53710940   af  HFS / HFS+
/dev/sda3   *        6729       10498    30272512    7  HPFS/NTFS
/dev/sda4           10498       11957    11718656   83  Linux


__________________________________________________  _______________


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

---

### Post by prshah on 2010-11-19
> **OldAbe said:**
> 
skitgubbe@macbook-air:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        6713    53710940   af  HFS / HFS+
/dev/sda3   *        6729       10498    30272512    7  HPFS/NTFS
/dev/sda4           10498       11957    11718656   83  Linux


First, as suggested, please use GnuParted, or Palimpsest.

Second, you already have 4 partitions. Though GPT allows for upto 128 partitions, your HDD has to be in a non-legacy mode (though everything looks OK), otherwise you are restricted to 4 partitions. Please post back with a description of the exact error you are facing.

---

### Post by srs5694 on 2010-11-19
The disk apparently uses a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) meaning that the fdisk output you posted is likely to be incomplete. You should use parted or gdisk instead. It's conceivable that your disk is already fully allocated, but that's far from clear at this point.

Also, I'm guessing from the types of the MBR partitions that this is a triple-boot system (OS X, Windows, and Linux). When you post back with the gdisk or parted output, you should also tell us precisely what you hope to accomplish with the 150GB FAT32 partition you say you want to add. Although Linux and OS X can both read GPT partitions directly, Windows can't, so you may need to adjust your hybrid MBR to include all the partitions that should be readable by Windows.

---

