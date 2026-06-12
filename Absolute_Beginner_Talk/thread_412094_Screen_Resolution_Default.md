---
title: "Screen Resolution Default"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by OpEn_SoUrCe_RoCkS on 2007-04-17
Hi !

**Problem 1** - How do I set up a default screen resolution ?

When I boot in, it always puts my screen at 1024x768, but I would like it to be 1280x1024 default.

**Problem 2** - Now I have to use ```
xrandr -s 1280x1024
``` every time, because I can't even change my resolution with the "Monitor and Display" section - it has absolutely no effect when I play with the slider.

How do I fix these problems ?

I'm running Kubuntu latest version.

TIA

---

### Post by edgecoug71 on 2007-04-18
You can try this....I had to do this with my HP dv9000 laptop and its resolution in the Feisty beta...

Open a Terminal and type this :

sudo dpkg-reconfigure -phigh xserver-xorg

Select the resolutions you want as available by hitting the space bar, then press Enter.
Finally, restart X with Ctrl+Alt+Backspace.

if this doesn't work there are forums out there on resolution probs you can find and it will walk you through how to manually edit your xorg conf file to include resolutions that are not there by default....Hope everything works out for ya.....

---

