---
title: "Find Physical Location of USB"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Colinu on 2007-02-14
How do I find the physical address of a usb drive. Not like with usbls but how do I find /dev/***?

I' trying to follow [this.]("https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29")

But I can only seem to find the mount point of the USB, not the actual location.

---

### Post by Colinu on 2007-02-14
Bump, I really need help with this tonight.

---

### Post by bodhi.zazen on 2007-02-14
To find the physical location, turn on the light, open your eyes, and look near you computer. You should see the device close by, perhaps plugged into the usb port :lolflag:



Seriously though, plug in your usb drive, open a terminal, and type:

```
sudo fdisk -l
```

USB devices are typically sd, so if this the the first device it is likely /dev/sda1 ...

HTH

---

