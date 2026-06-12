---
title: "crazy error installing .deb packages"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-09
hello all, once again, i'm having probllmes.

i am tyring to install network manager thorugh .deb installers but i get

Error: Dependency is not satisfiable: libnl1-pre6


PLZ HElP!!!! I can't believe ubuntu is hating me soo much!!!

---

### Post by ajmorris on 2007-03-09
> **gameman12 said:**
> hello all, once again, i'm having probllmes.

i am tyring to install network manager thorugh .deb installers but i get

Error: Dependency is not satisfiable: libnl1-pre6


PLZ HElP!!!! I can't believe ubuntu is hating me soo much!!!

Open a shell and type ```
sudo apt-get install libnl1-pre6
```

This will install the package it requires. Then just try running the .deb file again. Repeat the process for any other dependencies it comes up with.

---

### Post by gameman12 on 2007-03-09
i just tried the command but i get an output of

E: Couldn't find package libnl1-pre6

---

### Post by ajmorris on 2007-03-09
> **gameman12 said:**
> i just tried the command but i get an output of

E: Couldn't find package libnl1-pre6

did you convert this deb package from an RPM with alien? If the repositories do not have this package then you will have to find it elsewhere or find another version of this network package that does not require libnl1-pre6.

Have you tried the "network Manager" package in Synaptic? I am using it with not problems.

---

### Post by gameman12 on 2007-03-09
no, i didn't convert it, i downloaded it like this.

i decided to download it *because *i couldn't get it in synaptic. network manager wasn't in the synaptic.

i have tried installing it with the apt-get command and it returns 

E: couldn't find package network-manger

same when i do that with network-manager-gnome

---

