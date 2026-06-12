---
title: "accessing Windows files"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2006-09-03
I am trying out Breezy Badger.

If I go through Disks Manager, I can see the files on my C:\ drive which is NTFS and has access path of  /media/hda1.

But if I double-click on the [COLOR="Blue"]hda1[/COLOR] icon on the Ubuntu desktop, I get the error message that *folder contents cannot be displayed*.

Why the difference?

I want to be able to just double-click on the [COLOR="Blue"]hda1[/COLOR] icon to view the contents.

---

### Post by orb9220 on 2006-09-03
Post your fstab here with a terminal command of:
gedit /etc/fstab
Copy and paste here so we can see what is going on.

---

### Post by aysiu on 2006-09-03
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ieee488 on 2006-09-04
here's my  /etc/fstab   file

I have 2 hard drives. C:\ which is all Windows 2000
D:\  which has Windows 2000, OpenSUSE 10.1, and Ubuntu

I also do see an error during boot into Ubuntu.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1  /media/hda1  ntfs nls=utf,umask=0222  0  0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdb6       /media/hdb6     ext3    defaults        0       2
/dev/hdb7       /media/hdb7     ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ieee488 on 2006-09-04
It turns out that the NTFS partitions were mounted, but I did not have permissions to read the contents.

So, I needed
/dev/hda1 /media/hda1 ntfs defaults[COLOR="SeaGreen"],nls=utf,umask=0222[/COLOR] 0 0
/dev/hda1 /media/hdb1 ntfs defaults[COLOR="SeaGreen"],nls=utf,umask=0222[/COLOR] 0 0

I have Ubuntu 5.10 Breezy Badger.

---

