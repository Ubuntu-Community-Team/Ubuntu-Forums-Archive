---
title: "CD not working or mounted"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by dileepk on 2006-12-14
i just used desktop 6.10 i can't open cd/dvd drive.  i was able to load desktop from iso cd but since then it can't find it.   when i check computer it shows cdrom 1 but can not mount it. i am new to linux.

---

### Post by faraazs on 2006-12-14
```
cat /etc/fstab
```run that command in the terminal and paste its output here please :).

---

### Post by drphilngood on 2006-12-14
edit:
faraazs got here first.

---

### Post by dileepk on 2006-12-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b6dfca0-6995-4c18-8d7e-658640432a17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c8fce651-630a-48d2-b828-781c28714d59 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
dileep@dileep-laptop:~$ 

this is the output

---

