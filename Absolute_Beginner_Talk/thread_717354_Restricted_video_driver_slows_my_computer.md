---
title: "Restricted video driver slows my computer"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-06
After i enable the nvidia restricted driver my computer become a bit slower, for instance opening a new tab in firefox take a second or 2 to open(note this is not with compiz enabled).  I want the restricted driver for the compiz features, anyone else having this issue and know why or how to fix it?  BTW, i have the 8860 gts moblie graphics card(512MB)

---

### Post by Crafty Kisses on 2008-03-07
> **RyanZec said:**
> After i enable the nvidia restricted driver my computer become a bit slower, for instance opening a new tab in firefox take a second or 2 to open(note this is not with compiz enabled).  I want the restricted driver for the compiz features, anyone else having this issue and know why or how to fix it?  BTW, i have the 8860 gts moblie graphics card(512MB)

Post the following output:
```
top
```

---

### Post by Azakus on 2008-03-07
The nvidia proprietary driver may not have good support for your card ( the driver is usually old, and might need to be updated by the time the version of Ubuntu is released).

---

### Post by RyanZec on 2008-03-07
its wierd i disabled the restricted driver reenabled it activated compiz and now it seems to be working fine, wierd.  I'll have to keep an eye on it i guess.

it is starting to act slow only thing i notice from top is that Xorg sometimes jump to like 40-50 % cpu, is that normal?

---

