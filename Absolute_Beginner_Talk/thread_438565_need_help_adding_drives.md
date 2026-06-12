---
title: "need help adding drives"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by sgg on 2007-05-09
Learning linux as I go, so speak slowly please.

I just setup a JBOD array with port multiplier and my ubuntu server 6.06 sees all the drives.

I've partitioned the drives with gparted. However, I can't seem to access the drives from the
desktop, or I just don't know where to look. 
I can't seem to find them via command line either.

Do I need to change their permissions?
Do I need to edit fstab? what is the correct format for an entry into fstab?

Also, how can I give these drives a better name than "sdg1" and have them appear in 
a location of my choice?


Thanks in advance

---

### Post by Martin on 2007-05-09
I think you're halfway there. Yes you should edit fstab. the format for each entry is quite well explained in any number of howtos or try "man mount" in a terminal and you will get the options. In order to refer to the device as something other than /dev/sdg1 or whatever - create a directory in /media/ called 'drive_1' or 'music' or something, this will be the mount point for the drive (like an alias). The mount command will explain it in more detail but basically you mount a device  to a mount point. So your sdg1 becomes /media/music which you can then point to from a shortcut on the desktop or wherever. Hope this helps

---

### Post by alienexplorers on 2007-05-09
I don't know if this will be of help, but it shows how to mount different file systems.

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by sgg on 2007-05-09
thanks for the help.

I've followed all the instructions and have sucessfully mounted
my drives where I want them, with better names (sort of).

However, when i open the folder corresponding to a drive and attempt
to copy to it, I'm told that I don't have permission.

should I also chmod the folders within /media/?

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#/dev/sdg1
UUID=177c02de-390b-48af-b149-3806bae454c1       /media/apollo1  ext3    rw,user 0       1

#/dev/sdf1
UUID=6803dba8-d268-4952-8c57-09d87a77f35f       /media/apollo2  ext3    rw,user 0       1

#/dev/sde1
UUID=cec32e5a-dcc1-4cd9-8cf5-b40c9984856d       /media/apollo3  ext3    rw,user 0       1

#/dev/sdd1
UUID=715cfab1-91b1-4f55-b59b-4801894dc539       /media/apollo4  ext3    rw,user 0       1

```

---

### Post by sgg on 2007-05-10
Ok I've sorted out the permissions issue. I need to set  the drives to my user via chown command, then chmod
them correctly.  They were set to root:root.

Next issue is that these drives appear in gparted as 698.64 GB each and in the desktop file browser, the mounts indicate that they are only 63.7 GB . What is happening there?

---

