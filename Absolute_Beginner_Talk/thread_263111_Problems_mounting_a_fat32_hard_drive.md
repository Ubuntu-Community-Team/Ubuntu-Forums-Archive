---
title: "Problems mounting a fat32 hard drive"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2006-09-22
I'm currently having a problem mounting a newly formated hard drive that has fat32 as the filesystem. The snytax im using is as follows


```
sudo mount -t fat32 /dev/hdb1 /media/hdb1
```

It's telling me that fat32 is an unknown filesystem. What change do i need to make to mount the drive?

---

### Post by jcrnan on 2006-09-22
try vfat or vfat32

---

### Post by SpiceWeasel on 2006-09-22
vfat32 said the same thing and vfat returned the error "special device /dev/hdb1 does not exist. Which is weird cause it shows up in the computer window but wont let me mount from there cause im not root.

---

### Post by jcrnan on 2006-09-22
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Follow the guides there and it should work nicley

---

