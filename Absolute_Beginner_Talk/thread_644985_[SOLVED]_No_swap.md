---
title: "[SOLVED] No swap"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by rmx on 2007-12-19
Hi.

My laptop couldn't hibernate, and I suspected it was because my swap partition was smaller than total amount of ram (1GB).

So with acronis partition manager I erased the swap partition and created another one bigger.

Now Ubuntu doesn't recognize swap.

Can anyone tell me what to do please?

I'm newbie, please go easy:)

Thanks
RMX




rui@RMX:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035632     523132     512500          0      22792     270440
-/+ buffers/cache:     229900     805732
Swap:            0          0          0






rui@RMX:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc35cc35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15735636    7  HPFS/NTFS
/dev/sda2            1960        7234    42371437+   f  W95 Ext'd (LBA)
/dev/sda5            1960        5100    25230051    b  W95 FAT32
/dev/sda6            5101        5248     1188778+  82  Linux swap / Solaris
/dev/sda7            5776        7234    11719386   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001bc17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1110       11563    83971755    c  W95 FAT32 (LBA)
/dev/sdb2               1        1109     8908011   83  Linux
/dev/sdb3           11564       13523    15743700    5  Extended
/dev/sdb5           11564       13523    15743668+   7  HPFS/NTFS

Partition table entries are not in disk order



rui@RMX:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=50498ba2-1b89-452a-b62c-62c8dce46fd1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=70145EE3145EAC3A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E8A1-F8E5  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=6368-C2D6  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=84da5521-9485-4446-a958-28f57ee75874 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by rsambuca on 2007-12-19
It is possible your UUID changed after you resized it.  Use the command ```
blkid
```to see the UUID of your swap.

---

### Post by rsambuca on 2007-12-19
Whoa, sorry, I just had a better look at your outputs.  I am afraid the old swap (sda8) has been erased from your drive.  The new swap is sda6 for some reason.

---

### Post by thelatinist on 2007-12-19
Which means you need to delete the following lines from fstab:

```
# /dev/sda8
UUID=84da5521-9485-4446-a958-28f57ee75874 none swap sw 0 0
```

and replace them with:

```
# /dev/sda6
/dev/sda6 none swap sw 0 0
```

---

### Post by rsambuca on 2007-12-19
Yeah, that will work.

---

### Post by tech9 on 2007-12-19
you could also use gparted to resize your HD and create the missing swap partition

---

### Post by Cypher on 2007-12-19
And did you run "mkswap" after creating the new swap?

---

### Post by bcrom on 2007-12-19
Some computers just don't hibernate in Ubuntu; the command just doesn't work.  I've had it happen with a few different computers.  I doubt it had anything to do with the swap partition.  If the OS runs out of swap it will annex free space on the disk.

---

### Post by rmx on 2007-12-19
I made a mix of the suggestions and it worked out.

However, I tried the hibernation and it freak out the swap.

I have to run again:
rui@RMX:~$ sudo mkswap /dev/sda6

and after reboot, swap was on.

thanks

---

