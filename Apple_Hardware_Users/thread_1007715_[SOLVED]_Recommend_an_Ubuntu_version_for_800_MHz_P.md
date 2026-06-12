---
title: "[SOLVED] Recommend an Ubuntu version for 800 MHz PowerMac G4 &amp;quot;Quicksilver&amp;quot;"
date: 2008-12-10
forum: Apple Hardware Users
---

### Post by bavid on 2008-12-10
I'd like to install some version of Ubuntu on a PowerMac G4 "Quicksilver 2002". The machine specs from everymac.com are [here]("http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_800_qs.html"). Specs that might jog your memory are:

800 MHz G4
ATI Radeon 7500 AGP Graphics Card
40 GB HDD and 512 MB RAM

I have an Apple Studio Display, LCD, 17in with the ADC connector.

So far I have tried Intrepid 8.10 (server) and Gutsy 7.10 (live CD) and both failed (for different reasons, see below). I don't need a recent version of Ubuntu, just one that works. Before I waste any more time on this, can someone recommend a version of Ubuntu that would install on this machine with the least fuss? 

-----------------------------------
Intrepid installed just fine, but I can't get X to work. It seems to use the VGA jack (not the ADC jack) as I can see Gnome start when I plug in a VGA monitor. However, the keyboard and the mouse die at this point. I feel like the problem is probably with my xorg.conf file, but I can't find any leads on how to fix it.

The Gutsy live CD gets hung up at the BusyBox prompt, and all attempts to get the HD working with commands like "modprobe ide-core" fail.

If someone things they can fix these issues I'd be happy to provide more info, though I'd prefer just taking an older version that is known to work on this hardware.

---

### Post by ayoung on 2008-12-10
I've got Dapper Server installed on a 1999 OldWorld G3 mini tower.  This hardware does not support booting from CD, so I had to install a helper program to boot from CD and to enable the subsequent dual-boot.  Anyway, I've had stable operation for over a year now, and I frequently ssh tunnel into it as a development web server.

I mention this because 1) I see you attempted a server install and 2) the video settings were a nightmare when I was doing the text-based install with a monitor hooked up to the machine.  So, if you don't need a GUI, skip it!

Cheers.

---

### Post by ayoung on 2008-12-10
Right, and while Dapper seems horribly old now, considering the alphabetical 6-month release schedule, it was released June '06, and as a LTS server version, receives 5 years of security updates and support.

So, even with this old version, you're covered for another 2.5 years.

---

### Post by bavid on 2008-12-10
Thanks for the info. If you managed to get Ubuntu running on an OldWorld G3 you are truely a better man/woman than I. Unfortunately, my goal is use the Mac as a display board -- hence the need for the display. This is one application where the ADC port comes in handy, as it can supply data and power over a single cable. Otherwise it's just a pain in the ***. 

In the absence of any other suggestions, I'm going to spend tomorrow working my way back through Edgy, Dapper, etc. and see if I can get problems that I know how to solve. Donations of blank CD-Rs are greatly appreciated.

---

### Post by bavid on 2008-12-10
Update on my progress:

I finally figured how to boot into single user mode with Intrepid. The trick was to use "Linux video=ofonly nosplash single" at the yaboot prompt, and not just "Linux single". This allowed me to get a root shell play around with xorg.conf and determine the following:

The "fbdev" driver works for depth <= 8, but colors are so far out of whack that the display is almost unreadable. But at least I can start X.

The "ati" driver does seem to work at first. But upon plugging a second screen into the VGA port I find a very nice Xbunutu desktop, with good colors and everything. So it looks like X is using the VGA display for some reason. I think if I can figure out how to force it to use the ADC port, I'll be good to go.

I can't get my xorg.conf off the machine right now, but it's very similar to that shown [here]("http://www.linuxforums.org/forum/linux-desktop-x-windows/125698-adc-apple-studio-display-problems-ppc-debian.html").

---

### Post by bavid on 2008-12-11
As promised, my current xorg.conf file is attached. My current configuration is an old Compaq flat panel on the VGA port, and my 17 inch Studio Display on the ADC port. With the attached xorg.conf I get X on the Compaq, but with the resolution specified for the Studio Display. I get nothing on the Studio Display.

Not specifying the resolution gets me native resolution on the Compaq display, and nothing on the Studio Display. With some other options I can get the power light on the Studio Display to blink, indicating that it's trying to do *something* but I never get anything visible.

Using the "fbdev" driver instead of "ati" gets X on the Studio Display, but with the colors completely mangled. 

I'm giving up for now. Unless I can find someone with a deeper understanding of the xorg.conf file and Apple hardware, there's no way I'll be able to make this work.

---

### Post by bavid on 2008-12-16
After letting it sit for a few days I got a second wind and found an xorg.conf that works (attached).  The trick seems to be using the 'fbdev' driver instead of 'radeon' or 'ati', and configuring each screen/head separately. Some of my configuration may be unnecessary, but I don't want to mess with it now that it's working. I also need to boot with 'nosplash'.

Some things are still funky. For example, the Xfce file manager (thundar) doesn't work.

Since I got it working with 8.10 Intrepid, I didn't try reverting to 6.06 Dapper.

---

### Post by stream303 on 2008-12-16
wow - thanks for the detailed rundown.  That tip about adding extra parameters to *Linux single video=ofonly nosplash single* is going into the notebook right away.

Sorry to hear about the Xubuntu problems - I know that many are suffering from that having to either recompile or start the app from a terminal, ie *thunar &*.  There is an experimental repo to try and fix some of that in the sig.

Just wanted to say nice job of sticking with it...

---

