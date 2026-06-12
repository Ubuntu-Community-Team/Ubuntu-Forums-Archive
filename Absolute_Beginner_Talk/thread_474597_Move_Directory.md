---
title: "Move Directory ?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by hobo on 2007-06-15
How do I move my /home directory from say hda to hdb and make ubuntu use the new directory from now on?

---

### Post by Kobalt on 2007-06-15
You will have to format your hdb to ext3, copy your /home to the new partition and modify your fstab setting a new line with apropriate disk and partition, plus the mount point. Use [this guide]("http://psychocats.net/ubuntu/separatehome") to have the procedure.

---

### Post by Outrunner on 2007-06-15
You can simply edit /etc/fstab to make /dev/hdb mount to /home instead of /dev/hda. You can post the output of ```
cat /etc/fstab
``` here if you don't know how to do it and me or someone else will edit it for you.

EDIT: Umm, looks like I was too slow!

---

### Post by drs305 on 2007-06-15
Here is a link on how to move the home directory:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Be sure to backup your important data beforehand.

---

### Post by hobo on 2007-06-15
Here is my fstab after adding hdc:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

