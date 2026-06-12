---
title: "Unmounting Partition"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by xander848 on 2006-06-28
Hey I used the unmount command to unmount a partiton. After a restart it was automatically remounted. How would I stop ubuntu from doing this?

---

### Post by aysiu on 2006-06-28
```
sudo cp /etc/fstab /etc/fstab.old
sudo nano /etc/fstab
``` Delete the offending line. Save and exit (Control-X, Y, Enter).

---

