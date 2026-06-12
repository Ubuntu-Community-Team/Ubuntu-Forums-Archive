---
title: "genie effect"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-06
Hi,

Srry for repeating the thread. 

But how can i install and then enable the mac os x's genie minimizing effect? and btw I use compiz and somehow i can't seem to be able to run the compiz config setting. I mean if I click on the compiz settings option, it just doesn't respond to my double clicking. 

Thnx

---

### Post by tlages on 2007-11-06
I also would like this, I love macs animation scheme.

---

### Post by jordanmthomas on 2007-11-06
To get the genie effect to be just like OSX's you have to edit the compiz source and compile it yourself.  (In animation.c, you have to change a certain value to zero.  I won't say which since it's not zero for legal reasons as it is)

Then, in the compiz options, enable the animations plugin and use the magic lamp animation.

(to run the compiz configuration program, just run ccsm from a terminal and see what happens)

---

### Post by limac on 2007-11-06
This is what ccsm says:

limac@limac-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by jordanmthomas on 2007-11-06
I'm unfamiliar with the packages for Ubuntu since I use Arch, but I'd figure you need to install libcompizconfig.

---

### Post by Kevuntu on 2008-01-02
You probably mixed repos in your sources.list
Here: [http://ubuntuforums.org/showthread.php?p=4030543](http://ubuntuforums.org/showthread.php?p=4030543)

---

