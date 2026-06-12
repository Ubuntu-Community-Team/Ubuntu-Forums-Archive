---
title: "[SOLVED] Cannon access ubuntu"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Tabenx on 2007-11-24
I cannot access my installation of ubuntu, is it possible to access my files via a livecd linux to copy some files and if so which ones work best?
Thanks,
Tom

---

### Post by taurus on 2007-11-24
Yes, you can access your harddrive from the LiveCD but you first need to mount it before you can access it.  Do you know which partition Ubuntu is on?  If not sure, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Tabenx on 2007-11-24
Its on  /dev/hda1

---

### Post by taurus on 2007-11-24
Try

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
Your harddrive, Ubuntu, is now mounted to /media/ubuntu so you can use nautilus to navigate to it.

---

### Post by Tabenx on 2007-11-24
Dont i need to use some sort of livecd linux first though?

---

### Post by taurus on 2007-11-24
Yes, you need to boot your machine with Ubuntu LiveCD first.

---

