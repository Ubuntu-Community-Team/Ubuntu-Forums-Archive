---
title: "Replace harddisk"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by dacium on 2008-01-14
I have a 120GB HDD and am looking to replace it with a 500GB drive, I will need the 120GB to put into another system.

What is the easiest way to directly image everything over and make the extra free space available. I am running ubuntu 7.10 and have done a rather complicated setup on it to run as a PVR, so I would like to avoid having to reinstall and reconfigure.

---

### Post by Tekno_Cowboy on 2008-01-14
How is the 120GB drive configured?
IE.
1GB /boot
5GB /swap
10GB /
The rest /home

or just post the output of:
```
fdisk -l
```

---

