---
title: "Compiz broke after update. (I've got output data)"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-17
Updated my ubuntu and compiz broke. Here's the output of "ccsm" and "compiz" in the terminal. WTF is wrong? I've got a nVidia 8600m GS


```

felix@felix-ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
felix@felix-ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0425 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by Kingsley on 2007-10-17
Is dis with an Nvidia ca'd on Gutsy?

---

### Post by Lozz on 2007-10-18
What version of compizconfig-settings-manager do have installed? Is this on feisty or gutsy? I ask because I had a similar problem a few days ago in gutsy.

---

