---
title: "mount point 0 does not exist"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-12-25
I'm having problems mounting my second hard drive. When I do "sudo mount -a" I get an error that says: 

mount: mount point vfat does not exist
mount: mount point 0 does not exist

Here is my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda4
UUID=23033200-c949-4052-97c3-c754437477e4 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda2
UUID=216af082-157c-439e-a486-e9d41e35dc20 /boot           ext3    defaults        0       2

# /dev/sda1
UUID=6C14DF2614DEF256 	/windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/sdb1    
/archive  vfat   user,rw,exec 0 0

# /dev/sda3
UUID=cd805a02-33d0-44ce-aee5-68f39c0c57bd none            swap    sw   
           0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/           /media/floppy0  auto    rw,user,noauto  0       0


When I check fdisk -l it tells me:


Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        6770     1951897+  83  Linux
/dev/sda3            6771        7378     4883760   82  Linux swap / Solaris
/dev/sda4            7379       20023   101570962+  83  Linux

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+   b  W95 FAT32


I'd like to be able to write to sdb1. I appreciate the help.

---

### Post by dbbolton on 2006-12-25
which one are you trying to mount ?

---

### Post by beamo on 2006-12-25
I would like to mount this one:

/dev/sdb1 1 13054 104856223+ b W95 FAT32

---

### Post by Regel on 2006-12-25
```
sudo mkdir /media/hdd
sudo mount /dev/sdb1 /media/hdd -t vfat -o iocharset=utf8,umask=000

```

To unmount
```
sudo umount /media/hdd
```

In order to mount on boot-up this line needs to be in fstab:
```
/dev/sdb1    /media/hdd vfat  iocharset=utf8,umask=000  0    0
```

---

### Post by beamo on 2006-12-25
Thanks, Regel, worked like a charm.

Now my problem is that I can't rip my cd's to this location. I get the error message:

Sound Juicer could not extract this CD.
Reason: Invalid parameters

the mount point is /media/disk2 and I am able to browse the directory just fine. How do I write to it?

Another question is what's the best way to do this so that I can write to the same partition on my second hard drive from both Windows and Ubuntu? Is NTFS a better choice than Fat32? I've read that it is possible to write to NTFS from Ubuntu. I want to have a 100gb partition on my second disk to archive my cd collection and I'd like to be able to rip them from either Windows or Ubuntu and have them playable from both. I installed audiograbber on Windows because the media player's format is unplayable on Ubuntu as far as I know. Any suggestions are greatly appreciated.

Thanks for all the  help :-D

---

### Post by Regel on 2006-12-25
Well, Linux's ntfs-3g-driver is still a beta, you shouldn't use it. So you could make it a FAT32 partition, or you could make it an ext2(or 3) one and install necessarily drivers for windows.

---

### Post by beamo on 2006-12-25
Thanks again, Regel. I made the partition ext2 and installed the drivers for Windows. Wasn't able to write to it until I did "sudo chown tim /media/disk2" but now everything is wonderful. I would have done it in ext3 but it looks like the drivers for Windows can only read from ext3 and not write to it. 

I'm very happy ;)

---

### Post by Kavster on 2008-05-29
Hi, I have a similar problem as the first one. I am trying to mount my XP HDD and am having trouble. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8af4781f-a0ca-4f92-b1f8-8d221f7474fa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ef1983aa-346f-4037-8f34-01dc70b573ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any help is appreciated.

PS. Please assume very little knowledge of Linux! :(

---

### Post by k@e on 2008-05-29
Please post the output of
```
sudo fdisk -l
```

---

### Post by Kavster on 2008-05-29
Here it is:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffff6a42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

---

