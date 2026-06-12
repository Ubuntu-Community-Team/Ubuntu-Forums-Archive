---
title: "no automounting"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by matiw on 2007-12-13
Hi everyone
i have this problem, my partitions doest mount automatically.
i didnt have this problem in feisty
any solution?

---

### Post by lvleph on 2007-12-13
post the output from

```
fdisk -l
cat /etc/fstab
```

---

### Post by matiw on 2007-12-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=1c3e19f0-784e-4397-a876-b05299caa9b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=a56ecdce-6c08-4b9c-9026-7b93eb5135c2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by ctyc on 2007-12-13
Here is a typical working /etc/fstab from a dual boot laptop running windows and Ubuntu(ext3) for your comparison:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1dc0c903-1a95-44e9-bbe4-78e7605f49a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=3660adcf-f609-4783-ac63-ed1fcaed3a88 /boot           ext3    defaults        0       2
# /dev/sda6
UUID=83e63934-c989-4eef-a5d7-fe33bfaf86b3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=F807-9BA6  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4e8476c6-32be-47f4-9812-ba30f1fcd39c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by matiw on 2007-12-13
i forgot to say that i have ntfs partitions
i think i have to modify fstab, but i dont remeber what i have to put in it

---

### Post by thelatinist on 2007-12-13
There are an incredible number of threads on here that deal with this issue.  Next time, try searching first.  [http://ubuntuforums.org/showthread.php?p=3915803#post3915803](http://ubuntuforums.org/showthread.php?p=3915803#post3915803)

---

### Post by lvleph on 2007-12-13
You didn't post the 
```
fdisk -l
```

Also this line concerns me
```
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```
Maybe someone can explain to me why hda would mount on /media/cdrom0?

---

### Post by matiw on 2007-12-13
it works thanks
next time i'm gonna search a little more

---

