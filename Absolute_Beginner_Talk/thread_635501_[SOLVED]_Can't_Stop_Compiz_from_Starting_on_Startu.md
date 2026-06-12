---
title: "[SOLVED] Can't Stop Compiz from Starting on Startup"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by dunomous on 2007-12-08
I've recently had problems with Compiz. In trying to make fixes (as all problems start) Compiz now starts on startup as I previously did not have it doing.. I've gone to Sessions to see all startup programs, but it's not there. This is particularly annoying since it eats up 100% of my processor (it's a real mess, I'm starting to really hate Compiz). What are my options on killing this startup?

---

### Post by Crashmaxx on 2007-12-08
Is this on Gutsy or Feisty? Gutsy doesn't have a startup command, instead you need to go into System>Preferences>Appearance and go to the Visual Effects tab and check None.

For Feisty you it may be called Advanced Effects or the like and you'd need to turn off any effect there.

If all else fails, just remove Compiz, assuming you don't want to use it. You can do that a number of ways, but just removing the compiz package should take away the rest too.

---

### Post by AndyCooll on 2007-12-08
System > Preferences > Appearance.

Select the visual effects tab and choose "None".

:cool:

---

### Post by dunomous on 2007-12-08
> **Crashmaxx said:**
> Is this on Gutsy or Feisty? Gutsy doesn't have a startup command, instead you need to go into System>Preferences>Appearance and go to the Visual Effects tab and check None.

For Feisty you it may be called Advanced Effects or the like and you'd need to turn off any effect there.

If all else fails, just remove Compiz, assuming you don't want to use it. You can do that a number of ways, but just removing the compiz package should take away the rest too.

This is on Feisty. I tried removing the Compiz package (it's the git packages), still, even upon reboot, the compiz and the compiz.real processes are running, taking up 100% of the processor.

---

### Post by Hospadar on 2007-12-08
worst case scenario, just remove it with synaptic.  That'll stop if from starting!

note that the main compiz package is probably just a dummy package to get all of the components of compiz installed, try removing every package with compiz in the name.

Also, if you are trying to set up a new (or recent) install, why not just switch to gutsy?

---

### Post by dunomous on 2007-12-08
> **Hospadar said:**
> worst case scenario, just remove it with synaptic.  That'll stop if from starting!

note that the main compiz package is probably just a dummy package to get all of the components of compiz installed, try removing every package with compiz in the name.

Also, if you are trying to set up a new (or recent) install, why not just switch to gutsy?

I suppose I'll have to try and remove every single package next, but it seems like by removing the main one only, it broke many things. Emerald won't run, for instance.

I've been trying to put off upgrading to Gutsy as it is very time consuming and this is exam period.

---

### Post by technoidiot on 2007-12-08
To remove compiz and beryl/emerald. Open a terminal and type in the following code

sudo apt-get remove compiz* && sudo apt-get autoremove

then:

sudo apt-get remove beryl* emerald* && sudo apt-get autoremove

The only reason I know about this is i too tried compiz and didn't like its results. Couldn't seem to get all settings to work.

---

### Post by dunomous on 2007-12-08
I really appreciate everyone's help! The solution was just simply removing all compiz related packages and restarting. The ccsm issue is related to python problems, but that's fine. All has returned to normal.

---

### Post by nikoPSK on 2007-12-08
please mark this thread as "SOLVED". :D

---

### Post by dunomous on 2007-12-09
Ah, sorry about that. I had thought I did.

---

### Post by nikoPSK on 2007-12-09
[LEFT]that's fine, it just helps us people on the beginner team. We skip the threads that are "SOLVED".
[/LEFT]

---

