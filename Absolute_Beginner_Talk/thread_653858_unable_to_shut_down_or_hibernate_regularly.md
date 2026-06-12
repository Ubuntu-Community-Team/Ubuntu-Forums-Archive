---
title: "unable to shut down or hibernate regularly"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by raharris on 2007-12-30
Dell Inspiron 700m running both XP and Gutsy Gibbon/Gnome

From the suspend/hibernate/shutdown gui interface GG will only suspend, hibernate, or shut down maybe a third of the time.  The rest of the time I get nothing but a black screen and the computer stays on.  I've also tried using:
su halt
from the terminal, to the same effect.  Any help appreciated.
RA Harris

---

### Post by Bufke on 2007-12-30
You might have the problem in this bug report, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308")

There appears to be some work-arounds there.  Hope that helps!

---

### Post by raharris on 2007-12-31
Right on!

I added the line:
apm power_off=1
to:
/etc/modules

and the problem seems to be solved.

Thank you, Bufke

RA Harris

---

