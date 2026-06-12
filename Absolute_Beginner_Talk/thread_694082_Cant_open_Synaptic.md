---
title: "Cant open Synaptic"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by ronb94 on 2008-02-11
I got this when I tried to open synaptic or run an apt-get.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
Thanks

---

### Post by taurus on 2008-02-11
Close synaptic if you have it open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

