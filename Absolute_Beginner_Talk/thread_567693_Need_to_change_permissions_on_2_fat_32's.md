---
title: "Need to change permissions on 2 fat 32's"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-10-04
I have two partitions, separate drives (both fat32)  that I recently added but I need to write on them. I can access it but don't have permission to write which is annoying. Here's my fstab: I need to write on hdd1 and more importantly hdb1:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=779576c4-aa0c-4bd4-9a60-28fe6eaf801c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3B3D-1883  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd1
UUID=45D7-23C6  /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd3
UUID=049ec3da-9b1c-4ae9-9ace-e6e2b9e547fc none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /media/hdb1 vfat defaults,auto,users 0 0

---

### Post by Yoooder on 2007-10-04
fat32 doesn't support multiple user permissions, so the trick is when you mount them you have to identify what user owns them.

From the command line you do
> mount /dev/[drive] /mnt/[mountpoint] -o uid=[userid] -t vfat

[userid] corresponds to your numerical user identification number, which should be 1000 if you are using the user configured during Ubuntu installation.  To double check it just open up /etc/passwd and find your username entry--your userid should be the first number (the other is groupid).

you can set this up in your /etc/fstab, I belive the entry should be
> /dev/hdb1 /media/hdb1 vfat defaults,auto,users,uid=[userid] 0 0

If that doesn't work I probably got the syntax wrong, just mount the drive from the command and take a look at /etc/mtab which will show you all currently mounted partitions and their options.  It's format should match /etc/fstab

---

### Post by odiseo77 on 2007-10-04
You could change the 'umask' value to change the permissions of the partitions, I think (the only thing is, it's kind of late here and I'm sleepy, so I don't remember which value you have to put there so the data is writable :) ), but what I do with my data partition is to set/change the uid and gid for my current user (this is, just in case you only have one user on your machine):

```
# /dev/hdd1
UUID=45D7-23C6 /media/hdd1 vfat defaults,utf8,umask=007,uid=your_user_name,gid=your_user_name 0 0
#(...)
/dev/hdb1 /media/hdb1 vfat defaults,utf8,umask=007,auto,uid=your_user_name,gid=your_user_name 0 0
```

But if you have more than one user on your machine, and need both of them to access your data partition, you probably have to change the umask value to something like '000' (not sure about the proper value, though, someone please correct me if I'm wrong :) )

Greetings.

EDIT: Yoooder, you went ahead of me!! ;)

---

### Post by Yellowbelly on 2007-10-05
So this is going to be a problem with my windows right? I'm dual booting and it'd be nice if I could access it from both ubuntu and xp. I keep xp for itunes and games ya know, so I'm mainly just trying to move music around.

---

### Post by odiseo77 on 2007-10-05
No, it wouldn't be a problem with windows at all; by changing the permissions in /etc/fstab, you're basically telling your linux box how to read/mount this partition, so you can do it without problems (when you go back to windows, your fat32 partition will be still fully accessible from there). 
When I talked about the number of users, I was referring to the number of users on your linux installation, so, for example, if you have two users in ubuntu, one named 'user1' and the other named 'user2', and you set the uid and gid values for 'user1', then 'user2' won't be able to fully access this partition. But if you only have one user, you don't have to care about it. :)

---

### Post by philinux on 2007-10-05
Why not just use chown to change the owner to your user. 

This is weird cos my fat32 windows me hard drive has always had rw.

---

### Post by vanadium on 2007-10-05
Use

id

to quickly lookup your user id and group.

---

### Post by Discov3ry on 2007-10-05
Try changing the umask from 007 to 0000. Remount or reboot and test.

---

