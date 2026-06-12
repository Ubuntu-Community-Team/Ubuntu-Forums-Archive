---
title: "Unwanted &quot;Volumes&quot;"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by rlj999 on 2008-03-09
Trying to delete what appear to be duplicate "volumes" listed under "computer"  -- they probably  appeared as I had to reload linux due to a windows problem --running a dual OS  --XP and Linux 

Robert  -rlj999

Thanks

---

### Post by jken146 on 2008-03-09
Please open up a terminal and post the outputs of the following commands.

```
sudo fdisk -l

cat /etc/fstab

mount
```

---

### Post by rlj999 on 2008-03-09
Here is the info requested

Thanks
Robert  rlj999


obert@robert-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3111    24989076    7  HPFS/NTFS
/dev/sda2            4436        4864     3445942+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3            3112        3735     5012280   83  Linux
/dev/sda4            3736        4435     5622750    5  Extended
/dev/sda5            4374        4435      497983+  82  Linux swap / Solaris
/dev/sda6   *        3736        4338     4843534+  83  Linux
/dev/sda7            4339        4373      281106   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/sdc: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       22179   178152786    b  W95 FAT32
/dev/sdc2   *       22180       43592   171999922+  83  Linux
/dev/sdc3           43593       43777     1486012+   5  Extended
/dev/sdc5           43593       43777     1485981   82  Linux swap / Solaris

Disk /dev/sdd: 82.3 GB, 82348278272 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9334    74975323+   b  W95 FAT32
/dev/sdd2   *        9335        9975     5148832+  83  Linux
/dev/sdd3            9976       10011      289170    5  Extended
/dev/sdd5            9976       10011      289138+  82  Linux swap / Solaris
robert@robert-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ce4f7438-6e76-4f0a-99d5-b94a0c282cbf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=16bbb2d7-1e92-4676-8fe6-626322f01f44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
robert@robert-laptop:~$ mount
/dev/sdd2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/IOMEGA HDD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdc1 on /media/IOMEGA_HDD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdd1 on /media/IOMEGA_HDD_ type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sda1 on /media/SQ003686 type ntfs (rw,nosuid,nodev,umask=222,utf8)
robert@robert-laptop:~$

---

### Post by jken146 on 2008-03-09
Which partitions have duplicates?

---

### Post by rlj999 on 2008-03-11
Looks like partition 6 and 7 are duplicates of 4 and 5 

1 and 2 appear to be my Win XP  files 

all the rest appear to be Linux 

Thanks Robert  rlj999

---

### Post by vanadium on 2008-03-11
When you reinstalled Linux, you probably have created two additional partitions to install rather than having reused the existing Linux partitions from your first install. Anyway, this would mean that you still had unallocated space on your drive when you did your second install. I would probably just go for a third install, after having cleaned up the drive: I would, from a live CD, remove any partition higher than /dev/sda2, inclusive the extended partition, and then let Ubuntu install using the free space.

---

### Post by rlj999 on 2008-03-14
I had a notion that is what happened -- I think I'll just start from ground zero and clean the drive completely  install both OS systems -- since all is backed up it should not take that long   
also I am not quite sure of the process to remove the duplicated volumes 
Thanks so much

Robert  rlj999

---

