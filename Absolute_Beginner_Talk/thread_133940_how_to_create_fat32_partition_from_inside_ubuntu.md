---
title: "how to create fat32 partition from inside ubuntu"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by ninjasmith on 2006-02-21
Hi there pretty noob at linux

my pc currently successfully triple boots into windoze home and pro and linux.

there are two additional ntfs partitions my hard drive partitioningin could be described as

hard disk 111.76gig  partition1 /dev/sda1 NTFS - this is mounted in linux and has most of my data
harddisk  111.76gig  partition1 /dev/sdb1 NTFS - windoze home
                            partition3 /dev/sdb3 extended 3 - ubuntu install dir
                            swap partition /dev/sdb6
                            partition5 /dev/sdb5 NTFS - windoze pro
                            *swap partition /dev/sdb7 file system 'memory swap' size 60gig!!!!*

so the problem is that I have a 60 gig ntfs partition that I want to turn in fat32 but ubuntu seems to think that it is a memeory swap partition?

how do i turn is into fat32 (I dont mind formatting) and then hopfullly have it detectable by windoze too.

---

### Post by Herman on 2006-02-21
> so the problem is that I have a 60 gig ntfs partition that I want to turn in fat32 but ubuntu seems to think that it is a memeory swap partition?Please enter the following code and paste the results back on your next post.```
sudo fdisk -l
```Also, please do this code as well and paste the results of that back on your next post as well.```
sudo gedit /etc/fstab
```Also, what brand of partitioning software do you use?

---

### Post by patrick295767 on 2006-02-21
```
cfdisk /dev/hda
```
Powerful and easy.

A great one that is working all the time !
(make a Win95 (LBA))

Greetz

---

### Post by ninjasmith on 2006-02-22
[QUOTE=Herman]Please enter the following code and paste the results back on your next post.```
sudo fdisk -l
```Also, please do this code as well and paste the results of that back on your next post as well.```
sudo gedit /etc/fstab
```Also, what brand of partitioning software do you use?[/QUOTE]

```
sudo fdisk -l
``` gives

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14588   117178078+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            3769       14588    86911650    f  W95 Ext'd (LBA)
/dev/sdb3   *        2551        3768     9783585   83  Linux
/dev/sdb5            3826        6375    20482843+   7  HPFS/NTFS
/dev/sdb6            3769        3825      457789+  82  Linux swap / Solaris
/dev/sdb7            6376       14588    65970891    7  HPFS/NTFS

Partition table entries are not in disk order


so the bit I want to make fat is the last partition

```
sudo gedit /etc/fstab
``` gives

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

which shows the drive I have mounted I think.  does this mean i need to mount the second NTFS partition and then convert it or reduce it in size?

---

### Post by ninjasmith on 2006-02-22
[QUOTE=patrick295767]```
cfdisk /dev/hda
```
Powerful and easy.

A great one that is working all the time !
(make a Win95 (LBA))

Greetz[/QUOTE]


this just gives me a black screen and the following

 FATAL ERROR: Cannot open disk drive
                          Press any key to exit cfdisk

:confused:

---

### Post by yota on 2006-02-22
Cfdisk needs superuser privileges, try (with care since you will be editing your partition table):

```

sudo cfdisk /dev/hda

```

---

### Post by frodon on 2006-02-22
To do it in command line : ```
sudo fdisk /dev/the_name_of_the_partition
```Then follow the process and use the help.
To do it with a GUI : ```
sudo apt-get install gparted
```And then run gparted.

---

### Post by Herman on 2006-02-22
>     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            3769       14588    86911650    f  W95 Ext'd (LBA)
/dev/sdb3   *        2551        3768     9783585   83  Linux
/dev/sdb5            3826        6375    20482843+   7  HPFS/NTFS
/dev/sdb6            3769        3825      457789+  82  Linux swap / Solaris
/dev/sdb7            6376       14588    65970891    7  HPFS/NTFS >  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0 You should do sudo gedit /etc/fstab again and: (see how sudo fdisk -l says your swap area is called /dev/hdb6?),...well if you change that in /etc/fstab to be the same number for the swap area by deleting where it has the number 7 and replacing it with the number 6 (/dev/sdb6), and be sure to click 'save' before closing the text editor, your computer will work a lot bit better. You might need to restart it afterwards.

Then you can do your work with GParted or whatever partitioner you like, and format your sdb7 from NTFS to FAT32.

To make a new folder to mount your sdb7 fat32 partition:```
sudo mkdir /media/windows
``` You can add a line in /etc/fstab to automatically mount your new fat 32 partition too:```
/dev/sdb7 /media/windows vfat iocharset=utf8,umask=000 0 0
```  :-D (Herman)

---

### Post by xyz on 2006-04-18
Hi-
I think I did the right thing here but it doesn't work somehow.If someone had a little free time to help this n00b here, I'd be most grateful.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1 
/dev/hda1       /media/hda1  ntfs nls=utf8,umask=0222 0 0    
/dev/hda5       /media/hda5  ntfs nls=utf8,umask=0222 0 0   
/dev/hda6       none            swap    sw 0 0             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Why does it say this when I run:
> th@meander:~$ sudo fdisk /dev/sda5

The number of cylinders for this disk is set to 9731.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):


I want to convert /dev/sda5 to FAT32:
> th@meander:~$ fdisk -l

Disk /dev/sda: 80.0 GB, 80060423680 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        9733    78172290    f  W95 Ext'd (LBA)
/dev/sda5               2        9733    78172258+   7  HPFS/NTFS


Why doesn't it show in:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1 
/dev/hda1       /media/hda1  ntfs nls=utf8,umask=0222 0 0    
/dev/hda5       /media/hda5  ntfs nls=utf8,umask=0222 0 0   
/dev/hda6       none            swap    sw 0 0             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

What am I doing wrong? Thanks in adv.
PS: this is a usb external hd.

---

