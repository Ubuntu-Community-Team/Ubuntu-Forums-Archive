---
title: "Laptop freezes upon return from suspend"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by modalrooster on 2007-12-27
I have a ThinkPad R50e running 7.10 Gutsy.  I have set it to suspend automatically after a time interval.  When I try and return it from suspend mode, the machine most often freezes, staying instead as a black screen, or a black screen with some garbage around  the mouse pointer.  Regardless,  I can never regain control of the machine (even Ctrl+Alt+Del is useless) and I must turn the machine off and back on with the power button to regain usage.  I know this topic has come up a few times on these forums, but I have yet to find anything that would help my problem.  Any thoughts?

---

### Post by kregg on 2007-12-27
Do you have compiz-fusion settings running? These are still experimental, and can cause massive problems with suspending. I've had this problem before, and I reinstalled ubuntu (due to boredom and other things, not the acutal problem itself).

Just to be sure, try going to System>Preference>Appearance, going to the "Visual Effects" tab, and select "None" or "Normal". I currently have Normal and have no problems to date *touch wood*.

---

### Post by modalrooster on 2007-12-27
I do have Compiz-fusion running.  I tried both 'Normal' and 'None' for visual effects settings and neither seemed to remediate the problem.

---

### Post by PmDematagoda on 2007-12-27
This is a bug found in Gutsy's kernel, I have the same issue myself.

A bug report concerning this issue has been filed here:-
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387)

---

### Post by bump_ on 2007-12-27
I also have this issue, but I found that if I suspend manually, it will almost always resume fine.

---

