---
title: "Help formatting a ZIP disk"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-03-13
I'm trying to delete the contents of and format a 100MB ZIP disk to FAT. I've tried the various commands (such as "/sbin/mkfs –t vfat /media/zip") that I've seen on other threads, and none work. They all come back with "mkfs.vfat: unable to open /media/zip".

I'm lost. There must be a simple way to do this.

---

### Post by joshrobinson on 2008-03-13
have you tried using gparted to format it?

```
sudo apt-get install gparted
```
then launch gparted
```
sudo gparted
```

just be carefull

---

### Post by scragar on 2008-03-13
use```
mount
``` to find it's **device/partition name**, something like /dev/sda1 (I'm assuming sda1, replace with whatever it is) then unmount it:
```
sudo umount /dev/**sda1**
```
and reformat it:
```
sudo /sbin/mkfs &#8211;t vfat /dev/**sda1**
```

be sure to get the right device, nothing would be worse than accidentaly reformating you main hard disk or something similar.

---

