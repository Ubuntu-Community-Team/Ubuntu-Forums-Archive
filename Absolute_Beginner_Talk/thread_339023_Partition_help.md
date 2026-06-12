---
title: "Partition help"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2007-01-15
I have a server running Ubuntu 6.06LTS, its a webserver running ISPConfig.

here is the output of 'fdisk -l'
```
Disk /dev/hda: 36.5 GB, 36529274880 bytes
255 heads, 63 sectors/track, 4441 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        4255    24410767+  83  Linux
/dev/hda3            4256        4441     1494045   82  Linux swap / Solaris

```

and here is the output of my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda2       /home           ext3    defaults,usrquota,grpquota        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I just realized that **/var/www** is where all of the web stuff is stored. I would like to resize my /home partion and create a new 10Gb partition for /var/www.

the problem is I do all administration from the command line via ssh. I am assuming I need to use the fdisk command to accomplish this. I have searched and haven't found any how to's or info that would aid me. can someone please help? thanks in advance.

---

### Post by bodhi.zazen on 2007-01-15
I could be wrong, but I do not think you can resize partitions with fdisk or cfdisk, or even from the CLI.

Also you can not resize partitions that are currently mounted.

My advice (although I know this is not what you are asking) is to boot to a live CD (Gparted) and do your partitioning (I do not think you can do this task via ssh). Don't forget to edit fstab :p

---

### Post by Aberrix on 2007-01-15
alright, I just need to be able to resize from the CLI.

---

### Post by bodhi.zazen on 2007-01-15
Try parted:

[http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25)

---

### Post by Aberrix on 2007-01-15
meh, I think I am just going to move the 'www' dir to the /home partition. that should be good enough...

---

