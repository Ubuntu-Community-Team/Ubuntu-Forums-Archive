---
title: "Desktop Effects and Nvidia-glx-legacy"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by kacike76 on 2008-01-26
Please Help................
I've posted several threads on my problem.  

I am using and GeForce 3 Ti 200 video card and Ubuntu Gusty.  After about a week of playing around and researching the nvidia restricted driver for my card, i realized that nvidia-glx does not work with my card in Gusty.  I was able to get the nvidia legacy driver installed and working properly to an extent.  

I am able to run glxgears and the output of glxinfo | grep says that direct rendering is enabled.  

However, my problem now is that i can't enable the desktop effects.  When i try enabling desktop effects via systems->preferences->appearance the restricted manager asks me to enable the restricted driver, but it removes the nvidia-glx-legacy driver and reinstalls the nvidia-glx which does not work.  

I've also created a ~/.config/compiz/compiz-manager file and added a line "SKIP_CHECKS=yes" as what suggested in another thread, but that didn't allow me to enable my desktop effect either.  

I am dying to see this cube and all the fancy 3d effects, but unfortunately i am about to give up...... Can somebody please help?????????

---

### Post by Delkster on 2008-01-26
Desktop effects (using AIGLX) require some support from the graphics driver, and just OpenGL acceleration itself is not enough.

Latest NVidia drivers don't support their older chipsets (prior to GeForce 4 or so) but they continue to support those chipsets with the legacy driver. However, they aren't adding new features to that driver line and only provide fixes and compatibility.

The legacy driver line was established a little before desktop effects on Linux became widespread, so at that time there was no support for AIGLX in the driver. Since after that the old chipsets have only been supported by the legacy driver, there's no driver that would both have the newer features needed for AIGLX and support for the older chipsets.

The only way to get the effects working on those cards is probably to use a different approach called XGL. With XGL the whole graphical environment is drawn through OpenGL, and that doesn't require specific support from the driver like AIGLX does. However, XGL is not as well supported as AIGLX and I don't know how to go about installing and configuring it. There is some information about [GLX in the Ubuntu wiki](https://help.ubuntu.com/community/CompositeManager/Xgl) but it doesn't seem to be up-to-date.

---

### Post by kacike76 on 2008-01-26
Thank you very much.  I really appreciate the clarification.  when i read the thread posted below i thought i would be possible to get AIGLX desktop effects on my card but i guess not.  

[http://ubuntuforums.org/archive/index.php/t-574504.html](http://ubuntuforums.org/archive/index.php/t-574504.html)

Also, could you confirm that the Nvidia GeForce 3 Ti 200 does not work with the nvidia-glx.  I've tried several time to install this driver, but after reboot nothing happens (maybe the Xserver doesn't start).  According to the Nvidia documentation and support for linux drivers my card should work with the nvidia-glx, unfortunately i can get it to work (if i did that would fix my problem)  I think this has been reported as a bug, but don't know if it is being worked on....

It seems that i would have an easier time trying to get the desktop effects working with AIGLX, so at this time i am going to start considering an upgrade to my PC and video card in particular.

---

### Post by Delkster on 2008-01-26
> **kacike76 said:**
> Also, could you confirm that the Nvidia GeForce 3 Ti 200 does not work with the nvidia-glx.
I can't confirm that with any more confidence than can be gained with online searches. However, the [driver search page](http://www.nvidia.com/Download/index.aspx?lang=en-us) on the NVidia site seems to indicate that the GeForce 4 MX, GeForce 5000 FX series and newer are supported by the standard driver while the GeForce 4 Ti, GeForce 3 and older seem to be covered by the legacy driver. However, the distinction between which chipsets are considered legacy and which ones are supported by the most recent non-legacy drivers may also have changed over time and support for some chipsets may have been dropped from the mainline driver at some point after the legacy driver line was initiated.

Indeed, the NVidia driver version supplied by the nvidia-glx package in Ubuntu seems to be 96.39, and according to the [NVidia page for that version](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html), the GeForce 3 series is supported, so judging by that it should work. My luck with different driver versions working with different chipsets has varied, though, even if they have been officially supported.

The only NVidia cards that I have personally used even somewhat recently are a GeForce 2 Ti and a GeForce 6800 GT, the former of which clearly falls in the legacy category and the latter one equally clearly doesn't (in fact I use the "new" variant of the driver), so I have no personal experience with GeForce 3 cards.

> I've tried several time to install this driver, but after reboot nothing happens (maybe the Xserver doesn't start).
Sounds like a reasonable assumption. You might be able to find more information in the X server logs, /var/log/Xorg.0.log or so.

> It seems that i would have an easier time trying to get the desktop effects working with AIGLX, so at this time i am going to start considering an upgrade to my PC and video card in particular.
If you really want to get them, that might be the easiest path. (I'm using desktop effects on my home desktop but not on my work laptop because not all usability and compatibility issues have been sorted out yet. It's a matter of personal choice, really.)

---

### Post by Delkster on 2008-01-26
Maybe you could also try making sure that the legacy driver gets removed, resorting temporarily to the nv driver, and then trying to change back to the proprietary nvidia driver from scratch by installing the nvidia-glx driver directly instead of going to the legacy one at all. Of course you may already have tried that.

---

### Post by kacike76 on 2008-01-28
Yes! i got desktop effects to work!!!!!!!!!!!!!!!!!!!!!

Well this is what i did after the trouble i was having.  Still with the nvidia-glx-legacy driver installed and the ~/.config/compiz/compiz-manager file with a line "SKIP_CHECKS=yes"

I install compiz-fusion via the synaptic package and the xserver-xls package.  After that i typed the command compiz and my desktop effects suddently appeared.  

I wish i would've written all the steps followed to get them to work.  I took me over a week to get them.  I don't know if i'll be able to do it again...i tried so many things, so i am assuming the only thing i was missing was compiz-fusion.....

---

