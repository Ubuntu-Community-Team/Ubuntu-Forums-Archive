---
title: "[SOLVED] how to know the remaining free space in hard disk"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by arai on 2007-08-31
i want to know the free space remaining in the linux partition. how to know this please reply.

---

### Post by Elegorod on 2007-08-31
Run  System - Administration - System monitor.
Choose the tab "File systems". Here's all partitions

---

### Post by lloyd_b on 2007-08-31
In a terminal window, type
```
df
```
("df" stands for "disk free", I think).

Note that by default, "df" display space in kB (which can be a bit cumbersome for larger disks.  To get the space in megs
```
df -m
```

There are also many GUI tools and such that will display such info.

Lloyd B.

---

### Post by abhilash82 on 2007-08-31
You can find a disk space analyser tool in Accessories > Disk Usage Analyser. This link below should aldo help you.
[https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

---

### Post by ramjet_1953 on 2007-08-31
Navigate to:

[COLOR="Blue"]Applications>Accessories>Disk Usage Analyzer[/COLOR]

Regards,
Roger 8)

---

### Post by arai on 2007-08-31
Elegorod, lloyd_b, abhilash_82, ramjet_1953 thanks for the replies. 

> Applications>Accessories>Disk Usage Analyzer

worked.

---

