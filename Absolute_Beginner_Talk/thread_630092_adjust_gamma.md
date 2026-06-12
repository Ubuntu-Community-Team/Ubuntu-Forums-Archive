---
title: "adjust gamma"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-12-03
My screen seems a little dark since i installed ubuntu, how do i adjust the gramma?

---

### Post by ptn107 on 2007-12-03
I too would like to know how to change brightness\contrast in Ubuntu.

---

### Post by jordanmthomas on 2007-12-03
```
xgamma -gamma somenumber
```
1.0 is default
2.0 is twice as bright
0.5 is twice as dark

**edit**
If you find a gamma you like, it is possible to make it permanent by editing your xorg.conf.  Let me know if you need help with this.

---

### Post by Idk123 on 2007-12-03
I'm rather new to this whole "ubuntu" :P but, well... I believe if you right click on your desktop, there's an option for the brightness. Sorry if I'm wrong, and chances are I am wrong, but, hey... Worth a shot :P

---

### Post by ptn107 on 2007-12-03
So there is no gui application in ubuntu's systems menu that I can use to adjust brightness\contrast settings?

---

### Post by jordanmthomas on 2007-12-03
> **ptn107 said:**
> So there is no gui application in ubuntu's systems menu that I can use to adjust brightness\contrast settings?

I don't think so.  KDE has one, but Gnome tends to lack any feature Gnome-devs don't think everyone needs.  xgamma is pretty easy to use though.

---

### Post by jrharvey on 2007-12-03
if you are by chance using an Nvidia Graphics card then there is a nice GUI tool in the nvidia-settings that you can adjust the gamma. I wouldnt know about ATI or any other card because I have only used nvidia since ive had ubuntu.

---

### Post by apauloisdead on 2007-12-03
> **jordanmthomas said:**
> ```
xgamma -gamma somenumber
```
1.0 is default
2.0 is twice as bright
0.5 is twice as dark

**edit**
If you find a gamma you like, it is possible to make it permanent by editing your xorg.conf.  Let me know if you need help with this.


Yeah, how would i go about this?

---

### Post by jordanmthomas on 2007-12-03
open up a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo /etc/X11/xorg.conf
```
Find the "Monitor" section.  Mine looks like this (yours could be different)
```
Section "Monitor"
        #DisplaySize      330   210     # mm
        Identifier   "Monitor0"
        VendorName   "AUO"
        ModelName    "f0d"
EndSection

```
In here, add this line
```
Gamma THE_NUMBER_YOU_FOUND_YOU_LIKED
```
to make it look like this:
```
Section "Monitor"
        #DisplaySize      330   210     # mm
        Identifier   "Monitor0"
        VendorName   "AUO"
        ModelName    "f0d"
[COLOR="Red"]        Gamma THE_NUMBER_YOU_FOUND_YOU_LIKED[/COLOR]
EndSection

```
Save it and close gedit.  Now, log out and back in and your gamma should be fixed.  (hit ctrl-alt-backspace before you log back in though to make sure X gets reloaded)

---

