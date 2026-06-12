---
title: "[SOLVED] X server munged?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-05-07
Last night the dog, panicked by the thunder, creamed into the video cable hard enough to strip the thread on the screw anchoring the video card, and yank it partly out of its socket.

Now there is some minor damage to the mother board (two leaking caps) and when booting Ubuntu, it runs 'till about the point where X and Gnome would start up and the monitor says "No signal." It does still run with Windows 98.

An early try resulted in a rather strange color text screen showing X-errors: No screen detected IIRC.

I ran a boot in recovery mode and after that, and it now the video just shuts off near the end of the boot process. Looks like I'll have to recover this in the text mode from the recovery boot. . . But how?

Thanks in advance!

---

### Post by fakie_flip on 2007-05-07
Make sure the video card is seated in its slot firmly. It may have came loose.

---

### Post by pizzutz on 2007-05-07
Well, I can't be sure, it sounds like it's a hardware and not a software problem.  It sounds like it is blacking out when X loads your video card driver.  If that's the case you may have lost some functionality in your mbd/vid card that is not used using the generic drivers at boot-up, but is needed when the full drivers load when X starts.  you may need a new vid card or motherboard. you could try using a more generic driver (ie nv instead of nvidia) but if is locking up in recovery mode, then that will likely not help.

Post your motherboard, Video card and video card driver information so that someone smarter can help.

---

### Post by jrlii on 2007-05-07
The motherboard is a Mach Speed N2PAPLITE and the video board is an ATI 9200SE. However, the problem seems to resolved itself.

---

