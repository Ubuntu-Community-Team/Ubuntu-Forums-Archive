---
title: "sdb1 not accessible??"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-06-30
During a reboot, Ubuntu 7.04 displayed a message stating that hda3 had been accessed 23 times . . . . check forced.  Something like that.  I've seen it before - the number of accesses that triggers this check seems to be random - sometimes more accesses, rarely less.

Anyhow, the test usually goes without a hitch as all the items checked pass.

Today, there was one test that failed.  The message stated that sdb1 was not accessible, and the word 'fail' appeared in red at the right of the screen instead of pass.

The test continued to completion, and the machine booted and operates normally.

sdb1, when I explore it, turns out to contain my / partition, and that "drive" shows up as empty.  It is certainly accessible.  The machine operates normally - as it always has.

Is this something I need to be concerned about?

Thanks for any advice.

Caruso

---

### Post by eljalill on 2007-06-30
You should first check, whether the same message comes up, when you restart. The "fail" might come from sdb1 not having been unmounted correctly for various reasons, and if that's the case and you can access it now, everything should be fine upon reboot.

---

### Post by carusoswi on 2007-06-30
Thanks for the reply.  Actually, right after that forced check, everything seemed to be working just fine.  Reboots have been fine, also.  I was just surprised that my '/' would show up as non-accessible.

Ubuntu has become my OS of preference.  It always runs smoothly, I can browse without constant interuptions to update this, protect that, etc.

It  is the bees' knees.

Caruso

---

