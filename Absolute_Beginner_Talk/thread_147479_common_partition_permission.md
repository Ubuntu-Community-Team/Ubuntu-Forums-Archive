---
title: "common partition permission"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-20
when i open a file browser in ubuntu and expand the common partition, i see all folder icons have locks in it.  how do i change permission so that a certain user other than the root will have default write access to this common partition? thanks!

---

### Post by frodon on 2006-03-20
Maybe you didn't set the good rights in your fstab file.
Could you post here your fstab file and tell us which partitions don't have the good rights ?
To open thefstab file : ```
sudo gedit /etc/fstab
```

---

