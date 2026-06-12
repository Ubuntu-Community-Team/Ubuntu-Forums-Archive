---
title: "/dev/scd0 does not exist error"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by villindesign on 2008-02-10
For some reason, my CD-Rom no longer auto mounts. So, I thought I would mount it my self. I looked at /etc/fstab and saw:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=192c7424-d1cf-42ef-9fe0-d871d6614660 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3438B9C738B987FE /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=91612ca0-e323-40ff-8ab6-e54f1d5056c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```So, I typed ```
sudo mount /dev/scd0 /media/cdrom0/
``` and I get the error ```
mount: special device /dev/scd0 does not exist

```Any ideas on how to mount my drive? Thanks

---

### Post by Foxmike on 2008-02-11
It looks like a typo... scd1 instead of sdc1... cant you try the following:
 
```
ls /dev/s[a-z][0-9][0-9]
``` and post back the following?

---

### Post by villindesign on 2008-02-11
Thanks. When I try the code you suggested, I get:
```
britt@britt-laptop:~$ ls /dev/s[a-z][0-9][0-9]
ls: /dev/s[a-z][0-9][0-9]: No such file or directory

```
I also tried pressing tab after /dev/s to see what was there:
```
britt@britt-laptop:~$ sudo mount /dev/s
sda         sda3        sg0         snd/        stdin       
sda1        sequencer   shm/        sndstat     stdout      
sda2        sequencer2  snapshot    stderr  
```Any more ideas? Thanks

---

