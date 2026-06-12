---
title: "apt-get and aptitude"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by gantengx on 2007-04-27
What's the difference between apt-get and aptitude? When i see people post code to install stuff sometimes they use apt-get or aptitude... Tried to search on forum and google but still can't find the difference.. :)

---

### Post by Sef on 2007-04-27
aptitude is an updated apt-get.  Aptitude is better because if you uninstall a program with it, then all dependencies that were downloaded with that program will be uninstalled too.  With apt-get that is not true.

---

### Post by aysiu on 2007-04-27
> **Sef said:**
> aptitude is an updated apt-get.  Aptitude is better because if you uninstall a program with it, then all dependencies that were downloaded with that program will be uninstalled too.  With apt-get that is not true.
Well, until Edgy and Feisty--now *apt-get* has *autoremove*, which gets rid of unused dependencies.

---

### Post by gantengx on 2007-04-28
thanks a lot finally i understand it =D

---

### Post by Nythain on 2007-04-28
yeah, since edgy and feisty, apt-get is just as groovy... in fact some have said that its possibly better now to just stick with apt-get instead of aptitude... the main difference is how they manage and handle dependencies, with the most obvious being removing of them when you remove a package... but like said, since edgy and feisty has auto-remove, wich puts it on par with aptitude

---

