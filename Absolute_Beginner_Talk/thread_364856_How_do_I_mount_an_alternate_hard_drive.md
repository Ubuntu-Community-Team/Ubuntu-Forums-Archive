---
title: "How do I mount an alternate hard drive?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-18
I want Ubuntu to mount a storage disk I have, listed as /dev/hdd1. How can I get it to always mount it on system startup? Thank you.

---

### Post by STREETURCHINE on 2007-02-18
what is the output from

```
sudo fdisk -l
```

---

### Post by StarscreamD on 2007-02-18
Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7296    58605088+   7  HPFS/NTFS

---

### Post by STREETURCHINE on 2007-02-18
ok try this tutorial


[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by nailzs on 2007-02-18
error..

---

### Post by StarscreamD on 2007-02-18
Great! This is how it ended up...

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdd1 /winfiles ntfs nls=utf8,umask=0222 0 0

Works awesome. Thanks again!

---

