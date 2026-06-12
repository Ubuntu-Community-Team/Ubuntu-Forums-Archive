---
title: "Help with Flash Drives!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Keringe on 2006-09-24
[SIZE="3"][/SIZE]I need help configuring Ubuntu to run my SanDisk Cruzer Mini 512 mb flashdrive.. I need it for school but it says it only supports Windows and Mac(it specifically says it doesn't support Linux) But we've got the best brains around on this forum. Please help!

---

### Post by meng on 2006-09-24
To start with, I assume you've already plugged it in your Ubuntu box and it doesn't automount. Is this correct?

---

### Post by Keringe on 2006-09-24
Yes, but the light in the top of it lights up...

---

### Post by Keringe on 2006-09-25
OK well It seems to be working now but if I get the same problem I will come back!

---

### Post by tuxthepenguin on 2006-09-25
If you having trouble getting the drive to mount try the following
sudo mkdir /media/usb
sudo mount -t vfat /dev/sda /media/usb

when your done and wan to take it out
sudo umount /media/usb

---

