---
title: "5th Generation 30 GB iPod won't mount"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Lgndryhr on 2008-03-25
I am unable to mount my iPod at all. Since the upgrade to Gusty I have not been able to now. This is one of many problems I am having with Gusty but am taking one step at a time. Also, gtkpod cannot seem to mount it either. Much help is appreciated.

---

### Post by OmahaVike on 2008-03-25
i'm working with dapper, and had some problems with my 3g 30 gig.

reboot.
what is in your /media directory before you plug in your ipod?
what is in your /media directory after you plug in your ipod (and wait a few seconds)?

if same result (nothing in there) you might want to try adding this to your /etc/fstab:

```
none /proc/bus/usb usbfs devgid=1004,devmode=666 0 0
```

reboot and try again?

---

### Post by Lgndryhr on 2008-03-25
before plug in iPod: /media contains cdrom (shortcut), cdrom0, usb, windows.
after plug in iPod: /media contains the same

why wouldn't it contain the same anyways after plugging in since it cannot mount my iPod at all. 

i added that line but it did nothing as i suspected it would. i say this because upon checking out my fstab, i see nothing that looks similar to that.

---

