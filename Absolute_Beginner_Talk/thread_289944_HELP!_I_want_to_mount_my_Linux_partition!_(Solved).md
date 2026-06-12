---
title: "HELP! I want to mount my Linux partition! (Solved)"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-10-31
Hi.

I'm on the live CD right now and I want to mount my /dev/hda1 partition - so that I can make some changes before installing Ubuntu.

How do I mount it with read/write rights? The filesystem is ext3 - or whatever filesystem Ubuntu creates by default.

---

### Post by aysiu on 2006-10-31
```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/hda1 /media/recovery
gksudo nautilus
```

---

### Post by zugu on 2006-11-01
Thank you, aysiu, you're helpful as always!

---

