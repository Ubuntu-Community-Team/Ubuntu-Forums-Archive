---
title: "File will Not patch"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by gymophett on 2008-04-07
Ok, Im a real noob, Just got ubuntu last night. Im having the hardest time ever installing my wireless card or configuring or whatever. Ok, im using madwifi, and im trying to patch my file, but idk which file im supposed to patch. Heres whats happening in my terminal:

gavin@gavin-laptop:~/madwifi$ patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur old-hal/ah.h hal/ah.h
|--- old-hal/ah.h       2007-12-03 16:16:56.000000000 -0800
|+++ hal/ah.h   2007-12-03 16:16:01.000000000 -0800
--------------------------
File to patch: 



....


idk what file to patch.. help!!

Im currently following this guide: [http://ubuntuforums.org/showthread.php?t=680209](http://ubuntuforums.org/showthread.php?t=680209)

---

### Post by canthus13 on 2008-04-07
Umm.. What wireless card are you using?  You may just need to enable the restricted drivers for it.  Go to systrm > administration > Restricted drivers and enable restricted drivers.

--Me

---

### Post by gymophett on 2008-04-07
> **canthus13 said:**
> Umm.. What wireless card are you using?  You may just need to enable the restricted drivers for it.  Go to systrm > administration > Restricted drivers and enable restricted drivers.

--Me

Im using Atheros Communications, Inc. AR5006EG... Ive already tried that, didnt work..

---

