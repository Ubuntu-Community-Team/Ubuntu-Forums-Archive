---
title: "usbdev_ioctl: REAPURBDELAY"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-11-24
I don't know where to post this, so I'll start here and then someone can move it if it belongs in a different forum.:)

Trying to track down intermittent problems with a USB device.  I have captured the traffic by turning on usb snoop in the kernel, running the app, turning off usb snoop and then copying the syslog to another file so I can hang on to it.  Ran this again when it succeeded and have been comparing the log info.  The one that fails kicks out this extra line in the log (everything else is the same except for the actual length being 0 when it fails):

usbdev_ioctl:  REAPURBDELAY

I know that usbdev_ioctl is part of the usb core for the kernel, and I suspect the REAPURBDELAY is saying that the time-out specified on the usb call was reached, but I don't know.  

Can someone tell me what this means?

Thanks!:)

---

### Post by anewguy on 2007-11-24
bump

---

### Post by anewguy on 2007-11-25
bump

---

### Post by anewguy on 2007-11-25
bump

---

### Post by anewguy on 2007-11-27
Thought I'd bump this one more time now that the holiday is over, maybe someone can help?
Thanks!

---

