---
title: "Formatting a USB pen drive"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-06-09
Alright, I found a decent guide  on the net that lets me format my USB pen drive. But it assumes that the pen drive is at /dev/sda1. That does not apply to me, of course, because I only have a sda in my /dev folder and not a sda1. So, where can you get a list of devices on your computer, like /etc/fstab? My pen drive doesn't come up in fstab, so where can I find my USB in the dev folder?

---

### Post by yurimxpxman on 2007-06-09
> **Sabretooth said:**
> Alright, I found a decent guide  on the net that lets me format my USB pen drive. But it assumes that the pen drive is at /dev/sda1. That does not apply to me, of course, because I only have a sda in my /dev folder and not a sda1. So, where can you get a list of devices on your computer, like /etc/fstab? My pen drive doesn't come up in fstab, so where can I find my USB in the dev folder?
```
sudo fdisk -l
```

**Note:** that's l as in Laser

---

