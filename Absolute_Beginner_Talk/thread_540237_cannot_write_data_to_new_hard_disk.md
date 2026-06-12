---
title: "cannot write data to new hard disk"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by peebly on 2007-09-01
Hello

Installed a second hard disk, formated to ex3 using Gparted.

Why cannot I copy files to the disk, it says I don't have permission.

---

### Post by felicity on 2007-09-01
Use:
sudo chmod -R a+rwx /path/to/drive

where /path/to/drive is .. the path to your drive. like/mnt/NewDrive or /media/DriveName

---

### Post by peebly on 2007-09-01
Hello

Thanks thats got it.

Is there away to make the disk mount automatically on boot.

At the moment I have to click on it, then put in my password.

---

### Post by taurus on 2007-09-01
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add an entry for it.

```
/dev/XXX     /media/XXX   ext3   defaults   0   1
```
Replace XXX with the actual device name like hdb1 or sdb1...

---

