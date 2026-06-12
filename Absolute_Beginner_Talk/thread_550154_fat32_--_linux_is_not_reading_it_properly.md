---
title: "fat32 -- linux is not reading it properly"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-09-13
hello to all that read this

i recently converted one of my ntfs partitions to fat32 using partition magic in windows. windows tells me i have 54 GB of space and it is fat32. so i transfered about 40 GB of stuff to it. however, when i rebooted into kubuntu, the stuff isnt there and also, it tells me i have 36 GB capacity and only 21 GB available. anyone want to take a stab at my problem?

---

### Post by Nulifier on 2007-09-13
I am going to assume that your Linux is not mounting your new fat32 partition
So first things first, type:

sudo fdisk -l

this will show all the disks attached to your computer
find the disk that you want the line will look somthing like this:

/dev/sda2   *           7       11154    89546310    7  HPFS/NTFS

(It will be different but this is my windows partition)
 the part of this that you want is the begining /dev/sda2 (again this is only on my system you will have to find out yours) this is linux's reference to this HD

now type:

mount

if you see this drive there then it is mounting it
What I think is happening is that it is mounting it with ntfs file system when it is actually fat32 

you can try to mount it by reading [this]("http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/")

so good luck and I hope you can access it

---

### Post by Miroku on 2007-09-13
fdisk -l gives me this:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8172    65641558+   7  HPFS/NTFS
/dev/sda2            8173       13157    40042012+  83  Linux
/dev/sda3           13158       14593    11534670    f  W95 Ext'd (LBA)
/dev/sda5           13376       14593     9783553+   b  W95 FAT32
/dev/sda6           13158       13375     1751022   82  Linux swap / Solaris

Partition table entries are not in disk order


Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8288    66573328+   7  HPFS/NTFS
/dev/sdb2            8289       24792   132568380    f  W95 Ext'd (LBA)
/dev/sdb5            8289       17697    75577761    7  HPFS/NTFS
/dev/sdb6           17698       24792    56990556    b  W95 FAT32
```

mount gives me this:

```
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb5 on /media/sdb5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda5 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

the data is suppose to be on sdb6




also, in 'storage media' -- the other partitions have a HDD icon, but sdb6 has a folder icon, if that makes any difference

---

### Post by Miroku on 2007-09-13
well i followed the link you said, it did mount it, and the data is there

now my question is, how do i make it so its permanent and behaves just like my other partitions? or is it permanent already?

TIA

---

### Post by splintercellguy on 2007-09-13
It would appear that the FAT32 partition is already in /etc/fstab, so you should be good.

---

### Post by Miroku on 2007-09-23
unfortunately, i need to mount it everytime i restart the computer. anyway to make it stay permanent?

TIA

---

