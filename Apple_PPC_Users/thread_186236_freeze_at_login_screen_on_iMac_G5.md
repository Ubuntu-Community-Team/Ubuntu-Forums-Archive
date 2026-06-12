---
title: "freeze at login screen on iMac G5"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by n.b.r. on 2006-06-01
I have an iMac G5, and just installed Ubuntu 6.06. I had to use the alternate install cd, because my machine locked up every time the GUI started to load on the live cd.
The install went fine. When I boot Ubuntu, the splash screen is discolored - not a big deal to me, just thought I would mention it. When GDM  is loading, it is responsive for a brief moment, and the promptly freezes.
I tried swithcing to tty1 during boot. The following step failed:
```
* Starting pbbuttonsd
ERROR: The file '/dev/pmu' doesn't exist.
```
and later, where the GUI freezes, and it stops accepting mouse & keyboard input:
```
*Starting periodic command scheduler...
[ 121.599900] atat1: command 0x25 timeout, stat 0x50 host_stat 0x4
[ 151.932943] mpic_enable_irq timeout
```
and variations of the last two lines slowly repeat.

---

