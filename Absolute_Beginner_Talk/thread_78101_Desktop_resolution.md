---
title: "Desktop resolution"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-10-17
I seem to have created a mess here i tried following a how to install the ati driver on my ubuntu hoary system and now i am stuck in one resolution, the card i have is a ati radeon 9550ge 256mb.
when i try to change the screen resolution i get this error...........the xserver does not support the xrandr extention.runtime resolution changes to the display size are not available.
can anyone help with this as my screen resolution is really small

---

### Post by porsher_puddles on 2005-10-17
i have been reading through the threads and trying a few things and i noticed my card is being identified as a radeon 9600 which its not

---

### Post by ecobuntu on 2005-10-17
have you tried to manually edit xorg.conf?

or

at terminal:  sudo dpkg-reconfigure xserver-xorg

---

### Post by porsher_puddles on 2005-10-17
[QUOTE=ecobuntu]have you tried to manually edit xorg.conf?

or

at terminal:  sudo dpkg-reconfigure xserver-xorg[/QUOTE]


i have tried sudo dpkg-reconfigure xserver-xorg, and when i get to the part with the screen resolutions there a many ticked as available.

i haven't tried to manually edit xorg as i'm not sure what to do, could you help me with this

---

### Post by Murgle on 2005-10-18
when reconfiguring the xserver you might want to try setting your default color depth lower, I know that for some computers when the drivers are putzy they like a lower color depth.

---

