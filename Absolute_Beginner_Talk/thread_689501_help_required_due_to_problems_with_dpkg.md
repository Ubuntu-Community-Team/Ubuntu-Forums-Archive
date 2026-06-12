---
title: "help required due to problems with dpkg"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by fredsa on 2008-02-06
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
please can you advise thank you:(

---

### Post by shad0w_walker on 2008-02-06
You need to open up a terminal (Applications > Accessories > Terminal) and then run this command

```
sudo dpkg --configure -a
```

That should fix your problem.

---

