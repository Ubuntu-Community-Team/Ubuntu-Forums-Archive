---
title: "Weird Hard drive problem"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Kemik88 on 2007-07-19
Hello all,

After installing Ubuntu on a partition of my hard drive I could see my Windows partition and access it under "Computer". However, now that partition has disappeared from the Computer menu. Is there anyway way to force Ubuntu to reload the drives and check for other partitions?

---

### Post by Nevis on 2007-07-19
You could use
```
sudo fdisk -l
```
to list the partitions then use mount to mount whichever partition you're missing. Edit the fstab file to make it mount automatically.

Not sure if this totally answers your question but it should get you access to the partition again.

---

