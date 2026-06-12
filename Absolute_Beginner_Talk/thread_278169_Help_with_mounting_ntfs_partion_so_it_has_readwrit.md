---
title: "Help with mounting ntfs partion so it has read/write acess"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Phobiac on 2006-10-15
I have a windows partion (Bolded below) that I've been trying for some time now to get read/write acess on. I've googled, I've read guides, I've tried as hard as I can to find a solution and this is my last resort. At this point I've edited that line of fstab to the point that now I don't even have perimission to see the files. Someone please help? ](*,) 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda1       /media/hda1     ntfs    user,rw        0       0**
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
```

---

### Post by givré on 2006-10-16
here [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
is the solution for you.

---

