---
title: "upgrading to gutsy question/s......"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-10-12
I have some questions about upgrading to gutsy from fiesty.
today i thought id try and upgrade my system, so i went to the ubuntu site and found the instructions for upgrading, which ive followed and its worked. more or less.
I know that compiz fusion is included with gutsy, and its kind of what my question is about, if ive already got fusion (which i have) what happens when you upgrade ?
i was running emerald and fusion, but at some point in the upgrade emerald has been removed, i had thought i could just install it again through synaptic, but it wont install as one thing it needs cant be installed, so i thought no problem ill just adjust things in compiz and not bother using emerald anymore.
but i cant get the compiz settings manager to run from the system - preferences  menu, i did try and run ccsm in terminal but i got this error - 

/home/username/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/username/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/username/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

im guessing that part of that error is because i was running a custom theme, so when i changed to a standard theme i got this - 

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

am i wrong in thinking its python related ? and does anyone have any ideas on how to fix this ?
apart from this little problem it all works really well.
cheers

---

### Post by tdreyer1 on 2007-10-16
I am having the same problem. I get the following:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by Goliash on 2007-10-18
Unfortunately the same problem after upgrade to Gutsy.

---

### Post by Goliash on 2007-10-18
I figured out the problem. You have to uninstall all compiz packages and install it again. There was some problem about previous installation from another repository - so clean installation can help you.

---

### Post by burgoy on 2007-10-19
same problem.. also did reinstalling but still nothing happened... help pls.. my head aches.. XD

---

### Post by bobpur on 2007-10-19
Do a clean install. I've never had any luck upgrading from a previous version.

                                                              Good Luck.

---

