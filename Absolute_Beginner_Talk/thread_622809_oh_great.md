---
title: "oh great"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-25
so I was trying out kiba dock and I install some stuff to get it to work, then it updated my ccsm, which when i try to open gives me this:

nathan@fresh:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


any ideas on how to fix this? thanx. i don't like docks anymore.

sv

---

### Post by GavinZac on 2007-11-25
again, i think this is a Desktop Effects & Customisation thread.

not sure where to start but if worst comes to worst, purge the compiz settings manager and reinstall

---

### Post by staticvoid on 2007-11-25
I think I'll have to. Thanks GavinZac.

sv

---

