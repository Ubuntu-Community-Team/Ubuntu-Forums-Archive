---
title: "some prob.. read only !"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by robin_1323 on 2006-09-09
I did not made access to my drives during installation ... they r read only now .. I followed the procedure given here [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Chk this:

robin@robin-desktop:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551        9446    55392120    f  W95 Ext'd (LBA)
/dev/hdc3            9447        9484      305235   82  Linux swap / Solaris
/dev/hdc4            9485        9733     2000092+  83  Linux
/dev/hdc5            2551        5100    20482843+   7  HPFS/NTFS
/dev/hdc6            5101        7650    20482843+   7  HPFS/NTFS
/dev/hdc7            7651        9446    14426338+  83  Linux
/dev/hdc8            7651        7651           0+  83  Linux

and also the fstab .. file .. I edited .. but dont know wht I did .. 

[IMG]http://img168.imageshack.us/img168/4062/screenshot1od7.png[/IMG]

I also wnt access to my other drives .. as they r also read only.. I cant write anything to it ...Also in file system folder... I also dont have access ... it says I m not the owner.. 

See also .. I edited hdc1 which is my windows xp ntfs.. also I m not sure if I did editing correct .. now also I m not able to mount it now .. 

robin@robin-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

robin@robin-desktop:~$ sudo mount /dev/hdc1
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**Hey I m totally new to ubuntu ! :( **

---

### Post by jorn on 2006-09-09
Your fstab for ntfs must look like this:
> dev/hdc1  /windows   ntfs   nls=utf8,umask=0222   0   0
if hdc2 is fat then:
> dev/hdc2   /win98   vfat   iocharset=utf8,umask=000   0   0
Then make directory:
> sudo mkdir /win98
I assume you have made the directory for: /windows
Reboot and se if the the directories are present in nautilus.
In order to gain access type or paste in terminal:
> gksudo nautilus
You are now root: Be careful.
Browse to the directories example : /win98
Rightclick > Properties>Permissions
Make your changes. And close.
Post if it does't work.

---

