---
title: "[SOLVED] Synaptic error (dpkg)"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by And1945 on 2007-11-29
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What to do about this? :(

---

### Post by Dr Small on 2007-11-29
In your terminal, run:
```
sudo dpkg --configure -a
```

---

### Post by And1945 on 2007-11-29
> **Dr Small said:**
> In your terminal, run:
```
sudo dpkg --configure -a
```

Okay, I am doing that now. Does that reconfigure files?

Perhaps my synaptic got corrupted some way...

EDIT: It works now, thank you very much :)

---

