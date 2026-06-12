---
title: "My Windows drive was removed!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by enjtpl on 2007-12-09
My Ubuntu desktop has one Windows HDD. But a shortcut of the drive removed. What do I do? The format of drive is NTFS and OS is Windows XP.

---

### Post by spai on 2007-12-09
Cant you mount it back?

---

### Post by enjtpl on 2007-12-09
I don't know how to mount it.

---

### Post by Aseld on 2007-12-09
```
mount -t ntfs /dev/hda1 /home/[username]/winhd
```

Edit for your hard drive partition and folder. Note that you need to create the folder first.

---

