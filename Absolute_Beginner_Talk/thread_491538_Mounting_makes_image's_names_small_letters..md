---
title: "Mounting makes image's names small letters."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by danubius on 2007-07-03
Hej there!
I am new to mounting devices, but there is one thing unclear to me: If I mount my camera's filesystem with```
mount -t vfat /dev/sda1 /media/camera
``` all file and folder names are in small letters, like *dcim*, *pict0815.jpg*; whereas if I mount it via nautilus in ubuntu, they read *DCIM* and *PICT0815.JPG*.

Thank you.

---

### Post by kidders on 2007-07-13
Hi there,

FAT filesystems aren't case sensitive, so I don't imagine there's anything to be concerned about. I'd say the inconsistency has to do with differences in the mount options you and Nautilus are using.

---

