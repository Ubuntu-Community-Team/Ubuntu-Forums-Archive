---
title: "Is it possible to add the 832x768 resolution?"
date: 2005-04-08
forum: Apple PPC Users
---

### Post by Len on 2005-04-08
I've been playing with different linux distributions for some time, however, not a single one would allow me to choose the best resolution on my PowerMac 5500/275: 832x768.
I've modified my xorg.conf by adding this resolution to the list (no difference) and by adding a modeline for it.

Strange enough, if I force a framebuffer resolution of 832x768 in a kernel argument with BootX Xorg WILL be @ 832x768 without complaining (even if I didn't add the resolution to my config!).

Xorg seems to handle all other 'standard' resolutions fine when I add and remove them. Is there any way I could add 832x768 without forcing it in the kernel?
I'm using Ubuntu 5.0.4 rc. I could post my xorg.conf here if you'd like to see it. I definetly do it when all resolution modelines are perfect.

PS: Ubuntu PPC is the FIRST linux that detects my monitor correctly, all the others needed manual configuration :). Also, audio is working perfect, including microphone, and that's something I can't say about my new G4 1.25 GHz which gets distorted audio with ubuntu.
I'm very glad that Ubuntu revives my old machine, it is fully up-to-date again with FireFox, great work!

---

### Post by soul_rebel on 2005-04-08
what's you monitor max resolution?

---

### Post by Len on 2005-04-08
1024x768 @ 60 Hz.

My videocard is an ATI Rage II with 2 MB VRAM. The mac does 832x768@75 Hz which makes this a perfect resolution, since with the 2 MB of VRAM, 1024x768 cannot be displayed at 24 bit. Besides, a 60 Hz refresh rate is terrible ;-).

Since I've had a lot of trouble with X before I still have filled in the values that I measured with fbset:

max horizontal sync   49.725
max vertical refresh    74.55

---

### Post by Viro on 2005-04-09
[QUOTE=Len]1024x768 @ 60 Hz.

My videocard is an ATI Rage II with 2 MB VRAM. The mac does 832x768@75 Hz which makes this a perfect resolution, since with the 2 MB of VRAM, 1024x768 cannot be displayed at 24 bit. Besides, a 60 Hz refresh rate is terrible ;-).

Since I've had a lot of trouble with X before I still have filled in the values that I measured with fbset:

max horizontal sync   49.725
max vertical refresh    74.55[/QUOTE]

Check this site out. [http://gate.crashing.org/doc/ppc/doc027.htm](http://gate.crashing.org/doc/ppc/doc027.htm) No idea how helpful it will be as I haven't tried it out myself.

---

### Post by Len on 2005-04-11
I've checked that site before, but adding the resulution doesn't work; it isn't listed.

I could try removing all other resolutions but I'd like a system where I can switch ;-).

---

