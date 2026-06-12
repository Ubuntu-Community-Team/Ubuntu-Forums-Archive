---
title: "The Mana World 0.21"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Baochan on 2006-10-12
I add this repositories:

#The Mana World
deb [http://bertram.ifrance.com](http://bertram.ifrance.com) ./
deb-src [http://bertram.ifrance.com](http://bertram.ifrance.com) ./

but when I try to install tmw, I have this problem with those dependecies: 

tmw:
  Dipende: libc6 (>=2.3.6-6) ma 2.3.6-0ubuntu20 verrà installato
  Dipende: libcurl3-gnutls (>=7.15.5-1) ma 7.15.1-1ubuntu2 verrà installato
  Dipende: libgcc1 (>=1:4.1.1-12) ma 1:4.0.3-1ubuntu5 verrà installato
 Dipende: libgnutls13 (>=1.4.0-0) but it is not installable
 Dipende: libguichan0 ma non sta per essere installato
  Dipende: libsdl-image1.2 (>=1.2.5) ma 1.2.4-1 verrà installato
  Dipende: libsdl1.2debian (>=1.2.10-1) ma 1.2.9-0.0ubuntu2 verrà installato
  Dipende: libstdc++6 (>=4.1.1-12) ma 4.0.3-1ubuntu5 verrà installato
  Dipende: libxml2 (>=2.6.26) ma 2.6.24.dfsg-1ubuntu1 verrà installato
 Dipende: tmw-data ma non sta per essere installato

How can I resolve this problem?

---

### Post by PriceChild on 2006-10-12
This is what happens when you use 3rd party repos.

You will need to find soemwhere to get the updated packages from.

---

### Post by andnobodyslept on 2006-10-13
The problem most of the time is with Guichan, the Ubuntu repos have the old version. Use this thread to get it to work...or at least that is what I did.
[http://www.ubuntuforums.org/showthread.php?t=235525&page=3&highlight=the+mana+world]("http://www.ubuntuforums.org/showthread.php?t=235525&page=3&highlight=the+mana+world")

---

