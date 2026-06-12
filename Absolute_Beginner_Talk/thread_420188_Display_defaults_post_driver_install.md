---
title: "Display defaults post driver install"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Ryokukitsune on 2007-04-23
I have a Quadro FX 3500 GFX card and installing the driver was a pain, i couldn't even do it myself. i had to use Envey to get it done rite. once the driver installed I couldnt set my screen resolution any higher than 1024x768 till i Nano'd my xorg.cong file to append in additional resolutions that said now i have access to them however they do not stick once the machine is rebooted.

I think i must have missed a line when i was reading the walk threw. anyone know what i did wrong?

PROBLEM NUMBER 2)

after installing the Nvidia modules I lost the shutdown and restart options in the shutdown options menu. they just went poof. for a temp fix i set the power button to shut down. its a fix but its such an annoying problem.

help? u_u peeeezzz

---

### Post by Ryokukitsune on 2007-04-27
just a revisit to this thread before its niglected or closed.

I did manage to get the resolution settings to stick. apperently xorg.conf prioritizes the resolution list by entery so the first values are the defaults. if you want to set your default resolution add the display mode at the top of the list.

the missing shutdown and restart buttons where a result of messing with the log in screen/themes. if you unchecked a box that says something about addional options (i cant check, currently booted under windows) it turns off the shutdown and restart options in the log off options.

to fix that problem you need to go to system > administrator = log on window (or something similar, it is at least in this menu set)

---

