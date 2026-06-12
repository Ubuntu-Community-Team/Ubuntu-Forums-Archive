---
title: "New internal drive - almost got it... change owner from root to..."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by bhp666 on 2007-11-28
i have searched the forums and gotten far, but i am hung up on how to get my user the read / write access to the new disk - root is owner - anyone? i have been at it for some time now, and know i am close.

looking to get my user to be owner and / or read /write permissions
here is *cat /etc/fstab*
```
rmessner@ubuntu-dt-tb:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=227d00c8-48b5-46c5-b5bf-d2ec14c01213 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3491deee-5b59-4c94-8e75-1efe9792946e none            swap    sw              0       0
/dev/sdb1       /media/disk     ext3    rw,user         0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

here is*ls -la /media*

```
rmessner@ubuntu-dt-tb:~$ ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2007-11-28 14:34 .
drwxr-xr-x 21 root root 4096 2007-11-28 09:37 ..
lrwxrwxrwx  1 root root    6 2007-09-28 11:52 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-09-28 11:52 cdrom0
drwxr-xr-x  3 root root 4096 2007-11-28 09:04 disk
lrwxrwxrwx  1 root root    7 2007-09-28 11:52 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-09-28 11:52 floppy0
-rw-r--r--  1 root root    0 2007-11-28 14:34 .hal-mtab

```

thanks in advance and let me know what else you need to help guide this total noob

bhp

---

### Post by civic_si on 2007-11-28
Just go into the media directory and use chown

that changes the owner of the file.

usage

chown user:group disk

just replace user and group with your login name.

that will make you the owner of the file.

---

### Post by cmnorton on 2007-11-28
This is an example which you might be able to use, but it its not an exact answer to your question.

This is what I did (as root) to put /home on a larger, second IDE drive. (I am aware that Ubuntu refers to this drive as if it is SCSI.)

As root, did the following:

1) Created directory sdb1 in media.

2) Created this entry in /etc/fstab
/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

3) Created this soft link in /

lrwxrwxrwx 1 root root 16 2007-10-05 10:37 /home -> /media/sdb1/home

Everything under /home has the appropriate ownership and permissions as if /home were located on /dev/sda1.

---

### Post by bhp666 on 2007-11-28
> **civic_si said:**
> Just go into the media directory and use chown

that changes the owner of the file.

usage

chown user:group disk

just replace user and group with your login name.

that will make you the owner of the file.

:KS that did it! thanks very much - i must have already read that somewhere, 'cause it took mere seconds for me, almost as if i knew exactly what you were talking about!!!

rock on

---

