---
title: "when i click on desktop effects it says the comopiste extension is not available"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
and my sound question is still not answered

[http://ubuntuforums.org/showthread.php?t=493668](http://ubuntuforums.org/showthread.php?t=493668)

---

### Post by NeoLithium on 2007-07-06
Hi, 
Which version of Ubuntu are you running, and what video card are you using?

---

### Post by Korea91 on 2007-07-06
7.04 the new one and also the graohics is ATI MOBILITY RADEON X 700

---

### Post by NeoLithium on 2007-07-06
Thre's a few things you may need to enable within your xorg.conf file. See this part of Ubuntuguide to check if you missed anything that may help out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

i have an NVIDIA card myself, but ensure you enable GLX, etc, within your modules section.  The link gives you an easy walkthrough though.

---

### Post by Korea91 on 2007-07-06
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

