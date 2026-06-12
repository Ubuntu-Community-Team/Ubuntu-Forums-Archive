---
title: "Please help....Home Partition???"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by magicH$jxr on 2007-10-27
[FONT="Arial"][SIZE="2"]:)hello this is the content of my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=80b0c964-f163-45c2-a9cb-ace604b90209 /               ext3    defaults,erro$
# /dev/sda1
UUID=4C30E58930E57A7A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda5
UUID=3274e0ab-7563-4a07-bf34-7f394c01d51e /home     ext3    defaults        0  $
# /dev/sda6
UUID=4719-F165  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=4719-F17E  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=4719-F19C  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=389A-FCEE  /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3

would someone experienced please tell me whether the home folder is mounted on its own partition? I am running ubuntu 7.04 fully updated.  If not so, how can I go about mounting it. I have an extra ext3 partition I can use.  t/y in advance :) magic[/SIZE][/FONT]

---

### Post by Duck2006 on 2007-10-27
Yes it is

> UUID=3274e0ab-7563-4a07-bf34-7f394c01d51e /home ext3 defaults 0 $
# /dev/sda6

---

### Post by philinux on 2007-10-27
You sure do - its the best way to run the system, makes a reinstall a lot easier.

---

### Post by magicH$jxr on 2007-10-27
t/y  everybody :)

---

