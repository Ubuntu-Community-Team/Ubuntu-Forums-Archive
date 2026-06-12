---
title: "flash player in firefox problem"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-16
im running this:

gprok@gprok-desktop:~$ sudo apt-get install ubuntu-restricted-extras
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
gprok@gprok-desktop:~$ 

it seems that the process was interruped and i must type something in terminal to finish the install but i dont really know what to type at the moment ????


i also got this error in synaptic package manager: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


TIA !!

Gprok

---

### Post by lixy on 2007-06-16
Did you try an install thru automatix2. It went flawless for me and everyone I know.

---

### Post by machoo02 on 2007-06-16
Execute the command that apt-get told you to...```
sudo dpkg --configure -a
```

---

