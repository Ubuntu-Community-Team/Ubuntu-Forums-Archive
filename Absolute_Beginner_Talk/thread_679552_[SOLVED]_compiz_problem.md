---
title: "[SOLVED] compiz problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-01-27
i installed compiz using this guide: [http://http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty]("http://http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

and this is what i get in the terminal when i run "compiz --replace"

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Window manager warning: Screen 0 on display ":0.0" already has a window manager


can someone help? i noticed that it says less than blah blah memory, so does that mean i cant use compiz with my video card? i use a GeFroce FX GO5200

---

### Post by swoll1980 on 2008-01-27
do you have the nvidia drivers installed you have 64mb memory card detected that should work

---

### Post by brokenhachi on 2008-01-27
i used envy to install the drivers and it seems like that worked.. it did say installed when it finished and asked me if i want to edit the xorg.conf and i said yes. and now i have an nvidia settings manager that says my driver version is 169.09

---

### Post by swoll1980 on 2008-01-27
what OS are you using

---

### Post by brokenhachi on 2008-01-27
ubuntu 7.10

---

### Post by swoll1980 on 2008-01-27
> **brokenhachi said:**
> ubuntu 7.10

it was allready installed by default you have conflicting packages now I think. Did you uninstall the old compiz first I would uninstall every thing you just installed then reinstall it from the repos

---

### Post by brokenhachi on 2008-01-27
i did that

---

### Post by brokenhachi on 2008-01-27
still having the same problem... any other suggestions?

---

### Post by brokenhachi on 2008-01-28
check the link at the top and look at the comments for the resolution

---

