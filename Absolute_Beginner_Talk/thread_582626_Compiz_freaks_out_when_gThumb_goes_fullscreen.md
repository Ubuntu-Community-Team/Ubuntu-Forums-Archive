---
title: "Compiz freaks out when gThumb goes fullscreen"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by hohead on 2007-10-20
Hey kids,

Finally got Gutsy installed and working with my ATI x800 card!

Installed compiz by running the following:
> sudo aptitude install compizconfig-settings-manager

then:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace



Everything seems to be running smoothly, however, when I view an image in gThumb Image viewer and go fullscreen (F11). Once the top toolbar "scrolls up" after 1 second of going full-screen, the whole screen starts to flicker like crazy. Once I escape from fullscreen, this intense flickering goes away.

When I go to "System -> Prefs -> Appearance" and under "Visual Effects" click on none, I can now go to gThumb and go fullscreen without any issues.

So obviously this issue is related to Compiz. Even when I go in Compiz settings and turn off all of the effects, it still happens.

Any suggestions? Are there any other details I can give to help?

---

### Post by tboxmy on 2007-10-20
hohead,

Compiz is running on my Lenovo R60 with Gutsy installed. The Image viewer flickers when i go into slideshow. Same thing with gthumb, but if I do not move the mouse its all smooth in the slideshow.

Since gthumb didnt give the flicker, I made all jpegs open with gthumb by default.


Ciao!

---

### Post by adamorjames on 2007-10-20
hohead, 

Same problem. I think most everyone has the problem.

---

### Post by screaminj3sus on 2007-10-20
No problem here, compiz enabled with an Nvidia 7600GS.

---

### Post by camini on 2007-10-21
same here on a HP dv2000 (dv2386ea) laptop (nVidia 7200 me thinks).
any diagnose of problem?

---

### Post by wild_oscar on 2007-11-06
> **camini said:**
> same here on a HP dv2000 (dv2386ea) laptop (nVidia 7200 me thinks).
any diagnose of problem?

I have the exact same problem. Tried with gThumb as suggested and it flickering did not occur.

Anyone knows what bug this is?

---

