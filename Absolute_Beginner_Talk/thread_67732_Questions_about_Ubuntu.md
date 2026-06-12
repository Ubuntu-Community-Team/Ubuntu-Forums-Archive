---
title: "Questions about Ubuntu"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Etheric on 2005-09-21
Im told Ubunto is compiled with P4 instructions and not i386/i386.... Is this true? As I run an XP 2200+ and I Dont want to install. 

Im currently a SUSE user and I dont like the performance, Im told Ubuntu is very fast... I wish there was a version precompiled for athlonXP but ill make due if this rumor i was told is incorrect

-Etheric

---

### Post by az on 2005-09-21
Basically, it will run fine.  It installs with a 386 kernel which runs on everything.  The user can then install a 686 kernel if they run an intel cpu, or they can install a k7 kernel if they run AMD.  That will optimise your performance accordingly.

So, install normally and then, once you are up and runnning, install the linux-image-686 package, just like any other package.

---

