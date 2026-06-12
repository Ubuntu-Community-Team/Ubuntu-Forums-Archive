---
title: "Updates"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by dben on 2008-02-16
While trying to update I received the following messageafter trying to install updates:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/I]
Cutting the phrase to the terminal screen gives the following:

*dpkg: requested operation requires superuser privilege*

Need help.

dben

---

### Post by jan quark on 2008-02-16
```
sudo dpkg --configure -a
```

try now

---

### Post by dben on 2008-02-16
thanks

dben

---

