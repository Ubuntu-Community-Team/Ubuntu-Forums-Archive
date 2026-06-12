---
title: "Mounting Windows partitions"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-03-21
Hi,

I have edgy on a dual boot system with windows. I would like to mount the windows and another partition on the same drive. I tried following the instructions on "psychocats":

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

All was fine until I get to the bit:

sudo nano /etc/fstab

The result doesn't look like either of the options suggested and doesn't refer to either of the partitions I wish to mount (hda1 and hda2) i.e.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=6344c0e4-a596-4221-9417-e86016f266dd /               ext3    defaults,erro$
# /dev/hda5
UUID=d3179581-3a3e-41d4-b33a-3148e13babe9 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0








                               [ Read 11 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

Can anyone help please?

---

### Post by phiphedog on 2007-03-21
The info mentioned in /etc/fstab are mounts that occur at startup. Unless you have added the partitions you wish to mount in there yourself they will not be in there.

You need to find out the name of the partition you wish to mount and then add the line to the end of the fstab file as per the psychocats page.

For example if your windows partition is called hda1 with a ntfs file system then you'd add this line to the end of your fstab file

/dev/hda1 /media/hda1 ntfs defaults 0 0


Then when you re-boot the windows partition will be mounted in the directory /media/hda1

You will need to make sure that the path /media/hda1 exists already. If not just create it.

---

### Post by phiphedog on 2007-03-21
woops..

---

### Post by OldGrey on 2007-03-23
Sorry I have been slow responding. Anyway worked a treat.

Thanks

OldGrey

---

