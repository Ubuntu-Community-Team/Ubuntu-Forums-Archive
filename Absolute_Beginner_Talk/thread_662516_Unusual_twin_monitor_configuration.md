---
title: "Unusual twin monitor configuration"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ralphz on 2008-01-09
Hi I have two monitors acer al2223W and Samsung SyncMaster 204t. Samsung has pivot capabilities. 

Both monitors work perfectly fine with with tween view but I have really hard time to make acer to display in landscape mode as a primary monitor and Samsung in portrait mode. I want to use acer to write code and Samsung to open some documentation (it's easer to reed long pages in portrait mode)

When I use command: 

```
xrandr -o left
```

it turns view on both monitors. Is there a way to turn view only on one of them?

My configuration:

GeForce 7600 GT, Gusty Gibbon.

---

### Post by CatKiller on 2008-01-09
**man xrandr** suggests *--output <output>* or *-screen _snum_* as possibilities. I'm unclear as to what the differences are between them.

---

