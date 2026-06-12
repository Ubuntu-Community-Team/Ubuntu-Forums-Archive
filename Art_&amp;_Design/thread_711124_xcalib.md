---
title: "xcalib"
date: 2008-02-29
forum: Art &amp; Design
---

### Post by jtclicker on 2008-02-29
I'm using Xcalib to load a windows created profile. Is there any way of running the 'xcalib path to profile' at boot rather than in Terminal every time I boot up or switch user?

---

### Post by jtclicker on 2008-03-01
Joel, in his excellent blog, came me an answer to this newbie problem...
There is a simple solution to do what you need. I’ll try to do a step-by-step howto :)

1) open your text editor
2) type in
#!/bin/bash
xcalib /path/to/your/icc_profile.icc
3) save this file as loadicc.sh
4) right click on it, under properties / permission, tick “allow executing file as program”
5) Open System/Preferences/Sessions
6) Chose add
7) Name: load icc profile, command / browse to your loadicc.sh file
8 ) Make sure the new entry is ticked

This will allow you to load your monitor profile on login. There is a problem however with gnome screensaver that removes the profile when it activates. Simple solution: don’t use a screen saver. Better solution: check here and here for a script to circumvent the problem. Note also that clicking on the loadicc.sh file and choosing “run” will load your monitor profile.

Hope this helps. Take care,

Joël

wonderful

Thanks Joel

Julian

---

