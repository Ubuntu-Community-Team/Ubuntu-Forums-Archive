---
title: "IEEE80211 On Breezy"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by salvatore on 2005-09-14
Im not a first time linux user, but am a first time ubuntu user, so in the Beginner Forum I post...

Im attempting to get my Intel Wireless adapter working on my Dell Latitude D600, using Breezy ubuntu with a 2.6.12 kernel.  There's a well written ubuntu [how to](http://ubuntuforums.org/archive/index.php/t-26623.html) relating to the 2.6.10 kernel, and I fail in the same place user jhuff does (missing the gcc-version.sh file when doing a 'make' as root).
Google says there's LOTS on this issue with non .12 kernels, but Ive only found [this](http://lists.debian.org/debian-kernel/2005/08/msg00546.html) referring to the the 2.6.12 build.  That Debian post says "We believe that the bug you reported is fixed in the latest version of linux-2.6", but Im not entirely certain what they're referring to...the latest 2.6 kernel?  Isnt 2.6.12 that latest kernel?

Before I go too far and attempt to roll my own, does anyone have any suggestions or links they can share?

Thanks.

---

### Post by mlomker on 2005-09-14
Did you **apt-get install build-essential**?

My [how-to](http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16) was a bit more terse.

---

### Post by salvatore on 2005-09-14
[QUOTE=mlomker]Did you **apt-get install build-essential**?

My [how-to](http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16) was a bit more terse.[/QUOTE]
 Yes build-essential has been installed.  I'll try your post and report my findings.
Thanks for the quick reply.

---

### Post by salvatore on 2005-09-14
Unfortunately the ieee80211 make command fails with the gcc-version.sh file not found error, even after Ive eliminated references to it throughout the machine.

Is this perhaps a gcc issue instead of an ubuntu or ieee80211 one?

Some more detail:
build-essential is version 11.1
g++ is version 4.3
gcc is version 4:40.1-3

Is it necessary/possible to downgrade gcc to a version which may work with this kernel?

---

### Post by salvatore on 2005-09-15
I was able to get this working by installing gcc 3.4 (sudo apt-get install gcc3.4).

Thanks for your attention mlomker.

---

### Post by mlomker on 2005-09-15
[QUOTE=salvatore]I was able to get this working by installing gcc 3.4 (sudo apt-get install gcc3.4).
[/QUOTE]

Ah, you must be running Breezy.  I think you'll find that most applications do not compile properly with 4.x but yet that's the default in Breezy.

---

### Post by salvatore on 2005-09-15
[QUOTE=mlomker]Ah, you must be running Breezy.  I think you'll find that most applications do not compile properly with 4.x but yet that's the default in Breezy.[/QUOTE]Yes, sorry I mentioned Breezy in my initial post but not on the subsequent ones.

Thanks again for your help.

---

