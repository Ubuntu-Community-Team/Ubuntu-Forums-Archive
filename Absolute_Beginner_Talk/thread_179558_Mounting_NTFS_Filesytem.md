---
title: "Mounting NTFS Filesytem"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-20
Hi,

Linux mounts the NTFS drive okay(i think), but when I try to open it I receive an error message:
> Folder cannot be displayed, you do not have the permissions to view such a file or 
folder.
In the file browser the icon has a little  red and white cross on it.

I have tried remounting it using the guide at: 

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

The Fstab file looked like this:
> /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/Drive1   ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
o     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I changed the "/dev/hda1" line to:
> 
/dev/hda1       /windrvs/c      ntfs    nls=utf8,unmask=0222        0       0

the mount folder "/windrvs/c" is already been created and I have unmounted
my windows drive - hda1.

When I *sudo mount -a* i get the following error:

> [mntent]: line 1 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What do I need to do to get Linux to not just mount but be 
able to read the NTFS HDD.

You guys have already been a great help to me, thank you very much!

---

### Post by jorn on 2006-05-20
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
umask instead of unmask
Sometimes it's better to copy and pate, but I do't know if it solves your problem.

---

### Post by Ecthelion on 2006-05-20
> I changed the "/dev/hda1" line to:
Quote:
/dev/hda1 /windrvs/c ntfs nls=utf8,unmask=0222 0 0

the mount folder "/windrvs/c" is already been created and I have unmounted

Could it be that you have this error because you want to mount your partition as /windrvs/c instead of mounting it in **/media**/windrvs/c ?
I don't know if you can mount your partition in /

Hope it helps

---

### Post by mostwanted on 2006-05-20
jorn is right. umask is what sets permissions for file systems without native UNIX permissions support (the 0222 part means read-only permissions).

Ecthelion: you can mount partitions anywhere in the file system.

---

### Post by RudolfMDLT on 2006-05-20
Thanks Guys! Sorry for making you find my typo! umask VS uNmask.

Thanks!

---

