---
title: "[B]how can i change my permisions for a fat32[/B]"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by singetak on 2006-08-28
**i have a fat32**
but the user that i enter desktop have no permision on it
the only i can write to my hard disk is
by alt-f2 then writing gksudo nautilus


this is my fstab:..
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda5 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
Edit/Delete Message

i tried sudo chmod 755 /media/sda5
i tried sudo chown user /media/sda5
](*,) ](*,) ](*,) ](*,) ](*,) 
    i tried sudo

---

### Post by orb9220 on 2006-08-28
try changing defaults to users

---

### Post by annda on 2006-08-28
or umask to 000

---

### Post by singetak on 2006-08-28
i tried that and it also didn't work
](*,)

---

### Post by singetak on 2006-08-29
:-D thank you guys i needed to put:) users instead of defaults
and i needed to restart the computer.sudo mount -a has no effect on that:-D

---

