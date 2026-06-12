---
title: "Adding ext3 partitions to the computer after conversion from ntfs"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-07-28
I'm trying to migrate my ntfs partitions to ext3.  I've formated the hdb5 partition as ext3 and now want to add it.  I've changed my /etc/fstab to this:
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-3g    silent,umask=0,locale=en_US.utf8    0    0
/dev/hdb5       /media/hdb5	ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /media/hdb6     ntfs-3g    silent,umask=0,locale=en_US.utf8    0    0
/dev/hdb7       /media/hdb7     ntfs-3g    silent,umask=0,locale=en_US.utf8    0    0
/dev/hdd1       /media/hdd1	vfat defaults,utf8,umask=000 0 0
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I keep on logging in and a box in the lower right hand corner says I've used 97% of the disk space.  Opening up the G-drive in Nautilus just shows the Lost+Found folder.  

What am I doing wrong?

---

