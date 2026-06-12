---
title: "I can't adept it won't apply changes."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-09-26
I'm trying to install sun java so I can run frostwire but when I start up adept package manger. It tells me.
```

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```
But I can't figure out what is running the packaging system database. I've looked at what the 
```
top
```
command out puts but I don't see anything. And I've tried turning my Computer off by shutting down and holding down the power button. Nethere way worked.
I can't get it to not say that when I start add or remove or adept. 
Any Help.

---

### Post by Linux_Man on 2007-09-26
Try just sudo apt-get install *insert name of random program* to test it, also try opening synaptic and add/remove programs to see what error messages those make.

---

### Post by Pumalite on 2007-09-26
Do not have Synaptic open while running apt-get.

---

### Post by microsoft92sucks on 2007-09-26
I got this when I open Synaptic.
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```
I have Kubuntu and Ubuntu installed so I have Aptic and Synaptic. So what should I do run 
```
dpkg --configure -a
``` in the terminal.

---

### Post by Pumalite on 2007-09-26
At the Terminal:
sudo dpkg --configure -a

---

### Post by microsoft92sucks on 2007-09-26
ok I got it working thanks for the help.

---

