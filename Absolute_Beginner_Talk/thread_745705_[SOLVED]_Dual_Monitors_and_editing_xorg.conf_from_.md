---
title: "[SOLVED] Dual Monitors and editing xorg.conf from terminal"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-04-04
I've been trying to get dual monitors working over the past couple of days. I installed a video card that was capable of outputting to two separate monitors (GeForce FX 5200), but my screen is black, when I start ubuntu. I'm not exactly sure what the problem is, but I suspect that I have to modify my xorg.conf file. My questions are:

How can I detect the BusId of my graphics card?
What do I need to change/add to my xorg.conf file?
And once I get one monitor working, what do I need to do to setup dual monitors?

Thanks.


Edit: Hmmm, I just tried to autoconfigure my xorg file, but the screen is still blank. Any ideas?

---

### Post by JoshuaRL on 2008-04-04
Well before you try to manually edit xorg.conf and all that, try:

```

dpkg-reconfigure -phigh xserver-xorg

```

and see if that fixes your issue.

---

### Post by Inxsible on 2008-04-04
If you use the restricted nvidia drivers then all you need to do is type in```
nvidia-settings
``` in a terminal and then setup the dual monitors there.

If you want to write it to the xorg file though, you will have to use gksudo on that command or you won't be able to save the changes for your next bootup.

I would suggest, you NOT use gksudo initially. If everything works, you can always save the xorg file the next time.

---

### Post by anothrguitarist on 2008-04-04
Wait it worked, although there was an error message which said something like, "Cannot start on the specified device, trying 1" or something similar. I'll let you know if I continue to get an error message after reboot.

---

### Post by bodhi.zazen on 2008-04-04
As far as I know you need to install the nvidia (proprietary) driver for dual monitors.

You can do this easiest with envy :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Then run :

```
gksu nvidia-settings
```

Adjust your monitors and click the save button.

For a manual edit, see something like this (you will need the nvidia settings and your monitor specs)

[http://darkshed.net/files/rcs/misc/xorg.conf](http://darkshed.net/files/rcs/misc/xorg.conf)

---

### Post by anothrguitarist on 2008-04-04
That worked like a charm, thanks.

---

