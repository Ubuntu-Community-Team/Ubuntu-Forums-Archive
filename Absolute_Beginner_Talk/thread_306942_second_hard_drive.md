---
title: "second hard drive"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-25
I recently switched out my second drive on my computer with something bigger.  I added the old one using Aysiu's guide for ext 3 disk.  Now I reformatted my second drive but when I use this guide it no longer works.  Can anyone give me a hand putting in this second drive.  Is it different now than in dapper?

the second drive is hdb1 with only one partition.

Here is my fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=5c474c3f-0ffb-4b09-aa1a-f1b310159251 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1187a89e-b584-4b85-8772-de04a4b6d230 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=8500a994-fddf-43c9-aa26-9b93c297e97c /drive_two ext3 defaults 0 0
# /dev/hda1 -- converted during upgrade to edgy
UUID=3C5857A0585757AA /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /second_drive ext3 defaults 0 0

any help would be great.

---

### Post by H.E. Pennypacker on 2006-11-25
Can you post the guide?

Also, are you familiar with the fact that Edgy uses UUIDs now?  Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=278652](http://www.ubuntuforums.org/showthread.php?t=278652)

---

### Post by gentlemanmasher on 2006-11-25
[http://www.ubuntuforums.org/showthread.php?t=174562&highlight=Mounting+a+2nd+HDD](http://www.ubuntuforums.org/showthread.php?t=174562&highlight=Mounting+a+2nd+HDD)

Not really a guide but it always helped me.  So how do I add this drive now.  I formatted it Ext 3.  I read through the guide you posted, a bit over my head.  Any help getting this drive set up would be great.

---

