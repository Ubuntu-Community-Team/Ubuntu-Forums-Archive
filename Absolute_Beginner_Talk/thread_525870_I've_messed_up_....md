---
title: "I've messed up ..."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-08-14
so actually this is what i did..  I've attached a Hdd which is about 28.8 GB  and i just wanted to get it worked.. and i found i was not able to copy and paste things over there so at the bottom of the Properties of that media i read i don't have right of copying in that Hdd so I went to users and groups and i gave all rights to my user and now i'm not able to see my username over there.. so my username has become Root, I guess,, how do we solve..( including Hdd)

---

### Post by dhani99 on 2007-08-14
bump : anybody knows at least how can i use Hd ?

---

### Post by Rul on 2007-08-14
Can you now write on the hdd disk?

If you can, then you can change the owner and group of that disk to your username and then remove the extra rights to your username

---

### Post by dhani99 on 2007-08-14
no i can't do that..

---

### Post by dhani99 on 2007-08-14
is ubuntu have Restoring Earlier point facility ??

---

### Post by Rul on 2007-08-15
Does groups and users have a predetermined settings? I know in kubuntu there is a button that says predetermined that is in the low left corner of user and group settings but I'm not sure where it is in gnome.

For the disk, do you knowwhat is the format that it has? maybe you have to reformat it to ext3, try using the gnome partitioner to check out.

---

### Post by Inxsible on 2007-08-15
post the output of the following commands

```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by dhani99 on 2007-08-15
Disk /dev/sda: 15.3 GB, 15303075840 bytes
255 heads, 63 sectors/track, 1860 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1776    14265688+  83  Linux
/dev/sda2            1777        1860      674730    5  Extended
/dev/sda5            1777        1860      674698+  82  Linux swap / Solaris

Disk /dev/sdb: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3736    30009388+   5  Extended
/dev/sdb5               1        3736    30009357   83  Linux
-----------------------------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c4dc3759-b2cf-45e9-a304-e9d03f958639 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bce6f62b-bdc7-4cd4-b7e6-09d0a7d367f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Inxsible on 2007-08-15
```
sudo chown -R <your username>:<your group> <path to mount point>
```So assuming your username is dhani

```
sudo chown -R dhani:dhani MOUNT_POINT
```where MOUNT_POINT is the place where you have mounted your sdb5

---

### Post by Inxsible on 2007-08-15
Have you yet mounted the sdb5 ?

if its an external drive, then you should use pmount to mount it. Look at my signature for a link on how to do that.

---

