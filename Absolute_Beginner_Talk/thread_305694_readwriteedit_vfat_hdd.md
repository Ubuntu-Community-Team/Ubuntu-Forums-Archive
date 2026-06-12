---
title: "read/write/edit vfat hdd"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by octoquake on 2006-11-23
so as of right now, i have my slave vfat hdd mounted and i can write to it, and read from it. but i cant delete or edit anything already on there.
how can i change this? id have to edit the fstab file right?

---

### Post by taurus on 2006-11-23
Yes, you set the permissions for your fat32 in /etc/fstab!  What does it look like anyway?

Applications -> Accessories -> Terminal:

```
cat /etc/fstab
```

---

### Post by octoquake on 2006-11-23
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=dc7a68d7-a499-4a9d-bc9b-7d3a79a8a957 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=35d68882-f234-4e04-8d5c-efb327a874da none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdd5 -- converted during upgrade to edgy
UUID=44F0-761B /media/hdd5 vfat user,auto,rw,exec 0 0

---

### Post by taurus on 2006-11-23
Change the last line in your /etc/fstab from

```
UUID=44F0-761B /media/hdd5 vfat user,auto,rw,exec 0 0
```
to

```
UUID=44F0-761B  /media/hdd5  vfat  iocharset=utf8,umask=000 0  0
```
Then, reboot...  You can edit your /etc/fstab with

```
gksudo gedit /etc/fstab
```

---

