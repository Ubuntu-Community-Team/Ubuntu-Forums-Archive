---
title: "how do i unmount a windows partition"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-06-21
ne ideas?"

---

### Post by yabbadabbadont on 2007-06-21
In a terminal window, run ```
sudo umount /media/windows
```
Change /media/windows to be the correct path for your system.

---

### Post by Crafty Kisses on 2007-06-21
> **LiNuXxToOthEMaX said:**
> ne ideas?"
Here try this:
```
sudo umount /media/windows
```

---

### Post by LiNuXxToOthEMaX on 2007-06-21
> **Codename said:**
> Here try this:
```
sudo umount /media/windows
```

k but how can i view it a partition

---

### Post by Crafty Kisses on 2007-06-21
> **LiNuXxToOthEMaX said:**
> k but how can i view it a partition

I'm not sure what you're asking but here, try this:
```
sudo fdisk -l
```

---

