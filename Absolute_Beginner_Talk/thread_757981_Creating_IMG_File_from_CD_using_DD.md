---
title: "Creating IMG File from CD using DD"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-04-17
Hi,

I have a DVD and would like to convert it into an image file, for example the following works:

dd if=/dev/fd0 of=/root/floppy.img

However, for a CD, what should be the if since i cant find the CD Drive in the /dev or /mnt folder.

Thanks!

Mark

---

### Post by quirks on 2008-04-17
Hi markbusu,

if you are sure that your CD/DVD drive is recognized properly (i.e., you can read the content of them in Nautilus, for example), then you can use the **mount **command to display all mounted devices/partitions. Just open a terminal and type **mount** without any arguments, after you have mounted a CD/DVD in Nautilus. The device should be listed there.

quirks

---

### Post by Bachstelze on 2008-04-17
```
dmesg | grep CD
```

would work, too.

---

### Post by maybeway36 on 2008-04-17
/dev/cdrom should be a symbolic link to your CD drive.

---

### Post by bumanie on 2008-04-17
I think if you looked at fstab, you would find the name of cdrom > cat /etc/fstab It's probably /media/cdrom or something similar.

---

### Post by ScorpKing on 2008-04-17
ls -l /dev/cdrom will show you where it is and then use dd if=/dev/<cdrom_device> of=mydvd.iso and if you have problems reading from it install ddrescue and rather use that

---

