---
title: "Stuck in Recovery Mode"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by ghoss00 on 2008-01-29
Ok, I can't get Ubuntu AMD64 to run normally, my system keeps locking (the screen goes black and the monitor light goes off -- no more activity).  I can it to launch in recovery mode, then start X.  But I can't get internet, or really do anything.  I have an ATI Radeon X-700 pro SLI card, which I think may be the problem (but I'm not sure). When I launch into X I seem to be in Root but without Root access (not completely sure but was forbidden to activate the network card.  I seem to still have a lot to learn!!

---

### Post by brokenhachi on 2008-01-29
im not a linux or ubuntu genius... but i did figure out that when you boot in recovery mode, it does put you in root and you cant do jack, but if you type "login" they add your name and pw, it lets you access everything.

---

### Post by Law506 on 2008-01-29
Sounds like video problem.  How long have you waited with the no screen?  Sounds like mine, I cannot get my splash to work, monitor goes off and after about 20-30 seconds, depends, then it comes to the desktop.

- So if your not waiting long enough, try waiting a lil bit longer.

does it work with the livecd?

---

### Post by ghoss00 on 2008-01-29
I've let the computer sit for 15 or so minutes while I do something else.  No success.

---

### Post by ghoss00 on 2008-01-29
I have gone and done something else for a while and come back about 10 or 15 minutes later.  No luck!

---

### Post by Law506 on 2008-01-29
alright, definitly not a splash problem or whatever.

When I had Ubuntu 7.04 I had similar problems with it not working at all.  I have a Nvidia 8600GTS and once I went up to 7.10 and used the restricted drivers problems went away.

Does Ubuntu work on the LiveCD?  and have you used Envy yet?

---

### Post by JoshuaRL on 2008-01-29
I agree.  Try Envy, and if that doesn't work than boot into the Live CD.  If everything works, then you've got something to go off of.  TCheck out the xorg.conf.  Either write it down or mount your HD and save a copy there.  Then check what your xorg.conf says different than the Live CD one.

---

