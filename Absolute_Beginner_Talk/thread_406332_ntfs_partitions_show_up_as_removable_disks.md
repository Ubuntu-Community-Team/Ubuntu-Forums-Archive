---
title: "ntfs partitions show up as removable disks"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ubiwankanubi on 2007-04-10
on my gnome desktop there are icons of the ntfs partitions on my computer as well as the swap partition, and those partitions also show up on the disk mounter panel. is there a way to not show the ntfs partitions and just CD, Flash Drives, and other removable media on the desktop and disk mounter?

---

### Post by thefoolisme on 2007-04-11
I'm guessing that when you set up the mount for Windows, you set it up as /media/windows.  That will cause it to show up on the desktop.  Just mounting it as /windows has it show up in the filesystem.

---

### Post by ubiwankanubi on 2007-04-13
the windows partitions were setup in the /media/ but i don't know much about this UUID thing... if I change the location of the partition to /windows1 /windows2, etc. do I need to change the UUID?

I don't know why but my swap partition also shows up as a removable device on the desktop...

Also, how can I make the ntfs partitions writeable?

BTW, i'm trying this on ubuntu 7.04 beta.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=700b54bb-3371-4436-8742-8c5b89f68dbd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda10
UUID=44cfd3ab-de30-4b32-be46-c9cf2ed1f010 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D6004A5F004A46A9 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=FC04E00304DFBEB8 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=FA8CB1E48CB19C17 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=A05010A550108466 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=4c5dbfc8-e18a-4d84-a88a-efac6b2b246a /opt            ext3    defaults        0       2
# /dev/sda9
UUID=802788f4-acc4-4049-b5d4-fa6b527c29eb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

