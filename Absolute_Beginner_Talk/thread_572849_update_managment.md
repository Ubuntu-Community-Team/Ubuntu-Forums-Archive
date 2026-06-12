---
title: "update managment"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by mg6730 on 2007-10-10
When I try to install the updates and error occures.
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
After attempting to manually run the listed fix to correct the problem, it does nothing and it still wont allow me to install the updates.
Does anyone know what this error is and how to fix it, so I can install the updates?

---

### Post by rsambuca on 2007-10-10
Open a terminal and enter```
sudo dpkg --configure -a
```

---

### Post by Dr Small on 2007-10-10
Did you run the following ?
```
sudo dpkg --configure -a
```

---

