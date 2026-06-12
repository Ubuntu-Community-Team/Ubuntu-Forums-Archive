---
title: "help-synaptic package manager"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-12
every time I start synaptic package manager it says


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I do?

---

### Post by taurus on 2007-05-12
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by heimo on 2007-05-12
> **sethdotcom said:**
> every time I start synaptic package manager it says


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I do?

First thing for me in such situation is to run:
```
sudo dpkg --configure -a
```

However, sometimes it's not enough.

---

### Post by sethdotcom on 2007-05-12
It worked Thanks.

---

### Post by heimo on 2007-05-12
Try removing it.
```
sudo apt-get --purge remove acroread
```

Any errors?

---

