---
title: "Latest update broke graphics rendering"
date: 2010-12-01
forum: Apple Hardware Users
---

### Post by WanderingOak on 2010-12-01
I installed a whole mess of updates yesterday, and when I booted into Ubuntu today, my desktop looked off. I could only use the upper 80% of my display, while Docky had decided to completely take over the bottom portion. Killing Docky brought my display back to full size. However, any scrolling or window movement was very jerky. I double checked my appearance preferences, only to find out that I had been 'downgraded' from 'normal' to 'none'. I attempted to go back to my original settings. First, I was told that the Appearance Manager was searching for available drivers. After flashing through all of my open windows, I was told 'Desktop effects could not be enabled'. A bit of searching discovered that people have had problems with compiz in the past. I downloaded[ compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"), and ran it, only to be shown the following:
> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon HD 2400 XT
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

So, something in my updates broke my graphics rendering. Unfortunately, I don't know how to force Ubuntu to tell me what was updated yesterday. If I could do so, is there a way to revert to the previous version, so I could run the updates one at a time until I figured out what went wrong?

---

### Post by WanderingOak on 2010-12-02
This morning, I looked in Hardware Drivers, and discovered that the proprietary driver for my ATI graphics card were not enabled. When I tried to enable it, I received the following error message:

> SystemError: Failed to fetch [http://ppa.launchpad.net/tuxonice/ppa/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26-generic-tuxonice_2.6.32-26.47~ppa1_amd64.deb](http://ppa.launchpad.net/tuxonice/ppa/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26-generic-tuxonice_2.6.32-26.47~ppa1_amd64.deb) 404  Not Found

I had installed TuxOnIce a few weeks ago to see if it would help me with my Mac's sleep issues, and apparently their kernel doesn't like my ATI driver. I rebooted with a generic kernel, and now everything appears to be working. I'm probably going to wind up dumping TuxOnIce, since it doesn't seem to be helping, and breaks my graphics...

---

