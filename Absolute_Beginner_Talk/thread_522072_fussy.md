---
title: "fussy"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-10
i have an external HD with my music etc on.
yesterday it mounted fine.

but doay in terminal i get this error!

```

scott@scott-desktop:~$ sudo mount /dev/sdc1
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
scott@scott-desktop:~$ 


```

why is itr saying this? and not doing what  i, the user, wants it too?

---

### Post by jw5801 on 2007-08-10
What filesystem is the disk? If it is ntfs then you may want to run a diskcheck utility on it (I know gparted should be able to do the trick), otherwise specify the filesystem with the -t option. ie.
```
sudo mount -t ext3 /dev/sdc1
``` if it is ext3.

---

### Post by skymera on 2007-08-10
its definate NTFS

i try that with NTFS.

ok it didnt do anythig :(

---

### Post by jw5801 on 2007-08-10
Well then Ubuntu is telling you that your file system is corrupt. I'm not entirely sure on the best tool to test/fix an ntfs file system, but I don't know that Linux is particularly friendly for playing with NTFS file systems. If you have a Windows boot around somewhere try mounting it in that and see what happens. Otherwise it might be an idea to start a new thread with a slightly more informative title, ie. "NTFS no longer mounting" or something along those lines.

---

### Post by Inxsible on 2007-08-10
post the output of your fstab and also your sudo fdisk -l

---

### Post by asmoore82 on 2007-08-10
unplug and replug the drive and run
```
~ $ dmesg | tail
```
and make sure the have the right device.

---

