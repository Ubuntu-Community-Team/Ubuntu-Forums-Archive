---
title: "update manager problem"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by nicholas mccarthy on 2008-03-09
hi,

i tried to install the new updates, and when it tried to install them, it came up with this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so, i put that into the teminal, and this is what came up:

stephen@Stephen:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


so, i dont know what to do now. any suggestions? thanks

---

### Post by taurus on 2008-03-09
Put a sudo in front of that command.

```
**sudo** dpkg --configure -a
sudo apt-get update
```

---

### Post by adult swim on 2008-03-09
try to run 
```
sudo dpkg --configure -a
```
sudo gives you the superuser privelelge
edit: i was too slow!

---

### Post by nicholas mccarthy on 2008-03-09
thanks! i think its working now

---

