---
title: "custom mount fstab read-write"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-17
when I plug in a usb drive, it autoloads to /media/disk with perfect (read-write) permissions.


I'd like to change that to autoload to /media/e2

the device is /dev/sdc1

when I add

```
#UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1
```

to fstab, and then mount /dev/sdc1 /media/e2

it mounts fine but is ro.  

How can I get it to mount to e2 with rw permissions?

Thanks.

---

### Post by PaulFr on 2007-08-17
IMHO,

1. Your /etc/fstab entry should read as ```
UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1
```i.e. without the leading **#** symbol. If the '#' symbol is there, it means the rest of that line after the '#' symbol is a comment.

2. If you are sure the device is always loaded at **/dev/sdc2**, then the entry could also read ```
/dev/sdc2 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1
```i.e. use the device instead of the UUID.

3. If you are manually mounting the device and there is an **uncommented** (i.e. without the leading # symbol) entry in /etc/fstab, then ```
mount /media/e2
``` should suffice. Otherwise, the command would be ```
mount -t vfat -o rw,nodev,shortname=mixed,utf8,umask=077 /dev/sdc2 /media/e2
```.

---

### Post by johntkucz on 2007-08-17
thanks

---

