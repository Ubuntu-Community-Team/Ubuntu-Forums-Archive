---
title: "help trying to update"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by shane203 on 2008-01-22
im not to shur what happened but i was trying to install limewire and it locked up not to shur what i did but now i try and update and it gives me this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
shane@shane-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
shane@shane-desktop:~$

---

### Post by tojge on 2008-01-22
Try ```
**sudo** dpkg --configure -a
```

---

