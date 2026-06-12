---
title: "Can't enable DMA on my DVD!"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by VictorGavrish on 2006-08-27
Like it says in the title. When I run hdparm to enable DMA it says:
```
victor@desktop:~$ sudo hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

When I run hdparm without parameters it says:
```
victor@desktop:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

Under Windows DMA works fine.

Please help?

---

### Post by rbmorse on 2006-08-27
SATA drive. DMA is always on.

---

### Post by Frank Golden on 2006-08-27
> **rbmorse said:**
> SATA drive. DMA is always on.
That would explain why I get the same error on my 
laptop which uses SATA HD. Can I assume my DVD/CD drive uses SATA
as well? I get the error when I try to check for DMA on my Optical drive. My optical drive acts like it is using DMA, audio
and DVD's play smoothly.

---

### Post by VictorGavrish on 2006-08-27
Well, I think my DVD is connected using an IDE bus. Only two days ago I was installing a new SATA hard disk, and I had to buy a SATA bus in order to install it; the DVD, I noticed, was connected by a visibly different bus to a different set of ports on my motherboard, which the motherboard manual said were IDE ports. Plus, when I copy anything from the DVD drive, the CPU usage goes 100% all the time. This shouldn't happen with DMA, right?

---

