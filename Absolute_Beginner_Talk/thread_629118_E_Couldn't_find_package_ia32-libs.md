---
title: "E: Couldn't find package ia32-libs"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by sadistikal on 2007-12-02
why i always end up here "E: Couldn't find package ****" everytime i install something using terminal window...  could you please enlighten me further about this problem?

---

### Post by PriceChild on 2007-12-02
*moves approves and bumps*

---

### Post by ruibernardo on 2007-12-02
Hi sadistikal,

that package is available on the universe repository only if you have ubuntu for 64 bit architecture/kernel (aka amd64, but it is for all 64 bits PC).

Are you trying to install it on a 32 bit system? Did you install ubuntu for 64 bits or the normal one (i386)? Do you have the universe repository enabled?

---

### Post by sadistikal on 2008-01-06
tnx sir epitemio for enlightening me about my problem.... problem solved!!!

---

### Post by boombox1387 on 2008-02-21
I'm having the same problem.  I'm trying to install ia32-libs and others so that I can eventually run 32-bit Firefox.  I have universe enabled and I'm pretty sure I'm running 64-bit gutsy on an AMD64 processor.

I found instructions [here]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins"), but when I try to run 

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

i get:

E: Couldn't find package ia32-libs

Any help would be appreciated

---

