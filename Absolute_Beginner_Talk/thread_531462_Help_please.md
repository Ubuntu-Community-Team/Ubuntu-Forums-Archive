---
title: "Help please"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-21
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I get this error when I try and run the package installer or update client, whats wrong?

---

### Post by Perfect Storm on 2007-08-21
```
sudo dpkg --configure -a
```

Make sure synaptic and/or other applications that use package system is closed,

---

### Post by dljesse on 2007-08-21
I got it, it was wierd first time I ran that command java installer popped up, next time it fixed it.

---

