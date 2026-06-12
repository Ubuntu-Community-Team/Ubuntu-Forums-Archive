---
title: "Ybin after canonical kernel upgrade?"
date: 2008-02-05
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-05
After today's ppc kernel upgrade from Canonical to 2.6.20-16, I noticed that my mouse was a little jerky.

I'm running stock canonical-supplied kernels, BUT I have modified my yaboot.conf file to allow for a clean splash screen.

Immediately after the upgrade, everything looked good, even the splash, but the mouse was a little hesitant.  I checked the kernel with uname -a and the system is running the latest update.

So, barely awake, I just applied a sudo ybin -v to yaboot.conf, rebooted, and the mouse is doing fine again.

So is doing a ybin -v after a kernel upgrade a wise thing to do every time there is an upgrade?  My modified yaboot.conf wasn't changed by the upgrade, and the previously modified splash looked fine, but it cured a new mouse problem?

Puzzled....

---

