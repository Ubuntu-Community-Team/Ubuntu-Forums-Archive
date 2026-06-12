---
title: "Greek just vanished!!!"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-01
I have installed ubuntu 6.06 on my clevo m400 laptop (pentium M 2.0, X700 256 MB). Everything worked fine at first with the fonts changing from English to Greek by using Alt + Shift.

However, after a few system changes I can't switch to Greek anymore!!!
The changes were the following:
1. Installed all the latest Ubuntu updates.
2. Installed the flgrx (open source) driver for my ati card.
3. Installed components from Easy Ubuntu, including the extra fonts that it offers.

I think I may have some wrong options from the graphics driver in the part were it asks about options for the keyboard (the whole section). Somebody suggested the following :

Code:

sudo gedit /etc/X11/xorg.conf

Section "InputDevice" dad
Identifier "Generic Keyboard" 
Driver "keyboard" 
Option "CoreKeyboard" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc104" Option "XkbLayout" "us,el" 
Option "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll" 
EndSection

I tried both "el" and "gr" but all I got is a warning message when the system loads that X and Gnome have different keyboard settings....
How can I restore the keyboard functionality???

(I also have downloaded Modern Greek from language support section but nothing. Also (not that it matters but u never know I replaced Totem with Totem-xine)).

---

### Post by geokok1981 on 2006-07-01
I just run one more time the vga driver and used the settings EXACTLY as they were given in the suggested code above....and voila!!! Greek and Us with a simple Alt+Shift once again!!

---

