---
title: "Mount problems!"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by 25an on 2006-10-08
Hi!

I have just installed Dapper and I have a partition that i liked to mount to my home dir. So i edited the /etc/fstab and everything workt. The problem appered when i tryied to write a file to it. So I looked at the ownership and i got following

drwx------ 2 mans mans  4096 2006-10-08 11:00 Desktop
drwxr-xr-x 3 mans mans  4096 2006-10-08 12:40 memz
drwxr-xr-x 9 root root 16384 2006-10-08 11:49 Share
drwxr-xr-x 2 mans mans  4096 2006-10-08 12:39 torrent

The dir Share is the one i mounted when i try to change the rights on. I used the command 
 
sudo chmod a+rw Share/

to change the rights but nothing?
My /etc/fstab is

> # /etc/fstab: static file system information.
#
# <file system> <mount point>     <type>  <options>       <dump>  <pass>
proc            /proc             proc    defaults        0       0
/dev/hda8       /                 ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot             ext3    defaults        0       2
/dev/hda7       /home             ext3    defaults        0       2
/dev/hda1       /media/hda1       ntfs    defaults        0       0
/dev/hda3       /home/mans/Share  vfat    auto,user,exec,rw,sync        0       0
/dev/hda9       /usr              ext3    defaults        0       2
/dev/hda5       none              swap    sw              0       0
/dev/hdc        /media/cdrom0     udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0    auto    rw,user,noauto  0       0

What can I do?

---

### Post by mitch.c on 2006-10-08
> **25an said:**
> Hi!

I have just installed Dapper and I have a partition that i liked to mount to my home dir. So i edited the /etc/fstab and everything workt. The problem appered when i tryied to write a file to it. So I looked at the ownership and i got following

drwx------ 2 mans mans  4096 2006-10-08 11:00 Desktop
drwxr-xr-x 3 mans mans  4096 2006-10-08 12:40 memz
drwxr-xr-x 9 root root 16384 2006-10-08 11:49 Share
drwxr-xr-x 2 mans mans  4096 2006-10-08 12:39 torrent

The dir Share is the one i mounted when i try to change the rights on. I used the command 
 
sudo chmod a+rw Share/

to change the rights but nothing?
My /etc/fstab is



What can I do?

You can't chmod a vfat volume. You need to do it all in fstab.

You may want to try something along these lines:
```
# /etc/fstab
# change /dev/device appropriately; change gid to match group ID
/dev/device   /home/mans/Share   vfat    defaults,utf8,umask=000,gid=100 0  1
```
umask=000 sets permissions to 777
Set gid= to a group that your users belong to. I use 100 which is my "users" group (I can't remember if user accounts are already members, or if I had to add them), and made sure all user accounts are members.

EDIT: If you use umask=000, you may not need to set the gid. On my vfat parition I use, umask=002,gid=100 so that the owner and group have rwx permission, and others have rx only.

"man mount", and search for msdos and vfat for more mount options.

---

