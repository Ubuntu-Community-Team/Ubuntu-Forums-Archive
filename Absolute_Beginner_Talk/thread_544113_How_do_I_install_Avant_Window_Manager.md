---
title: "How do I install Avant Window Manager"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-09-05
Yes i no this is a stupid one to ask but I can't figure out how to install it.

---

### Post by santiagoward2000 on 2007-09-05
Hi Jonward690:
Here's a link to a how-to: [http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")
I hope it helps!

---

### Post by PurposeOfReason on 2007-09-05
There are actually a few "bzr" versions of AWN now.

Awn-curves
awn-effects
awn-effects 2 (forgot the real name)
regular awn

Say which one you want and I'll point you in the right direction.

---

### Post by jonward690 on 2007-09-05
Well all I want is the awn dock that is it man.

---

### Post by PurposeOfReason on 2007-09-06
Then the how to will work fine. Some people just want a curved dock or extra effects on the icons.

---

### Post by GMarx on 2007-09-07
PurposeOfReason how do you install awn-curves and awn-effects?

---

### Post by PurposeOfReason on 2007-09-07
**Curves**
$ bzr co [http://bazaar.launchpad.net/~meek./awn/awn-curves](http://bazaar.launchpad.net/~meek./awn/awn-curves) awn-curves
$ cd awn-curves
$ ./autogen.sh && make && sudo make install

**Effects**
$ bzr co [http://bazaar.launchpad.net/~mhr3/awn/libawn-effects](http://bazaar.launchpad.net/~mhr3/awn/libawn-effects) libawn-effects
$ cd libawn-effects
$ ./autogen.sh
$ make
$ sudo make install

---

