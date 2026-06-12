---
title: "Boot problem"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by wormitian on 2007-03-09
I have just upgraded from breezy badger to dapper drake,but on booting it fails to install hardware drivers.  However it continues on its way and eventually seems to work OK!

Is this a common problem and is there anything I can do about it??   This never happened with breezy badger.

---

### Post by Crooksey on 2007-03-09
Maybe you just need more drivers installed, old ones outdated,

---

### Post by oilchangeguy on 2007-03-09
that was a real helpful answer. and you're part of the beginner team????????????
if the computer will load the operating system go to system, admin, device manager. and see what, if anything shows a problem. hopefully automatic updates will address any outdated drivers. and if you've upgraded from one version to another, it's probably best to do a fresh install rather than upgrade.

---

### Post by wormitian on 2007-03-09
thanks.Found device manager.Everything seems to be listed with no obvious problems.But I am not at all sure what I should be looking for!!

---

### Post by dstew on 2007-03-09
What do you mean "fails to install hardware drivers"? Are you seeing a message from the kernel at startup? Sometimes, during kernel loading, if a particular hardware device is not detected, the kernel will not load that driver module, and will tell you so. That is a feature, not a bug. However, it does not tell you about every module that it does load, so it might appear that the only thing happening is failure. The fact that your system runs is evidence of success.

---

### Post by wormitian on 2007-03-09
During boot-up,I get a message at one point early on which says -

"Loading hardware drivers" and after a couple of minutes or so reports  "Failed" and then proceeds to the next stage.  At every stage but this one I get an "OK" report.
I am glad you reckon it is running successfully as I thought being a newcomer that a "fail" was something that I should be concerned about.
It did not fail at this point when running the CD live.

---

