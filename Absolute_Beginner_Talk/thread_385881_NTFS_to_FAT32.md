---
title: "NTFS to FAT32"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by nerds in parties on 2007-03-16
I have one external hard drive NTFS, usb.

I have problems mounting it with ntfs. If I change it to fat32 with gparted I will loose my files?

---

### Post by mahy on 2007-03-16
> **nerds in parties said:**
> I have one external hard drive NTFS, usb.

I have problems mounting it with ntfs. If I change it to fat32 with gparted I will loose my files?

Definitely yes. Your only option is backup.

---

### Post by nerds in parties on 2007-03-16
> **mahy said:**
> Definitely yes. Your only option is backup.

thanks. what can i do? it says cannot mount volume.

---

### Post by mahy on 2007-03-16
Are you trying this:

sudo mount -t ntfs /name/of/disk /mnt/something

(the directory /mnt/something has to be created beforehand)

---

