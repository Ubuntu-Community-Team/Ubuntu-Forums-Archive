---
title: "help on new patch"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by hitspace on 2008-02-25
the new patch fix is not working it downloads but when i try to install the patch program says error and that i need to do it manually 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



any possible fixes . i already tried putting the mentioned line into terminal . it tells me i need administrative prev. i tried keying in my password it didnt work .

---

### Post by PeterJS on 2008-02-25
Give running:
```

sudo dpkg --configure -a

```
another go. When the password prompt comes up enter your password, you're not going to get any visual feed back, that's normal, and let us know how that goes.

---

### Post by SOULRiDER on 2008-02-25
After that its not a bad idea to do
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

