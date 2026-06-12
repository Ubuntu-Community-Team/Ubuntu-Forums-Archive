---
title: "[SOLVED] Open Office on Xubuntu"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-16
hello there,

could anyone please tell me what's the safest way of installing Open Office on Xubuntu Gutsy?

Many thanks!!!

---

### Post by Ub1476 on 2008-03-16
I don't use Xubuntu, but I guess it's in the package manager? 

```
sudo apt-get install openoffice-base
```

If Synaptic is installed on Xubuntu, you might search for it through there

---

### Post by al.adab on 2008-03-16
It didn't work on terminal:

~$ sudo apt-get install openoffice-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice-base

Any idea? Is it safe to install it through Synaptics?

---

### Post by Ub1476 on 2008-03-16
Synaptic is just a GUI for "apt-get". So yes, it's very safe. The reason it couldn't install was because I forgot the name of the OOo package.. I haven't used Debian repos for a couple months..](*,)

Package name might have been "openoffice-core", but searching for Open-Office in Synaptic will do better.

---

### Post by ghost_ryder35 on 2008-03-16
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.1)

---

