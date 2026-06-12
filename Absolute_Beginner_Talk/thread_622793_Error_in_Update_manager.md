---
title: "Error in Update manager"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-11-25
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Whilst trying to update as soon as i click install the above error comes up. Can any one tell me how to correct it?

---

### Post by Ub1476 on 2007-11-25
Have you tried to run what it says in the terminal?

```
sudo dpkg --configure -a
```

---

### Post by reesy on 2007-11-25
ye that worked fine thanks

---

