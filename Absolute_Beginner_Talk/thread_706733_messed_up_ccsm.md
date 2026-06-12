---
title: "messed up ccsm"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by JParkus on 2008-02-24
parkus@ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

I was tryn to get kiba dock working and trevinos repo compiz plugins did this (and on top of that kiba wasnt in the repo )

---

### Post by macogw on 2008-02-24
Try uninstalling Compiz all the way and removing Trevino's repo, then reinstall Compiz from the official repos.

AWN's a bit nicer (more usable, less crashy) than Kiba, by the way.

---

### Post by JParkus on 2008-02-24
I'll try it 
I like AWN but I want it on the left of the screen instead of the bottom if theres a way to do that now ill switch back

---

