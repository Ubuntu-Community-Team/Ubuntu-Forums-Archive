---
title: "Mounting usbdisk in console"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by dimovich on 2007-01-30
Hello,

How to mount a usb disk in text-mode console? I'm running Ubuntu on an old laptop, so I disabled gdm.

Thanks!

---

### Post by taurus on 2007-01-30
Maybe something like

```
sudo mount -t vfat /dev/sda1 /media/usbdrive -o iocharset=utf8,umask=000
```

---

### Post by dimovich on 2007-01-30
> **taurus said:**
> Maybe something like

```
sudo mount -t vfat /dev/sda1 /media/usbdrive -o iocharset=utf8,umask=000
```

Thanks, it works!

---

