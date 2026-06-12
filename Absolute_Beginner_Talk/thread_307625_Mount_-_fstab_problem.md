---
title: "Mount - fstab problem"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-11-26
I am running Dapper 6.06 and have an external hard drive with four partitions. I also have a flash stick removable drive 128megs.
I also have two internal hard disks with four partitions on each.
I am having problems mounting the external drives. When I insert the flash stick it assumes the dev allocated to the first partition of the external hard drive. Please find my Fstab file hereunder. Can someone please advise where I am going wrong. The kingston is the flash stick. I am also getting permission problems with the external and the flash stick. The internal partitions have mounted no problems and show all data. Any advice appreciated.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda1       /mnt/WinXP ntfs nls=utf8,umask=0222 0 0
/dev/sda5       /mnt/Windows_Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /mnt/Win_Multimedia     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       /mnt/Win_Research     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb8       /   ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       /mnt/SpareDrive   vfat iocharset=utf8,umask=000 0 0
/dev/sdb6       /mnt/WinSpare     vfat   iocharset=utf8,umask=000 0 0
/dev/sdb7       /mnt/Music_Files ntfs nls=utf8,umask=0222 0 0 
/dev/fd0 	/media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto 0 0

/dev/sdc1       /media/ExtPart1   vfat iocharset=utf8,umask=000 0 0
/dev/sdc2       /media/ExtPart2   vfat iocharset=utf8,umask=000 0 0
/dev/sdc3       /media/ExtPart3   vfat iocharset=utf8,umask=000 0 0
/dev/sdc4       /media/ExtPart4   vfat iocharset=utf8,umask=000 0 0

#/dev/hda        /media/DVD RW   udf,iso9660 user,noauto     0       0
#/dev/hdb        /media/CD RW   udf,iso9660 user,noauto     0       0
/dev/sdc5        /media/Kingston vfat iocharset=utf8,umask=000 0 0   
#auto defaults,user 0 0 
#vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0
#/dev/sdc5 	/mnt/Kingston auto defaults,user 0 0

---

### Post by bodhi.zazen on 2006-11-26
fstab looks OK to me.

How are you mounting the devices and what permissions problems are you having?

---

### Post by Gerry Atric on 2006-11-26
Thanks for your reply,
I keep getting a message that only root can mount the partitions. Any attempt to mount through properties fails. 
Get this when I try to mount -a
jeff123@jeff123-Main:~$ sudo mount -a
Password:
mount: mount point /media/ExtPart1 does not exist
mount: mount point /media/ExtPart2 does not exist
mount: mount point /media/ExtPart3 does not exist
mount: mount point /media/ExtPart4 does not exist
mount: special device /dev/sdc5 does not exist
jeff123@jeff123-Main:~$

---

### Post by taurus on 2006-11-26
> **Gerry Atric said:**
> Thanks for your reply,
I keep getting a message that only root can mount the partitions. Any attempt to mount through properties fails. 
Get this when I try to mount -a
jeff123@jeff123-Main:~$ sudo mount -a
Password:
mount: mount point /media/ExtPart1 does not exist
mount: mount point /media/ExtPart2 does not exist
mount: mount point /media/ExtPart3 does not exist
mount: mount point /media/ExtPart4 does not exist
mount: special device /dev/sdc5 does not exist
jeff123@jeff123-Main:~$
You need to create those mountpoints first before you can mount stuff to them...

```
sudo mkdir /media/ExtPart1 /media/ExtPart2 /media/ExtPart3 /media/ExtPart4
sudo mount -a
```

Check your /dev/sdc5 to make sure it's there because the kernel can't find it!!!

---

### Post by Gerry Atric on 2006-11-26
Thanks for that advice Taurus. I can now view contents of the partitions in 'Computer' for all four removable partitions but get the following symbols over the icons.

A orange circle with a hand in same over the ExtPart 1-4 and a orange circle with exclamation mark over the filesystem icon.

The removable flash stick also shows under ExtPart1

---

### Post by buddie on 2006-11-26
is that really 'hand' icon or is it the usb symbol? this is normal, it's there to tell you that those are removable drives. :)

---

### Post by Gerry Atric on 2006-11-27
Bodhi.Zazen, Taurus and Buddie,

Thanks for your help, much appreciated.

---

