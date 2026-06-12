---
title: "Help!!!!"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by watsgoodg on 2008-03-06
Error when opening Synaptic..."E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."  

I ran dpkg --configure -a" and it says super user rights are needed?

---

### Post by watsgoodg on 2008-03-06
dpkg: requested operation requires superuser privilege

---

### Post by chewearn on 2008-03-06
Add "sudo" before the command to get root privilege, like this:
```
sudo dpkg --configure -a
```

---

### Post by taurus on 2008-03-06
```
**sudo** dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by watsgoodg on 2008-03-06
Thanks for the fast reply i can now close this threat out.

---

