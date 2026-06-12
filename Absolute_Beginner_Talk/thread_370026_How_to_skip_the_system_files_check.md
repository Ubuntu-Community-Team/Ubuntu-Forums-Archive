---
title: "How to skip the system files check ?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-25
How to skip the system files check before  the boot ?
I think it takes too much time , over 5 minutes ..
How to do this ?

---

### Post by terdon on 2007-02-25
Could you post your /etc/fstab ile?

I assume you have  a windows partition, formatted as NTFS. If you find that partition's line in the fstab file you will see something like this:
[QUOTE]
# Entry for /dev/hda1 :
UUID=A8AC250FAC24DA18 /winblows/D ntfs-3g defaults,locale=en_US.UTF-8 0 2

If you change that last 2 to 0, the drive will not be checked at startup.

---

### Post by almasry on 2007-02-25
yes , you are right,
i edited the file with nano , and turned all the last ones to zeros ..
am i right , and what does this mean ?
 and this is the content of the file :
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=cec35ddd-4535-4256-84a8-de8f57bfafb3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=BC2C805C2C801414 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=13E0-1C28  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=42E8-06C1  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=4211a1a8-ac6a-4a78-9628-6bbe9c3202fb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by almasry on 2007-02-25
sorry , repeated post

---

### Post by shanepardue on 2007-02-25
Is there a key command to skip it just once if you're in a hurry or something?

---

### Post by terdon on 2007-02-25
You should change these lines:
> # /dev/hda1
UUID=BC2C805C2C801414 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=13E0-1C28 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6
UUID=42E8-06C1 /media/hda6 vfat defaults,utf8,umask=007,gid=46 0 1


to

> 
# /dev/hda1
UUID=BC2C805C2C801414 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hda5
UUID=13E0-1C28 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda6
UUID=42E8-06C1 /media/hda6 vfat defaults,utf8,umask=007,gid=46 0 0


These numbers tell the system in what order the drives should be checked. The 0 just tells it not to check this drive.

shanepardue: as far as I know there is no such key...

---

