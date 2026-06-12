---
title: "File Permissions"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by jmdean on 2006-12-10
I am having some trouble with file permissions for my FAT32 drive which I want to access under both XP and Ubuntu but all the files and folders are set to read only in Ubuntu.

I have read up on chmod and can change the permission on individual files and have also amended the /etc/fstab file to show hdd1 as umask=000 but that still leaves all the files I have not individually altered as read only.

Could anyone tell me where I am going wrong or where I could read more (in easy terms) to understand what is going on and how to change file permissions for all the files on a drive?

---

### Post by StormNet on 2006-12-10
Would you be able to post your fstab so that we can see how it is currently mounted?

---

### Post by bscbrit on 2006-12-10
Firstly, you cannot set individual file access permissions on a FAT32 drive - it doesn't have the same structure as ext3 and therefore cannot understand them.

All you can do is set the drive and/or partition for full read / write access.

---

### Post by jmdean on 2006-12-10
Here is a copy of my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d4c570d1-6d21-4ddd-bef5-df45af2e735e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda10
UUID=9d5cd711-5644-4d94-8acb-8d7a7a662218 /home           ext3    defaults        0       2
[B]# /dev/hdd1
UUID=0F20-18E0  /media/hdd1     vfat    umask=000 0    [/B]   0
# /dev/sda1
UUID=A61069381069111B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=12ACDF85B9CB4AD9 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=12D17523FA0325D9 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=7CC41FA6C41F61A6 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=9a6869a8-b674-46c8-8220-c6002302640b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Does this help at all.

---

