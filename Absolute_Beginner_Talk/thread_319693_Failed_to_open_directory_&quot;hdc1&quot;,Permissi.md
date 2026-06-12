---
title: "Failed to open directory &quot;hdc1&quot;,Permission denied."
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by hafez on 2006-12-16
Hi,
I am new with linux, I now try to throws away windows, but I need to use some of my old  windows file, my Xubunt automatically mount the drives, but when I try to open any one, I have this error : 
```
Failed to open directory "hdc1". Permission denied.
```

and my /etc/fstabe 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=035c5d36-e16c-490d-b452-5c70d813d104 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=FC95-0480  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc3
UUID=5A71-4815  /media/hdc3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=CCA1-56B7  /media/hdc5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc6
UUID=D4A7-1C69  /media/hdc6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc7       /media/hdc7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc8
UUID=8867-95A9  /media/hdc8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0




```

any Ideas,
Thanks  ;)

---

### Post by bodhi.zazen on 2006-12-16
How did you access hdc1? 

It is located at /media/hdc1 (not /dev/hdc1)

fstab looks OK.

---

