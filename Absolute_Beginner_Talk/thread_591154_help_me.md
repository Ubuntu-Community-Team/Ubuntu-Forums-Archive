---
title: "help me"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by wuzzums2000 on 2007-10-25
i cant update or download can you tell me what this means ?????????????

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by mali2297 on 2007-10-25
> **wuzzums2000 said:**
> i cant update or download can you tell me what this means ?????????????

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Copy/paste to the terminal:
```

sudo dpkg --configure -a

```

---

### Post by taurus on 2007-10-25
Close synaptic if you still have it open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

