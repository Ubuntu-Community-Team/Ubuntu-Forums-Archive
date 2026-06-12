---
title: "Configuring X to work with widescreen monitor"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Kaelor on 2008-03-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/49827](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/49827) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm not sure if this should go in absolute beginner talk, but what the heck.

I recently purchased a new Westinghouse L1975NW 19" widescreen monitor for my home PC. The monitor is designed for 1440x900@60 Hz resolution. Currently, it's running a dual boot with Ubuntu Gutsy and Windows XP Professional edition. The graphics card is an ATI Radeon X700. The monitor immediately showed some problems, especially with regards to resolution. 

I've already tried using dpkg-reconfigure xserver-xorg; it doesn't seem to recognize widescreen monitors.

After some hacking away, I managed to get two distinct failure modes.

The first is one that gives full 1440x900 resolution @ 60 Hz, but without any of the fgrlx restricted driver benefits. I suspected early on that GNOME settings might be part of the problems, so I deleted all my .conf files related to GNOME in my home directory, and then followed the suggested modifications to xorg.conf in this tutorial:
[http://ubuntuforums.org/archive/index.php/t-495350.html](http://ubuntuforums.org/archive/index.php/t-495350.html) (of course, all of this was done after a dpkg-reconfigure xserver-xorg with the best answers I could give).

After rebooting, GNOME started up with the login screen on low graphics mode prompting me to reconfigure, when I selected "Generic Monitor 1440x900 (Widescreen)" and the open source ATI driver. After a reboot I can then login and work at 1280x1024 (not exactly what I want), but functionality is choppy, most visual media drops frames all over the place and needless to say, disabling compiz is a must. If I attempt to enable the restricted driver via the GNOME restricted-manager application, after rebooting X does not work correctly and will react much the same way as in the other failure mode.

The second failure mode happens if I mark the proprietary ATI fgrlx driver for use after wiping the GNOME .conf files or using dpkg-reconfigure. After reboot the monitor goes blank and simply reads "Out of Range," or worse, continues to attempt to adjust without success.

This appears to be a problem with X rather than with GNOME. If I mark fglrx as the driver in xorg.conf and run "startx -- :1" from a tty, then the same problems appear. 

This is a complete mystery to me. Any way I can fix this?

---

### Post by LowSky on 2008-03-28
Your issue is with your ATI drivers. I say this only because they have been the source of evil for many users here, and the fact is my monitor is running at  the same resolutions with Nvidia drivers just fine.
You might want to try using a program called Envy to install you ATI drivers.
After that you should be able to run you monitor at 1440x900

---

### Post by Inxsible on 2008-03-28
> **LowSky said:**
> Your issue is with your ATI drivers. I say this only because they have been the source of evil for many users here, and the fact is my monitor is running at  the same resolutions with Nvidia drivers just fine.
You might want to try using a program called Envy to install you ATI drivers.
After that you should be able to run you monitor at 1440x900I agree. I have the same res with NVidia drivers without any issue. Everything worked out of the box.

I would keep away from Envy though. There are a few tutorials on how to make the ATI drivers work, if you search the forum.

---

### Post by Kaelor on 2008-03-28
Fixed the problem. My ATI restricted driver (fglrx) was already installed when I had an older monitor. I realized the problem was coming from GNOME after all, since I was trying to configure xorg.conf and, expecting instant results, using the GNOME configuration utility when that didn't work. 

Note to future self: when modifying xorg.conf, reboot, don't just restart X.

I ran sudo dpkg-reconfigure xserver-xorg with the correct settings, selecting fglrx as my driver, and then added the following lines to xorg.conf in Section "Screen":

```
SubSection "Display"
     Depth 24
     Modes     "1440x900"     "(pitch"     "1440)"
EndSubSection
```

After that a simple reboot got me working fine, with the restricted driver and compiz in operation with the 1440x900 resolution at 60 Hz. 

Thanks everyone for your help.

---

### Post by dcstar on 2008-03-28
> **Kaelor said:**
> Fixed the problem.
........
After that a simple reboot got me working fine, with the restricted driver and compiz in operation with the 1440x900 resolution at 60 Hz. 

Thanks everyone for your help.

Excellent that your problem is solved, please mark the thread as such so some of us don't waste our time looking at things that are resolved.

---

