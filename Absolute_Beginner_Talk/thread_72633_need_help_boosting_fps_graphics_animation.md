---
title: "need help boosting fps/ graphics animation"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by helmethedd on 2005-10-06
I've been unable to find the info i need to make my animations run smoother.
When i grab a window and move it around i git a "trail". When i run one of the 3d screen savers, which look fine in the small preview window, run jittery and lack the round lines i see in the previews.
any suggestions? or google search ideas? I don't know enuff about comps. to know even what to look for.

---

### Post by grimmson on 2005-10-06
If this is a clean install and your a n00b like me you probably havn't installed good video card drivers yet. You can check your xorg.config by typing this in console

nano /etc/X11/xorg.conf

find device ati,nvidia,vesa,fglrx(maybe),nv

Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

hit Ctrl x to close

ati's are rough. I think ati's like fglrx. Nvidia likes "nvidia" not "nv". Nv was default for me. "Glxgears" in terminal is a crude benchmark for speed. Using Nv i had 250 fps. Updating to Nvidia 7667 I got 3900 fps. That may be your problem.  If you know your make and model post it. Older cards are falling by the wayside and brand spanking new cards may not have good driver support yet. Hope for a middle of the road Nvidia. Follow this howto for nvidia
[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

search for other howto's for different manuactures. Post for help. Good luck.

---

