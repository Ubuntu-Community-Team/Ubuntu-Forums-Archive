---
title: "problems"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by windows hater on 2007-07-11
i try to use synaptic package manger  and i get this

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. [/B]

---

### Post by jordanmthomas on 2007-07-11
Well, try what it says:
```
sudo dpkg --configure -a
```
and see if that helps things along.

---

### Post by Atomic Dog on 2007-07-11
open a terminal window.

type in: sudo dpkg --configure -a'

---

### Post by windows hater on 2007-07-11
thank you it worked

---

