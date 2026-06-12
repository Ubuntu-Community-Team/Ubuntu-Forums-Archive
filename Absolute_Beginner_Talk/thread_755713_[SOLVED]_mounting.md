---
title: "[SOLVED] mounting"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-15
I have a dual boot and have mounted all my partitions in ubuntu
but the c drive of vista (sda1) unmuonts itself everytime i login to windows

---

### Post by powerpleb on 2008-04-15
> **sameer.india said:**
> I have a dual boot and have mounted all my partitions in ubuntu
but the c drive of vista (sda1) unmuonts itself everytime i login to windows

What do you mean "unmounts itself"? If you're logged into Vista then surely it must be mounted. Is your Vista login successful?

---

### Post by aeiah on 2008-04-15
im guessing windows is changing the partitions uuid each time you log in. what does your fstab file look like?
```
gedit /etc/fstab
```

---

### Post by aeiah on 2008-04-15
> **powerpleb said:**
> What do you mean "unmounts itself"? If you're logged into Vista then surely it must be mounted. Is your Vista login successful?

i think he means that if he logs into vista, then when he logs into ubuntu next, the vista partition is unmounted, but if he doesnt log into vista between ubuntu boots, it stays mounted.

---

### Post by sameer.india on 2008-04-15
aeah has got it right

---

### Post by sameer.india on 2008-04-15
sameer@sameer-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2946bc29-bb7c-466c-823e-86394c27eed3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=26A40C6DA40C4233 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=A26E18426E1811A1 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=9e904b2b-6cfc-4ad2-bdeb-f77f39217d8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by bumanie on 2008-04-15
Your fstab looks OK. One thing I'd ask is, "Do you always shutdown windows properly by choosing shutdown or restart or do you push reset to boot into ubuntu?" If you push reset to boot into ubuntu, the drive and OS is not closed down properly and ubuntu sees the drive as still being in use and will not mount it. Linux will not mount drives that have not been not correctly unmounted whether it be hard drives or usb pendrives.

---

