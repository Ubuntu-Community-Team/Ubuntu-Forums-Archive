---
title: "KDE with XGL font &amp; compiling error."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-28
Ok, i've decided to try using KDE with XGL I have it installed but immediately into a problem

when compiling software (I was tring to compile kxdocker I got an error saying this: 

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I am in a sperate XGL session running KDE and have no idea what to do! I tried to compile by downloading to desktop, extracting and doing ./configure

Calv

Calv

---

### Post by calvinthomas on 2006-09-28
Fixed, missing packages installed KDElibs-dev

---

### Post by pay on 2006-09-28
I find that sudo apt-get build-dep <package> (where <package> is the program that you want to compile) helps me to make sure that I have all the dependencies needed for compilling. Aslong as you have the dep-src activated in your sources.list for that program.

---

