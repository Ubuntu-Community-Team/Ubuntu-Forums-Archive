---
title: "followed the instructions and still no FAT32 partitions visible"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-02-19
I have installed Ubuntu on my Dell Inspiron E1505's 30 GB hdd. I partitioned the hdd into (3) 10GB sections. (There are also 2 small partitions on the HDD that Dell put there).

Ubuntu 6.10 Edgy Eft is on the first 10GB partition, the other two partitions I made by creating one 20GB Extended Partition, then created (2) 10GB partitions within that (Ubuntu also made a swap partition, of course). I made them both FAT32 since I intend to use one to install Windows XP on, and use the other as a shared drive on which I can store files to be used by both Ubuntu and WinXP. I made them with the default Ubuntu install CD partitioning software.

After installing Ubuntu I could not access the two FAT32 partitions I had made, then I realized I probably needed to format them, so i did that, and also i followed the instructions for modifying the /etc/fstab file to automount the partitions at [https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6)

The partitions did not show up so i followed the instructions for modifying the pmount.allow file at [https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28partitions%29%7C%28mount%29#head-7036f2492d04f1d0984017ad8e71af0eda2690d6](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28partitions%29%7C%28mount%29#head-7036f2492d04f1d0984017ad8e71af0eda2690d6)

I still was unable to see the partitions in the folder i made ( /media/part ) so I rebooted, that did not help either. Then i tried the commands: sudo mount -a and sudo mount /dev/sda5 /media/part
neither of which returned any errors, but i still could not see the partitions where i understand they should be in ( /media/part ). I can see them in the device manager, and also when i run fdisk. I am now at a loss as to how to mount these partitions so i can begin storing files on them. Can anyone help? I am a complete nOOb with Linux so please be very specific and gentle. Below is some additional info which may help you shed light on this, if any other info is needed let me know. Thanks in advance.


CONTENTS OF FSTAT:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=79e3c055-96c7-469f-9d8d-bb05b504f151 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7
UUID=6bc57b4d-2007-4210-83e1-dc9b013477e2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda5 /media/part vfat user,fmask=0111,dmask=0000 0 0
/dev/sda6 /media/part vfat user,fmask=0111,dmask=0000 0 0


CONTENTS OF PMOUNT.ALLOW

# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/sda5
/dev/sda6


CONTENTS OF TERMINAL OUTPUT OF: sudo fdisk -l

Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 1349 10795680 83 Linux
/dev/sda3 4075 4680 4867695 db CP/M / CTOS / ...
/dev/sda4 1350 4074 21888562+ 5 Extended
/dev/sda5 1412 2689 10265503+ b W95 FAT32
/dev/sda6 2690 4074 11124981 b W95 FAT32
/dev/sda7 1350 1411 497952 82 Linux swap / Solaris

---

### Post by overdrank on 2007-02-20
Hi I have not tried this yet was going to try it. Maybe it will help you I hope
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

good luck

---

### Post by bodhi.zazen on 2007-02-20
First, you need a unique mount point for each partition.

You can not mount both partitions at /media/part at the same time.

Second, you should not mix pmount and mount. mount uses fstab (or not as root), pmount is for partitions not listed in fstab.

paul capps gave you a good link for how to mount via fstab :p

If you want to go with pmount, the command is :

pmount <partition> <abbreviated_mount_point>

abbreviated mount point because pmount always mounts in /media

Example:

```
sudo rm -R /media/part
pmount /dev/sda5 sda5 -o umask=000
pmount /dev/sda6 sda6 -o umask=000
```

---

