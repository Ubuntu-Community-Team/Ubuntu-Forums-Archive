---
title: "DVD installer fails to detect partitions on internal disk drive"
date: 2005-11-02
forum: Apple PPC Users
---

### Post by danchr on 2005-11-02
Hi,

I'd like to give Ubuntu a try to supplement my Mac OS X installation, and I believe I have what's needed to do so. However, the installation wizard on the DVD gave me no other options than deleting the partition table on the internal hard drive. Needless to say, I don't want to do that.

I tried manually partitioning my hard drive, by using the option to get a shell in the installer. I added bootstrap, swap and standard Linux partitions using mac-fdisk. I even tried formatting the standard partition as ReiserFS, but that didn't help either.

Here's a dump from Darwin's pdisk, and it's quite similar to the output of mac-fdisk:
```
% sudo pdisk /dev/rdisk0 -dump

Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name               length   base      ( size )
 1: Apple_partition_map Apple                  63 @ 1        
 2:          Apple_Boot eXternal booter    262144 @ 64        (128.0M)
 3:          Apple_HFSX Tiger            62914560 @ 262208    ( 30.0G)
 4:           Apple_HFS Users           167772160 @ 63176768  ( 80.0G)
 5:     Apple_Bootstrap bootstrap            1600 @ 230948928
 6:     Apple_UNIX_SVR2 swap              4194304 @ 230950528 (  2.0G)
 7:     Apple_UNIX_SVR2 Ubuntu           41943040 @ 235144832 ( 20.0G)
 8:          Apple_Free Extra            35493936 @ 277087872 ( 16.9G)

Device block size=512, Number of Blocks=312581808 (149.1G)
DeviceType=0x0, DeviceId=0x0

```

Perhaps my HFSX Tiger partition is throwing it off? My plan is to use whichever Linux disk format is recommended, and then users my Mac OS X /Users (which is Journaled HFS+) partition for sharing data between the two installs. I would have used Ext3 if the Darwin Ext2 driver worked with Mac OS X 10.4.

---

### Post by jdp on 2005-11-02
You don't really need to make all the partitions for Ubuntu, just leave enough free space.  You can just leave the Ubuntu and swap space as empty space and the installer should ask if you want to wipe the drive or use the largest free space.  You choose the free space option and it'll setup the partitions for you.  If you don't mind deleting and moving your OS X partition (and everything on it going bye-bye ;)) to put it at the end of the disk, it'll help keep yaboot functional.

---

