---
title: "Numbers Lock"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-08-07
I've had Edgy now for quite a few months and never resolved the numbers lock which doesn't work.  It is always on even though the keyboard led toggles on and off.  I just tried installing numlockxx and now get the following error message on boot.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Can anyone advise please?

Thanks

Keith

---

### Post by FakeOutdoorsman on 2007-08-08
Did you try this?
[How to turn on Num Lock on GNOME startup]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup")

---

### Post by bugster on 2007-08-09
> **FakeOutdoorsman said:**
> Did you try this?
[How to turn on Num Lock on GNOME startup]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup")

Thanks - just tried it and it's the same.  Just to clarify - the numbers lock is on even though the keyboard LED can be switched on and off with the Num Lock key.

There is no option in the bios to alter the keyboard num lock - all there is reference to USB keyboard enable/disable - I've tried both options and it's the same.

I've also tried 3 different keyboards and edited xorg.conf to try all the different options for keyboards to no avail.

Really beginning to tear my hair out now.:confused:

Help really appreciated.

---

### Post by bugster on 2007-08-09
I've just rebooted and during the GRUB stage the num lock led stays off.  It is later just as the nautilus screen appears the num lock led switches on. 

Does this help anyone please ?

---

