---
title: "netatalk(fatal!)"
date: 2005-01-09
forum: Apple PPC Users
---

### Post by cutterjohn on 2005-01-09
If you get the unsupported netatalk package to work, let me know. (UBUNTU 4.10 Warty Warthog, dialup NAT enabled via 802.11b)

(I installed the netalk package on an ibook2 g3/500 and had a HARD(non-OOPS) LOCKUP!  Reboot resulted in another HARD non-OOPS lockkup and an extensive guessign game to reboot to an extent that I could UNINSTALL the netatalk package.

VERY VERY BAD


Side note:  monodoc is also EXTREMELY(lockup of app, but not system lock/crash/oops) buggy, but also unsuported.

---

### Post by adamw on 2005-01-26
I haven't seen a direct kernel panic when using netatalk, only when using netatalk and then using Firefox for about an hour (netatalk was loading on boot, I wasn't engaging in any appletalk sessions).  This is with Warty on a Powerbook 1.5ghz.  I will try uninstalling netatalk and see if I have better luck with FireFox.  (I suppose I could get by with just FTP anyways)

---

### Post by adamw on 2005-01-27
Hmmm... After uninstalling netatalk, I am able to run all day without any kernel panics.  Guess that did the trick.  Thanks for the heads up! =D>

---

### Post by adamw on 2005-02-03
Actually, I have just had to reinstall my system due to a failed custom kernel install, and it looks like the kernel panics were largely the result of running software for the first time on a clean system.  netatalk had nothing to do with it.

---

