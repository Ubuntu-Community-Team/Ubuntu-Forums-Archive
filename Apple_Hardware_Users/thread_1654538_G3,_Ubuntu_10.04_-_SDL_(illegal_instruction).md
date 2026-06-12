---
title: "G3, Ubuntu 10.04 - SDL (illegal instruction)"
date: 2010-12-28
forum: Apple Hardware Users
---

### Post by Ksiazkowicz on 2010-12-28
Hi.
Everytime I try to run app, that requires SDL, it crashes with "Illegal instruction". Actually, someone had this problem some time ago, but there is no possibility of installing fixed packages (they are just... too old!).

What can I do, except of moving back to OS X?

---

### Post by biobunny on 2010-12-28
I thought that the iMac g3 was PowerPC and that you couldn't install Ubuntu 10.10 on it.

---

### Post by Ksiazkowicz on 2010-12-28
There is Ubuntu 10.10 for PowerPC. I tried to upgrade from Lucid, but system is actually dying. ALSA not working properly, Calculator crashing with Illegal instruction...

---

### Post by linuxopjemac on 2010-12-29
I would install MintPPC, which has active support in MintPPC's own forums. The user base is growing steadily and people seem to be enjoying it a lot. It's not as polished as Ubuntu, but it runs a lot faster and smoother.

---

### Post by Ksiazkowicz on 2010-12-29
I don't know, why should I move. Does it have better support for PowerPC than Ubuntu? I know that Yellow Dog Linux has - but it's RPM based. 
Still, I don't have time for making backups, burning CD's...

I can't find anywhere about "why MintPPC is better than my configured Ubuntu". Give me a reason to move, tell what works better.

---
I've actually managed to use those Debian packages I've found, to fix libSDL. For everyone that has PowerPC without AltiVec (pre-G4) and are about to give up on Ubuntu or just... destroy their PowerMacs (maybe setting them on fire or put in bathub full of water and connect it to 220v power source), there are fixed libraries here:
[http://ubuntuone.com/p/VlL/](http://ubuntuone.com/p/VlL/)
Extract it to /usr/lib (you can backup original files if you want to)

That's all, SDL should be working.

---

