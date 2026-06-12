---
title: "Multi-Monitor and Resolution"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by JamesB41 on 2006-11-10
Ok...relative neophyte here.  Installed Ubuntu as my first foray into Linux distros.  After a fairly painful install process, I'm up and running.  The install itself went ok, but when I tried to boot into it, my second monitor said it couldn't display the video mode and my primary monitor had a few sparse pixels at the top, and that's as far as it would go.

A friend advised me to unplug my secondary monitor and try to boot again.  Bingo, life's good (aside from losing the secondary monitor).  For whatever sets of reasons, my monitor's maximum resolution isn't available in the dropdown.  I have options for 1280x1024 and lower, but my monitor supports 1600x1200, which I'd like to use.  I went into /etc/X11/xorg.conf and the 1600x1200 *is* listed...but I can't figure out why it's not an available resolution.  The video card is an nVidia geForce 6600 (256) and the monitor is a Dell 2001 FP.  The driver listed in xorg.conf is "nv".  I have not added any additional drivers post installation, whatsoever.  How can I get it to run at 1600x1200?  Driving me nuts.

Secondarily, how do I add multi-monitor support?  To complicate matters, my secondary monitor is a Dell 1905 FP and only supports 1280x1024.  In Windows I'm able to extend my desktop to both monitors and have them running at independent resolutions.

Any help would be ridiculously appreciated.

James (n00b)

---

### Post by CatKiller on 2006-11-10
This thread might point you in the right direction:

[ HowTo: Dual Monitors (Xinerama/TwinView/MergedFB)]("http://www.ubuntuforums.org/showthread.php?t=221174")

---

### Post by JamesB41 on 2006-11-10
Awesome, thank you.  Didn't find that in my search results for some reason.  I'll try that when I get near my machine again.  

Any thoughts on why I can't access that resolution, even in a single monitor configuration?  Do I need to upgrade drivers?  Are the ones that came with Edgy necessarily up to date?  Again, sorry for being a neophyte =).

---

### Post by CatKiller on 2006-11-10
> **JamesB41 said:**
> Any thoughts on why I can't access that resolution, even in a single monitor configuration?

The most common reason seems to be problems reading the EDID information from the monitor through the graphics card. So putting the appropriate HorizSync and VertRefresh lines for your particular model in the Monitor section of your /etc/X11/xorg.conf might help. Some people have had to resort to calculating their own modeline value and adding that, but that's both extreme and rare, I think.

Sometimes, the resolutions aren't listed in xorg.conf at all, and then adding them will help - in the Screen section. And I don't think that the "vesa" driver understands the existence of high resolution values, so if you happened to be using that, you'd need to change to a more appropriate driver.

Those are the main reasons I've seen so far for people not being able to access the resolutions they want. All the gory details are listed in /var/log/Xorg.0.log.

---

