---
title: "[SOLVED] partition not mounting properly"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Samrat Rao on 2008-03-14
i have both ubuntu 7.10 and windows xp in my desktop. from windows OS i reformatted one partition to ntfs filesystem and renamed it. subsequently the mount point has changed from /media/sda5 to /media/new_partition_name. every time i use ubuntu i need to mount the partition. 
also in /media/ using command 'ls' lists both sda5 and new_partition_name. how do i make it mount during the startup itself?

---

### Post by jan quark on 2008-03-14
you have to edit the fstab file

please post the result of

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by alphaniner on 2008-03-14
You will have to modify your /etc/fstab file.  Do some searching, there are plenty of tutorials around the forums and the web.

---

### Post by bumanie on 2008-03-14
try this site is among the simplest to understand re editing fstab
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Samrat Rao on 2008-03-14
the command 'sudo fdisk -l' is not working since i get the message 'command not found' but 'cat /etc/fstab' works and here is the result:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=b27edbdc-2ef0-4514-badf-8fb20c754b7d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4456-5E6F  /media/sda1     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=00AE-3E3D  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=0C05-0BDD  /media/sda6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=17457bb2-df5c-4a1a-b585-7d27793436eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

and i will try to understand the tutorial provided in the link. thanks.
i may be a bit late in following up since i do not have net connection for my PC.

---

