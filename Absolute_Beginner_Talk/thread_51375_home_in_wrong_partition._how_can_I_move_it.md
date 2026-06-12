---
title: "/home in wrong partition. how can I move it?"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by xwang on 2005-07-23
Hi,
I have my /home directory in the wrong partition as you can see from my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext2    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hda2	/windows/D	vfat	umask=000	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

as hda7 is a very small partitio (100MB9 in which, before I installed Ubuntu, I had only Suse boot manager.
I would like to move the /home directory in hda6.
How can I do?
Xwang

---

### Post by Xian on 2005-07-23
Rename your current home folder (i.e., home_old).
Then create an empty folder named home in the '/' path.

Copy or move the contents of /home_old to /home.

Edit your /etc/fstab file and remove the line that contains hda7.
Reboot.

---

### Post by xwang on 2005-07-23
[QUOTE=Xian]Rename your current home folder (i.e., home_old).
Then create an empty folder named home in the '/' path.

Copy or move the contents of /home_old to /home.

Edit your /etc/fstab file and remove the line that contains hda7.
Reboot.[/QUOTE]

Thank you very much.
Can I resize my hda6 in order to use the free space of the hda7 partition?
Xwang

---

### Post by Xian on 2005-07-23
I make it a practice not to resize existing Linux partitions containing a working install, but if you do so just be sure to back everything up on that hda6 since any partitioning does involve some risk to the file system.

---

### Post by chgokt7raid on 2005-07-23
Can partitions be resized without losing any information?

---

