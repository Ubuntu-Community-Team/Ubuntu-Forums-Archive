---
title: "Transferring files"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Auria on 2007-01-06
Hi, i just installed Ubuntu on my mac PPC and am now trying to transfer my old files to it.

I have an external drive i thought i'd use to transfer data. It has 2 partitions on it - one mac partition (HFS i believe) and the other Unix filesystem.
Strangely enough, the HFS partition appears but the Unix one doesnt.

I am able to open the mac partition and see the files on it (though they have a big red X on them, what's that?), but i cant seem to be able to copy the files on it. No error message pops, it just does nothing. I also tried to open the files from where they are, but it said i didn't have the permissions to do that. It treats it as a read-only volume, so i can't seem to be able to change permissions.

What can i do?? Thanks =)

---

### Post by taurus on 2007-01-06
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
And if you want to mount the other partition, ext3, then you need to know which one it is?  Is it /dev/sda2?

```
sudo fdisk -l
```

---

### Post by quartzy on 2007-01-06
Also can you post the result of 

```
cat /etc/fstab
```

---

### Post by Auria on 2007-01-06
apparently the partition i'm traying to access is /dev/sda5 

gksudo nautilus:

what is that for? it just openend a bunch of windows, none of them being the right one. When i look in places->computer, what i'm looking for is just not there

sudo fdisk -l:

/dev/sda
        #                    type name                 length   base     ( size )  system
/dev/sda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k )  Partition map
/dev/sda2              Apple_Free                      262144 @ 64       (128.0M )  Free space
/dev/sda3               Apple_HFS Apple_HFS_Untitled_1 38810472 @ 262208   ( 18. 5G)  HFS
/dev/sda4              Apple_Boot eXternal booter       17408 @ 39072680 (  8.5M )  Unknown
/dev/sda5               Apple_UFS Apple_UFS_Untitled_2 39075256 @ 39090088 ( 18. 6G)  Unknown
/dev/sda6              Apple_Free                          16 @ 78165344 (  8.0k )  Free space

Block size=512, Number of Blocks=78165360
DeviceType=0x0, DeviceId=0x0

/dev/hda
        #                    type name                  length   base      ( siz e )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31. 5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 117187501 (977. 0k)  NewWorld bootblock
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1 116925293 @ 262208    ( 5 5.8G)  HFS
/dev/hda4         Apple_UNIX_SVR2 untitled           114996094 @ 117189455 ( 54. 8G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                 2256099 @ 232185549 (  1. 1G)  Linux swap
/dev/hda6              Apple_Free Extra                 262144 @ 64        (128. 0M)  Free space

Block size=512, Number of Blocks=234441648
DeviceType=0x0, DeviceId=0x0


cat /etc/fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

