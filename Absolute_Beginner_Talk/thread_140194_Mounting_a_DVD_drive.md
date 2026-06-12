---
title: "Mounting a DVD drive"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-03-05
I am trying to mount a DVD drive and am not having any luck.  My fstab looks like the following:
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/DVDRW_Drive   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/mnt/Disk_60GB vfat iocharset=utf8,umask=000   0   0
/dev/hdc1	/mnt/Disk_10GB vfat iocharset=utf8,umask=000 0   0
/dev/sda1	/home/calvarymanagua/180GB_Drive_USB vfat iocharset=utf8,umask=000 0 0

However, I put in a CD with only JPEGS on it (it was burned using Windows XP) and when I click on the directory for the CD Rom - it says unable to mount (The volume is probably in a format that is unable to be mounted)?  I really don't know what that means and don't know how to fix it.

My ultimate goal is to install DVD shrink and copy some DVD's, but I want to make sure the drive is working first.

Thanks
Brian

---

### Post by patrick295767 on 2006-03-05
As I heard dvd shrink is rather slow... 
  
I can read DVD via my fstab:
  
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
10.1.1.1:/mnt/home	/home	nfs	rsize=8192,wsize=8192,timeo=14,intr


```
  
I think it would work similar for ur case ... 

Greetz, 

I hope u'll make it ... 

Pat'

---

### Post by B7may on 2006-03-05
I found the problem.  I needed to change the jumber on the CD rom drive to Cable select.  I have noticed that I have to do this on all of the extra drives that I have installed.  I am not sure why, but it fixes the problem.

---

### Post by patrick295767 on 2006-03-07
[QUOTE=B7may]I found the problem.  I needed to change the jumber on the CD rom drive to Cable select.  I have noticed that I have to do this on all of the extra drives that I have installed.  I am not sure why, but it fixes the problem.[/QUOTE]

 Good ! Thread Solved 

Greezt

---

