---
title: "Synaptic Package Manager error"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Nezing on 2007-06-05
When I try to access Synaptic,I keep getting this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

How do I do the above?:redface:

---

### Post by taurus on 2007-06-05
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by Nezing on 2007-06-05
Cheers taurus.Problem solved very quick.:popcorn:

---

