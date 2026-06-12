---
title: "Why can't I see any USB devices when I use lsusb?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-08-22
I built my own kernel, which is 2.6.22.1. The original kernel is 2.6.18.2

When I boot with my own kernel and use /usr/sbin/lsusb, I can't see any USB devices.

But if I boot with the origial kernel, I can see two. 

Is there anything wrong with my new kernel?

thanks.

---

### Post by Terl on 2007-08-22
Sounds like a module is missing/not turned on.  Check here:  [Linux USB FAQ]("http://www.linux-usb.org/FAQ.html#gs1")

---

### Post by J33pG33k on 2007-08-23
I recently had the same problem with kernel 2.6.22.2 that I built.  After scouring over the config options, I found USB_DEVICE_CLASS listed under the USB section.  The description states that it is deprecated, but provides backward compatibility for libusb, which lsusb apparently depends on.

I recompiled with this flag set and everything is back to normal.

Hope this helps.

---

