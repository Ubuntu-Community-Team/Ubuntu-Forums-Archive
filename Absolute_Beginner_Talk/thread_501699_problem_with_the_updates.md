---
title: "problem with the updates"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by itsryan on 2007-07-15
I was trying to get some updates and i get this error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

I dont know how to run anything i just installed ubuntu, so if anyone could help me that would be great.

---

### Post by forestpixie on 2007-07-15
in terminal run

sudo dpkg --configure -a

---

### Post by Vajra Vrtti on 2007-07-15
[LIST=1]
[*]Open *Accessories -> Terminal*
[*]Copy/paste the following command and press Enter:
[*]```
**sudo dpkg --configure -a**
```
[*]Enter your password when asked
[/LIST]

**EDIT**: command corrected.

---

### Post by Vajra Vrtti on 2007-07-15
That message occurs sometimes when an install/update is interrupted.
Then, just enter the requested command to fix it.

---

### Post by Vajra Vrtti on 2007-07-15
The command was corrected in my first post.

---

