---
title: "hdparm failure message"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by jandjfrench on 2008-03-03
Hi,

After typing "hdparm /dev/hdc" in the terminal I get the following:

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

What is the meaning of the "HDIO..." failure and how can I correct it?

---

### Post by Average Joe on 2008-03-03
I get
```
/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 19457/255/63, sectors = 312581808, start = 0
```
as hdparm output. So I guess HDIO_GETGEO means that hdparm cannot get the geometry of your disk. I have no clue how to fix that.

Maybe
```
sudo hdparm -I /dev/hdc
```
will give you some more information about your disk and the error.

---

### Post by Cypher on 2008-03-03
Show us the output of
```

sudo fdisk -l

```

---

