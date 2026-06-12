---
title: "Kubuntu remnants after return to Ubuntu"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-07-11
Hi All,
   I installed the Kubuntu desktop using aptitude to check something out
and then uninstalled it using aptitude. I used aptitude because aysiyu and others said it did a thorough job on unistall. The problem is on boot up
I get the Kubuntu graphics and some cursors like the activity cursor appear to be KDE cursors. I guess aptitude didn't do such a good job after all.
This isn't such a big deal just an annoyance unless it causes other 
problems. Anyone know of a fix.

---

### Post by Frank Golden on 2006-07-11
Anyone!!!

---

### Post by arochester on 2006-07-11
You could try changing the session from KDE (if is still shows) to Gnome.

If you enter a password there is a button there marked "Menu"(?) the top of the pull-down is "Session Type"(?). It can be changed there

---

### Post by Brunellus on 2006-07-11
use deborphan:

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by KFASheldon on 2006-07-11
You could try a re-install of ubuntu base and/or gnome base plus check session id gnome not last in login - your not autologing in are you !!

---

### Post by Dr. Nick on 2006-07-11
If you are just getting the blue kubuntu text on the inital startup as oppsed to the brown ubuntu then look here toward the end (its short anyway)

[http://ubuntuforums.org/showthread.php?t=211187](http://ubuntuforums.org/showthread.php?t=211187)

---

### Post by aysiu on 2006-07-11
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by Frank Golden on 2006-07-11
> **KFASheldon said:**
> You could try a re-install of ubuntu base and/or gnome base plus check session id gnome not last in login - your not autologing in are you !!

Yes I am.

---

### Post by dmizer on 2006-07-11
just try this:
```
sudo dpkg-reconfigure gdm
```
that should return you to the original ubuntu login manager setup.

---

### Post by dmizer on 2006-07-11
i gave the wrong command previously, if you've tried it and only got "gdm is already installed and configured", please take a look at my previous post again and try the change.

---

### Post by Frank Golden on 2006-07-11
Thanks for the responses but too late used my partimage image
and restored ubuntu to earlier. Have bookmarked info for future use.
I am sure I'll need it in future. I can't seem to keep from fixing things
til they are broke.:D

---

