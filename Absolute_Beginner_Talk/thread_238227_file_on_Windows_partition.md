---
title: "file on Windows partition"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2006-08-17
Can the files on my Windows partition be accessed from Ubuntu? I know you can in Freespire. You can browse the file system and bring up files on that side. Does Ubuntu have that ability?

Thanks.  DB :D

---

### Post by bulldog on 2006-08-17
Yes you can in Ubuntu :) 

Only read acces no writing is aloud.
You can copy and paste all you want to your Ubuntu.

---

### Post by purebuilt on 2006-08-17
How do you do it? When I try to access the drive it says it can't be mounted.

---

### Post by bulldog on 2006-08-17
I'll go to places or my map Media and select  one of my drives.
This opens the drive for me with no trouble at all.

When this 
will not happen for you,maybe you should take a look at your fstab,and see of you drives are there.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

This is my fstab,you can find your's in /etc/fstab.
Before you make any changes.I should make a copy first.

---

### Post by aysiu on 2006-08-17
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Kobalt on 2006-08-17
If you have a NTFS partition and want to be able to write/delete stuff on it, through Ubuntu, I suggest this easy method : [http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009")

Cheers !

---

