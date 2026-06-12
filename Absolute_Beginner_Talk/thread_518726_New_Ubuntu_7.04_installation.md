---
title: "New Ubuntu 7.04 installation"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by kandas on 2007-08-06
New Ubuntu 7.04 installation not detected on dell inspiron 5100 laptop. Message no OS detected.

---

### Post by bigfox on 2007-08-06
Sounds like grub didn't get installed or that the partition didn't get set as bootable.

This should only happen if the partitions were set manually and you forgot to set the boot partition as bootable.

---

### Post by bigfox on 2007-08-06
You could boot the Live CD and then use Gnome Partition Editor to set the partition as bootable by enabling the boot flag.

---

### Post by asmoore82 on 2007-08-06
> **bigfox said:**
> Sounds like grub didn't get installed or that the partition didn't get set as bootable.

This should only happen if the partitions were set manually and you forgot to set the boot partition as bootable.

you don't have to mess with the bootable partition flag on *NIX systems.

It sounds to me like the hard drive is not in the Boot order of the BIOS

---

