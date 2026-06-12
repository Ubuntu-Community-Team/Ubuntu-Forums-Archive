---
title: "[SOLVED] Wacom + Gimp = serious lag"
date: 2008-10-29
forum: Art &amp; Design
---

### Post by DirtDawg on 2008-10-29
When using my Wacom Graphite to draw in Gimp, after a few minutes I really get a lot of lag. That is, the time it takes for the cursor on the screen to catch up to where my stylus is on the Wacom pad can be several seconds. Especially when I have both opacity and size set to vary with pressure. 

The computer I am currently using is not a new one. It has a pentium 4 with 256Mb Ram and 768Mb swap (I erred my swap size on install). In Gimp preferences, I set my max undo memory to 32Mb(from 64) and tile cache size to 512Mb(from 1024). I also found booting into Fluxbox helps speed things up. But the problem still persists. 

I also tried Mypaint and even with pressure sensitive size and opacity, it runs very smoothly, but does not support layers.

Is there a Gimp guru who could help me here? Do my Gimp preferences need tweaking? Are layers what cause the problem since Mypaint works fine? Is my computer just too slow to use Gimp + Wacom? 

Any suggestions welcome. Thank you.

---

### Post by Dragonbite on 2008-10-29
My first thought is the lower RAM giving problems because the system has to handle opacity and size set to vary with pressure. Swap files, while useful, are still slower than RAM.

That would go with an improvement with Fluxbox since fluxbox is a lower-resource window manager than Gnome or even Xfce.

If you can't raise your RAM, you may want to see what you can turn off to free up some resources.

---

### Post by cb951303 on 2008-10-29
your tile cache size is still more than your physical memory. I think you should set it to something like 196 MB...

However I doubt this is the problem with your tablet

---

### Post by DirtDawg on 2008-10-29
Thanks guys. Turning the tile cache down to 196 and using Fluxbox really helps. There are still instances of lag, but not as frequent.

I'm also going to try using the older, Synaptic-provided version of the xserver-xorg-input-wacom driver as, according to [this thread]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6056351"), it will fix a bug that causes X to crash on system beep. Maybe it will improve Wacom performance as well.

---

### Post by cb951303 on 2008-10-30
> **DirtDawg said:**
> Thanks guys. Turning the tile cache down to 196 and using Fluxbox really helps. There are still instances of lag, but not as frequent.

I'm also going to try using the older, Synaptic-provided version of the xserver-xorg-input-wacom driver as, according to [this thread]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6056351"), it will fix a bug that causes X to crash on system beep. Maybe it will improve Wacom performance as well.

you can also try the newest one from here [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)
ubuntu package is a litle bit older I think.

---

### Post by DirtDawg on 2008-10-30
> **cb951303 said:**
> you can also try the newest one from here [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)
ubuntu package is a litle bit older I think.

Yes. It was the new driver causing the problem so I had to "downgrade." It did solve the random crash problem, but it did not seem to affect my Wacom performance either way. Still, I am satisfied with its' performance at this point considering the limits of the computer I'm working on so thanks again :)

---

