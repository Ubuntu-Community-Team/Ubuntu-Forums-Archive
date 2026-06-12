---
title: "synaptic package manager"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-26
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

this is the message i get when i start synaptic package manager and when i try to update

i have installed ubuntu,and use kubuntu desktop 

what can i do ? :confused:

---

### Post by Dark Star on 2007-08-26
```
sudo dpkg --configure -a
sudo apt-get install -f 
```
This  will help :)

---

### Post by nikef on 2007-08-26
thanks for the fast reply
will try that :)

---

### Post by nikef on 2007-08-26
Its not working ,this is what i get 

trish@trish-desktop:~$ sudo dpkg --configure -a
trish@trish-desktop:~$ sudo install -f
install: invalid option -- f
Try `install --help' for more information.

---

### Post by Dark Star on 2007-08-26
1'st enter ```
sudo dpkg --configure -a
``` Then hit enter . .After that type ```
sudo apt-get install -f
```

---

### Post by nikef on 2007-08-26
sorry it has worked

synaptic package manager and update manager is now working

many thanks :)

---

### Post by Dark Star on 2007-08-26
> **nikef said:**
> sorry it has worked

synaptic package manager and update manager is now working

many thanks :)
My pleasure :)

---

