---
title: "[SOLVED] Restricted Drivers help"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-09-09
i have a question... i have not had too much trouble with my installation but maybe a few very minor freezes here and there ... no more than one every few days but i keep noticing a restricted driver listed.

it says 

in order for this computer ubuntu may be using driver software that cannot be supported.

because the software is proprietary it cannot easily be changes to fix any future problems

 and the following is listed as checked enabled and in use

atheros hardware access layer (HAL) 

can i attribute this to the glitches i see every now and then in my computer???
Thanx! any feedback is appreciated :)

---

### Post by madcow72 on 2007-09-10
Hey Vic!

No, this isn't a glitch.  This is just saying that in order to get all of your devices working on your computer, you are using some restricted drivers (not open source)  In this particular case, I think it is your wireless card.  The warning means that because it is a closed source driver, ubuntu can't guarantee that it will support future upgrades to the kernel and such.  It's a warning that's mostly for your own knowledge, in case you do an upgrade in the future and suddenly your wireless card stops working - you'll know what to do.  (Probably that won't happen, though.)

---

