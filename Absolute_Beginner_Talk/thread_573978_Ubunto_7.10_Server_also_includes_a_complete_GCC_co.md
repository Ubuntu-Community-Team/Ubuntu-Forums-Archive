---
title: "Ubunto 7.10 Server also includes a complete GCC compiler ?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-12
I need a linux server for scool lessons.Ubuntu 7.10 GG is ok ?

i Also need a complete gcc compiler (with dependencies, libreries to compile everithing ).

wHAT other linux distribution (SERVER) can you racomand me ?

---

### Post by taurus on 2007-10-12
If you want to install GCC compiler, just install it with

```
sudo aptitude update
sudo aptitude install build-essential
```
That's all you have to do.

---

### Post by bambubambu2 on 2007-10-12
without internet connexion can gCC  be installed ?
i MEAN ONLY WITH live cd.
I really need the Reposytories ?

---

### Post by taurus on 2007-10-12
Build-essential is on the LiveCD.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

