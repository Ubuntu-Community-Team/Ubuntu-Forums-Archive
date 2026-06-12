---
title: "How to install Emerald Theme Manager?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-12-02
I have Gutsy, and so it came with Compiz Fusion.

However, I have been poking around for the emerald theme manager, and I can't find one!  I can do GNOME themes just fine.  I did a search for 'emerald' and only two things showed up: a .png file and a .desktop file.

I looked in Add/Remove for both Emerald and Beryl, and nothing showed up.

Please help!

---

### Post by nae5 on 2007-12-03
open synaptic and search for emerald. its in there.

If you've never used synaptic before you might have to enable repositories

open synaptic and go to settings repositories i just enabled all of them.

you can also sudo apt-get install emerald

---

### Post by Fonon on 2007-12-03
Thanks much.

I've used it before, to get Metal Blob Solid, but not that much.

Thanks again.

---

### Post by DutyDuty on 2007-12-03
```
emerald --replace
``` can be used to switch themes.

---

### Post by s2001t on 2008-04-17
Things started to go screwy for me with compiz, and emerald after installing Kiba Dock.  I'm trying to reinstall emerald, but I'm getting this message,

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable

Can anyone help me w/ this, or point me in the right direction?  

Thanks:confused:

---

### Post by 10Digits on 2008-04-17
How do I install compiz without aninternet connection??

---

### Post by kevinlang21 on 2008-07-10
@ s2001t: I reccomend that you uninstall kiba dock and install avant window manager (awn) instead. It's under current development and does the same thing. It's much easier to find help on awn.

@ 10Digits: Compiz should be preinstalled if you have gutsy or hardy. Go to Sytem -> Preferences -> Appearance -> Visual Effects -> Extra to enable Compiz fusion. You then install emerald via synaptic. Once you install that, you can go back to visual effects and select Custom. If you don't have internet, I'm not quite sure. Maybe you could find a .deb somewhere on a computer with internet and put it on a usb drive?

---

