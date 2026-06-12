---
title: "harddisk and boot partition numbers"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by owerio on 2007-04-04
Hello. Could you give the command which will output the harddisk and boot partition numbers ?

---

### Post by lwalper on 2007-04-04
Try this
```
sudo fdisk -l
```

---

### Post by Maestro23 on 2007-04-04
In terminal:

> sudo fdisk -l

---

### Post by owerio on 2007-04-04
> **Maestro23 said:**
> In terminal:

Thansk to both of you. The output says my hard disk is **/dev/sda** but there is nothing about boot partition number. Asking this for Grub localization .

---

### Post by xopher on 2007-04-04
```
cat /boot/grub/device.map
```

First partition is 0 second 1 etc.

---

### Post by owerio on 2007-04-04
> **xopher said:**
> ```
cat /boot/grub/device.map
```

First partition is 0 second 1 etc.

Hello. Thanks for your help. It oututs this;(hd0) 

> (hd0)   /dev/sda

Will I use  **root (hd0,0**) for root localization? I dont understand the differ. between  /dev/sda , /dev/sda1.

---

