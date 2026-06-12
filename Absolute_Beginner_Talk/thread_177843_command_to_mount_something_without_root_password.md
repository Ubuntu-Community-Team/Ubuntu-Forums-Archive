---
title: "command to mount something without root password"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2006-05-17
dear all
how I mount some network folder / fat without giving root password

I have seen this command before from this forum but can not find it again.

sudo chmod ..... 

but I forgot it.

thank all for help

---

### Post by Sutekh on 2006-05-17
Generally to mount a FAT partition requires the use of sudo and password
```
sudo mount /dev/hda1 /mount_folder -t vfat -o iocharset=utf8,umask=000
``` the only way you can mount a partition without the need for sudo and password is to alter the /etc/fstab and add the option **user** to the partition entry, much like CDROM and floppy entries
```
/dev/cdrom   /media/cdrom   auto   ro,noauto,**user**,exec   0 0 
/dev/hda1    /mount_folder  vfat   iocharset=utf8,umask=000,**user   **0   0
``` 
If you are talking about allowing access to the partition without the need for sudo and password then you should read these links for information on mounting FAT partitions with non-root access.

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

[Ubuntu Wiki - Mounting Windows Partitions]("https://wiki.ubuntu.com/MountingWindowsPartitions")


Don't try to sudo chmod anything. FAT partitions are incapable of supporting the ownership and permission characteristics of Linux partitions.

---

