---
title: "T61p w/ NVIDIA 570M - Restricted Driver Not Detected after Envy Uninstall"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by navraj on 2008-03-18
Firstly, I've searched on the forum for a solution to this, and although there are other threads regarding T61p with nVidia 570M, I couldn't find a solution.

I'm running Gutsy on a T61p with nVidia Quadro FX 570M. Initially, I was running the restricted nvidia driver (I think its nvidia-glx-new), and it was working fine. However, I tried installing the non-restricted updated drivers with the Envy tool (primarily to get the screen brightness control working, which doesn't with the restricted drivers). Envy installed fine and downloaded/packaged/installed the nVidia driver, but after reboot, I got a very bad resolution and rendering. So, I uninstalled Envy, re-installed the restricted drivers, and rebooted. Before the user login, I got the following message:

"Ubuntu is running in low-graphics mode

Your screen & graphics card could not be detected correctly. To use higher resolutions, visual effects, or multiple screens, you have to configure the display yourself"

There is a configure and continue button. Continue just proceeds with booting, but the resolution is very low, and I can't make it higher. When I go to the restricted drivers manager, I see that the restricted nVidia driver is enabled, but it says its "not in use". Clicking Configure on the low-res dialog let's me select the driver, but that doesn't seem to help, and I still can't get the correct resolution.

Right now I'm running the vesa driver, after disabling the restricted drivers..this seems to work fine. 

One thing I noticed after reinstalling the restricted drivers - the xorg.conf file had listed the card in the "Device" section as "Generic Video Card". I changed this to "nVidia Corporation G80 [Quadro FX 570M]", but it still didn't help.

Any ideas?

---

### Post by Hospadar on 2008-03-18
I think you may be confused as to what you actually did, envy doesn't install any non-restricted drivers, the drivers you download from nvidia (which is what envy installs) are really the same as the restricted drivers, although they may be a slightly newer version.

There are non-restricted drivers for nvidia, which are the "nv" drivers.  If you would like to try using these drivers, I would suggest using envy to remove and clean your nvidia drivers, and then run "sudo dpkg-reconfigure xserver-xorg" and on the first page, select the "nv" driver (instead of vesa or "nvidia") you can pretty much just default your way through the rest of the options.

I suspect what happened is that what envy tried to install some drivers on top of what was already there, and there were some conflicting files.

---

### Post by navraj on 2008-03-18
Yes...I was mistaken when I said "non-restricted" drivers...I guess there is no such thing from NVIDIA. I tried your suggestion, but that didn't fix the resolution issues either. I think in the process I've completely lost control of the xorg.conf file with no way of restoring it. Since I haven't done much in ubuntu yet, I think I'll just reinstall it. Thanks for the suggestion though!

---

