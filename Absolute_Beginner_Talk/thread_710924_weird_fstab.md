---
title: "weird fstab?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by wildseven on 2008-02-29
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cb2d2852-f409-46f4-b972-00bc62d182ec /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3690ea2d-9c3c-4c68-80dd-798a0ef0571b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1 /media/wind0ze ntfs-3g defaults,locale=en_US.utf8 0 0
```

Hey i was wondering why it mounts my root partition and swap partition like that? it's not the class /dev/sda2 /media/ubuntu yada yada yada

---

### Post by PeterJS on 2008-02-29
UUIDs are unique to a parition and will never change regardless of how you order the drives or what machine you put them in. Where as the name of the dev node is dependent on the physical order of the drives in the machine. It's just the new style of specifying devices.

---

### Post by wieman01 on 2008-02-29
The UUID uniquely identifies your partition, the use of it is pretty common nowadays. But of course you could replace each of the with '/dev/sda2', etc. Alternatively your 'fstab' would look like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
/dev/sda2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
/dev/sda5    none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1 /media/wind0ze ntfs-3g defaults,locale=en_US.utf8 0 0
It makes little difference unless you change the size of your partitions. UUID's can be a hassle in that case because they change.

---

### Post by bodhi.zazen on 2008-02-29
Ubuntu changed to UUID with 6.10 I think ??

If you would like to read about fstab : 

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by wieman01 on 2008-02-29
Nicely written, bodhi.zazen! :-) Well done I'd say.

---

### Post by Thingymebob on 2008-02-29
To find the UUID's of all your devices, type
```
blkid
``` in a terminal

---

### Post by wildseven on 2008-02-29
thank you all very much!

---

