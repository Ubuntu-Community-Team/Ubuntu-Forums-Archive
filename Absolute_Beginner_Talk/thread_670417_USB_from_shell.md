---
title: "USB from shell"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by eccheng on 2008-01-17
Hello all.  I was wondering if you guys could help me with this.  Long story short, my gdm crashed and I cannot get back onto the xwindows system.  I have the file I believe i need in my usb drive but I dont know how to access it from my usb.  Which directory should my usb drive be on when i access it through the shell?

Thanks a bunch.

---

### Post by milton1 on 2008-01-17
You may need to mount the drive manually. The drive is likely listed as something like 'sdb1' in /dev use this to find the drive:

```
fdisk -l 
```

then to mount:

```
mkdir usbmount

sudo mount -t vfat /dev/sdb1 usbmount

```

replacing sdb1 with the device name fdisk gives you.

---

### Post by stchman on 2008-01-17
> **eccheng said:**
> Hello all.  I was wondering if you guys could help me with this.  Long story short, my gdm crashed and I cannot get back onto the xwindows system.  I have the file I believe i need in my usb drive but I dont know how to access it from my usb.  Which directory should my usb drive be on when i access it through the shell?

Thanks a bunch.

If you are referring to a flash drive or a usb hard drive they are mounted in the /media folder.

They usually start with disk and go from there.

---

