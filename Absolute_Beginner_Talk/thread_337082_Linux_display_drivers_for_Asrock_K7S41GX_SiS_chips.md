---
title: "Linux display drivers for Asrock K7S41GX SiS chipset, are there any?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by whee on 2007-01-12
I'm looking for Linux display drivers for the SiS chipset on an Asrock K7S41GX motherboard.
Does anyone know if there are any?
I'm now using vesa drivers, but they tend to be a bit slow with that chipset and there's also some light, but slightly anoying flickering going on.
So that's why i'm looking for original Linux drivers.

---

### Post by RMorris78 on 2007-01-12
i believe the open source driver for them is called "sis" and should be included in the kernel. i have a mobo with sis integrated gfx and that worked fine for me

try running

sudo dpkg-reconfigure xserver-xorg

from Terminal, and make sure to select the "sis" driver

good luck

---

### Post by whee on 2007-01-12
Thanks, it worked, all problems of unresponsiveness and flickering are gone, everything is totally smooth now.
But instead of running the command in the terminal i tried looking up the xorg.conf file in /etc/x11 . And then tried editing it with sudo/root permissions.
I scrolled down to: Section "device" , in the xorg.conf file and changed Driver from "vesa" to "sis".
And that did the trick.
I was offcourse able to change the driver via the terminal with the command you suggested, though instead of just asking me to change the driver it asked me a question for alot of other X configuration settings and i didn't know how to exit and save after i just changed the driver brand/type.
So that's why i did it the way i did...i just happened to know the xorg.conf was in /etc/X11 .

Thank you!

---

### Post by whee on 2007-01-12
I have one more question though.
Suppose next time i wanted to use the command:
sudo dpkg-reconfigure xserver-xorg

And suppose i wanted to only change 1 setting....how would i do that? Because i'm asked to set alot of other X configuration settings, but i see no Escape or Save option anywhere.
It just keeps on asking things.
Does anyone know how this is supposed to work?

---

### Post by whee on 2007-01-12
*bump, i think the thread got buried

---

