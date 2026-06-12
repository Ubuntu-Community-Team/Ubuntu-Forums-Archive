---
title: "USB Drive"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by spencewah on 2006-03-07
When I plug in my USB drive it does not show up, instead a konqueror window pops up with an error:

> The file or folder media:/sda1 does not exist

and each time I plug it back in the letter changes (eg. sdb1, sdc1, sdd1)

But when I manually go to /media/sda1 I find all the files on my drive.

Confused..

---

### Post by Pragmatist on 2006-03-08
Please tell us the type of device (hard drive?) and the make and model.  Also, please give the output of the following commands:
```
ls -l /media
```
```
cat /etc/fstab
```
```
mount
```
```
cat /var/log/messages |grep usb
```
```
dmesg |grep usb
```
```
lshal |grep usb
```

---

