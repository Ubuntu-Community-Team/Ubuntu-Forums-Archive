---
title: "Enabaling Drivers"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by spanerman on 2007-05-13
when i try to enable nivedia to work i get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


what to do?

---

### Post by meng on 2007-05-13
Try
sudo dpkg --configure -a

see if that fixes the problem, then try enabling your nvidia.

---

