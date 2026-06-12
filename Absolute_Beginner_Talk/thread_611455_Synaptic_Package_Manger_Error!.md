---
title: "Synaptic Package Manger Error!"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-13
When I open Synaptic I get this:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by FuturePilot on 2007-11-13
Open a terminal and try
```
sudo dpkg --configure -a
```

---

### Post by rudeboyskunk on 2007-11-13
then, after running that command, run these two:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

