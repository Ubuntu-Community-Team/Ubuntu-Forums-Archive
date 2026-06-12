---
title: "Name of usb stick"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-12-29
How do a get the partition name of my USB-stick? (Is partition name the correct name, I mena a name starting with /dev/sd..., or something).

Please!

---

### Post by Mark_in_Hollywood on 2007-12-29
From Places/Computer/File System

mine is:

/dev/disk/by-id

In the future, please say what your goal or purpose is. That makes giving help MUCH easier. thanks.

---

### Post by p_quarles on 2007-12-29
> **hannulan said:**
> How do a get the partition name of my USB-stick? (Is partition name the correct name, I mena a name starting with /dev/sd..., or something).

Please!
You can get the device names of all attached devices by running this:
```
sudo fdisk -l
```

---

### Post by hannulan on 2007-12-29
The purpose is to install ubuntu on a usb-stick. But i have to be sure of the name of it so a don't do something to, let say, the hard disk drive.

fdisk seemed to be the right program to run. Thanks!

---

