---
title: "Can't update"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Captain CutLess on 2008-04-08
Whenever I try to update my software at Update Manager, I always get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by scragar on 2008-04-08
open a terminal ( Applications > Accessories > Terminal ), and run```
sudo dpkg --configure -a
```it will prompt for your password, enter it, then wait for it to finish. Once it has you will be free to install things again(although it's recomended you run```
sudo apt-get install -f
```to fix any broken packages as well).

---

### Post by Captain CutLess on 2008-04-08
Thanks so much!

---

