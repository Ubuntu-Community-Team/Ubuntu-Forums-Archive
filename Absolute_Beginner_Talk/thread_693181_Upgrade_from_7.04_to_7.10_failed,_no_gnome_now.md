---
title: "Upgrade from 7.04 to 7.10 failed, no gnome now"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Lderan on 2008-02-10
I tried to upgrade from 7.04 to 7.10 mainly out of boredom but it crashed, it came up with some error saying "this program has failed to close, close now?" and that went on a couple of times and then the upgrade program disappeared. I tried rebooting, but nothing appeared but my background, no toolbars or anything. 

I have no idea what is going on, can anyone please help?!

I can get firefox and the media player to load and I hear sounds from the IM program so its just the desktop that is missing.

---

### Post by PmDematagoda on 2008-02-10
Boot Ubuntu in Recovery Mode and execute:-
```
dpkg --configure -a
```
and
```
apt-get install -f
```
see if that solves your problem.

---

### Post by Lderan on 2008-02-10
Thankyou soooo much PmDematagoda =D

hmmm I can't turn on desktop-effects, it says it doesn't exist and i can't install it through synaptic.
how very strange

---

