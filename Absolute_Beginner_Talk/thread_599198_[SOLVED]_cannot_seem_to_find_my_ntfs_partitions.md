---
title: "[SOLVED] cannot seem to find my ntfs partitions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-11-01
my ntfs partitions don't show up in gutsy

---

### Post by thesm on 2007-11-01
In a command prompt type 
```
nano /etc/fstab
```
and see if the drive is listed there (or post it here), you can tell by the third column which should say ntfs.  If it's there check the mount point, most likely /media/NAME.  Check if you can see it if you go into the /media folder. 

If it's not listed in fstab you'll have to add it.  See here:  [http://cazatech.wordpress.com/2007/10/03/adding-a-ntfs-partition-to-fstab/](http://cazatech.wordpress.com/2007/10/03/adding-a-ntfs-partition-to-fstab/)

To find out the name fire up **gparted** which shows you the partitions (it needs to be run as root)
```
sudo gparted
```.

Good luck.

---

### Post by sayuki288 on 2007-11-01
is there something i can use to fix my ntfs partitions seems to have error or something with it

---

### Post by Sef on 2007-11-01
> is there something i can use to fix my ntfs partitions seems to have error or something with it

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download").

---

### Post by louieb on 2007-11-01
Do you shutdown windows or hibernate?
[http://ubuntuforums.org/showthread.php?t=586836](http://ubuntuforums.org/showthread.php?t=586836)

If you hibernate Gutsy won't mount your windows partitions.

---

