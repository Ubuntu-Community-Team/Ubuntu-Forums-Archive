---
title: "can my computer use compiz"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-25
i learn that compiz is a compositing window manager from the ubuntu official site. can my computer run on it? from the screenshot compiz looks fun. but what is the practical use of it? it looks like a dice which your 'desk'' can be rolled on.
computer 1
ubuntu 7.10
P4 1.8G
768Mb RAM
160GB HD
Intel i845G on broad integrated graphic

comuter 2
ubuntu 6.06
PIII 933mHz
386Mb RAM
20GB HD
SiS 630 on broad integrated graphic

---

### Post by MaximusTG on 2007-10-25
I see you are running Ubuntu 7.10, it has Compiz installed by default. I'm guessing it will probably work on computer 1, don't know about computer 2 though.. To enable desktop effects:

System -> preferences -> appearance -> visual effects tab

Whether the effects are practicle,  you have to decide for your self. I personally think it is, though I don't use the cube. I use 2 workspaces, with the desktop wall plugin. 

To have more control over Compiz settings, you can install Compizconfig-settingsmanager (ccsm)

You can install it with:

sudo apt-get install compizconfig-settings-manager

You'll probably have to enable the 'universe' (community maintained) software sources

---

### Post by Sef on 2007-10-25
Computer 1 should run ok; but I think that Computer 2 is too low on CPU to run.

---

### Post by Paulmd on 2007-10-25
> **afeasfaerw23231233 said:**
> i learn that compiz is a compositing window manager from the ubuntu official site. can my computer run on it? from the screenshot compiz looks fun. but what is the practical use of it? it looks like a dice which your 'desk'' can be rolled on.
computer 1
ubuntu 7.10
P4 1.8G
768Mb RAM
160GB HD
Intel i845G on broad integrated graphic

comuter 2
ubuntu 6.06
PIII 933mHz
386Mb RAM
20GB HD
SiS 630 on broad integrated graphic


The 2nd reason comp 2 is a NO is the limited 3d capability, and poor 3d support in the linux drivers for the sis 630.

If comp 1 doesn't work, I'd blame the graphics. Intel 845 isn't a high performing GPU (it's ok for ordinary use, but not really much in gaming, and high 3d apps ),

---

### Post by TadH on 2007-10-25
it should actually run on both, but on computer 2 it wlll probably be choppy and slow.

---

### Post by afeasfaerw23231233 on 2007-10-25
even extra works fine on computer 1. but what function does it have besides that ''elastic'' window? not so practical to me. but i may keep ''extra'' on because it causes no harm

---

