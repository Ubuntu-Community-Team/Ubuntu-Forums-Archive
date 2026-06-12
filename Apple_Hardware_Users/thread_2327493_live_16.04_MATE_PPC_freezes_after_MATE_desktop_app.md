---
title: "live 16.04 MATE PPC freezes after MATE desktop appears"
date: 2016-06-11
forum: Apple Hardware Users
---

### Post by gsahli on 2016-06-11
PMac MDD/1GHz ATI 9600XT, currently running Debian 8.4 MATE with mesa workarounds.

Trying to install ubuntu 16.04 MATE ppc from live CD.
Boots up, shows normal plymouth "moving dots," then shows normal-looking MATE desktop. Freezes as soon as the welcome greeting window comes up, showing nothing within that window. (I'm expecting some simple slide-show animation within that window - right?)
Can't click on "Install 16.04 MATE" on desktop. While waiting for startup to complete, In the System pull-down in top bar, I can click to show menu, but also can't click on Install 16.04 MATE.

Ideas? Is there an alternate installer image for 16.04 MATE PPC?

---

### Post by gsahli on 2016-06-12
On suggestion of folks in MATE community, used these yaboot options:
live only-ubiquity radeon.agpmode=-1

You also have to modify yaboot.conf with radeon.agpmode=-1.
16.04 MATE ppc works!

---

