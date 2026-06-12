---
title: "Dual or Triple booters:  Pls help with mounting HFSPLUS"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by rscow on 2006-09-22
Hi, all.  I'm looking for some help mounting my OS X partition.  I have the Windows partition up, but haven't had much luck with the OS X, which is dev/sda2.  I have made a mountpoint at /media/CamelToe_3, and linked the /media mount point to the filesystem at /dev/sda2.

Here is my /etc/fstab

roger@macbook:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/swapfile       swap            swap    defaults        0       0
/dev/sda4       /media/windows  vfat    iocharset=utf8,umask=000        0      0
/dev/sda2       /media/CamelToe_3       hfsplus user,auto,file_umask=0177,dir_um ask=0077,uid=1000       0       0

But I can't get it to mount properly with mount -t, or open when it does. 

If I cd to /media/CamelToe_3, then, all the mac directories are there.

Maybe one of you could cat /etc/fstab on your machine and I can see what I have wrong.  Journalling is off on the mac side.

Roger

---

### Post by rscow on 2006-09-23
Well, I used very unscientific means, searched the web, and found most of the hits here, of course.  But I just changed my /etc/fstab and rebooted, and my OSX partition mounted. Permissions are correct.  Here is the line from my fstab:

/dev/sda2       /media/CamelToe_3       hfsplus rw,exec,auto,users      0      0

Hope this may help someone else.

---

