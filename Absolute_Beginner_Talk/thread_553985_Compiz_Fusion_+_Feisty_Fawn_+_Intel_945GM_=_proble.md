---
title: "Compiz Fusion + Feisty Fawn + Intel 945GM = problems"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by phendric on 2007-09-18
Hi,

I'm new to GNU/Linux, so be easy on me.  I'm running a new installation of Ubuntu Feisty Fawn (7.04) on a Dell Inspiron E1405 with Intel integrated graphics (the 945GM chipset) (other specs: Intel Core 2 duo 1.83 GHz, 2 GB DDR2 RAM).

This morning, I followed the tutorial [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") to install the latest stable version of Compiz/Emerald on my system, but when I get to the "compiz --replace" terminal command, I lose all of the title bars on my windows, and the GNOME bars at the top and bottom of the desktop disappear.

Here is the list of errors that accompany the command:

> phendric@phillip-laptop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Any tips from anyone on how to get compiz fusion / Emerald working?

Thanks,
Phillip

PS - I running the "xserver-xorg-video-intel" graphics driver

---

### Post by overdrank on 2007-09-18
> **phendric said:**
> Hi,

I'm new to GNU/Linux, so be easy on me.  I'm running a new installation of Ubuntu Feisty Fawn (7.04) on a Dell Inspiron E1405 with Intel integrated graphics (the 945GM chipset) (other specs: Intel Core 2 duo 1.83 GHz, 2 GB DDR2 RAM).

This morning, I followed the tutorial [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") to install the latest stable version of Compiz/Emerald on my system, but when I get to the "compiz --replace" terminal command, I lose all of the title bars on my windows, and the GNOME bars at the top and bottom of the desktop disappear.

Here is the list of errors that accompany the command:



Any tips from anyone on how to get compiz fusion / Emerald working?

Thanks,
Phillip

PS - I running the "xserver-xorg-video-intel" graphics driver
Hi you might have a look at this thread
[http://ubuntuforums.org/showthread.php?t=545806&highlight=window+bars+missing+in+compiz](http://ubuntuforums.org/showthread.php?t=545806&highlight=window+bars+missing+in+compiz)
Or you can try this
No window boarders (titlebars)

Insert the window decorator of your choice (gtk-window-decorator, kde-window-decorator or emerald) in CompizConfig Settings Manager &#8594; Window Decoration &#8594; Command
Good luck!

---

### Post by phendric on 2007-09-18
> **overdrank said:**
> Hi you might have a look at this thread
[http://ubuntuforums.org/showthread.php?t=545806&highlight=window+bars+missing+in+compiz](http://ubuntuforums.org/showthread.php?t=545806&highlight=window+bars+missing+in+compiz)
Or you can try this
No window boarders (titlebars)

Insert the window decorator of your choice (gtk-window-decorator, kde-window-decorator or emerald) in CompizConfig Settings Manager &#8594; Window Decoration &#8594; Command
Good luck!

Thanks for your reply.  I have already seen the thread that you cite, but my case is different from that one in that his desktop effects were working - only his title bars were missing.

In my case, not only are the title bars missing, but I can no longer switch between windows, and none of the Compiz effects are working.  Something more than what his problem was is wrong on my computer.

Finally, regarding your last suggestion re. choosing the window decorator of my choice, I've already used "gtk-window-decorator" in the CCSM --> Window Decoration --> Command box, as per the instructions in the above-linked tutorial.  When I run "gtk-window-decorator" in the terminal, the terminal seems to hang: the cursor blinks, and nothing happens.

Other suggestions from the community?

P

---

