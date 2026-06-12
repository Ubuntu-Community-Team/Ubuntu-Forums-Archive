---
title: "USB Hard Drive - how do I find its device name?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-09-23
I have an external USB hard drive.  How do I determine which device it is mount to?

I need to know the device name so I can run the mount command.

Thanks

Carl

---

### Post by Jimmyfj on 2007-09-23
Your USB drive should automount when you plug it in. Otherwise it's either /media/disk or /media/usb

---

### Post by ddrichardson on 2007-09-23
/media is the mount point, if its a USB disk then the device will be /dev/sdXY wher X is whatever number channel and Y is the partition that appears whe you connect it.

---

