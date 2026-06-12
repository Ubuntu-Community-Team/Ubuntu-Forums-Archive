---
title: "Ubuntu Studio broke my computer. :("
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Losgann Mor on 2008-03-06
Hello, I'm am a total newbie to Linux, just built my first system and installed Ubuntu 7.10 on it. One of the reasons I chose Ubuntu over other distros is Ubuntu Studio -- I'm a musician and really keen to explore music recording and production with open-source software. Anyway, it was all working fine until I went into Synaptic and installed all the Ubuntu Studio packages. When I restarted my machine, I got the following code:
> 
*Starting anac(h)ronistic cron anachron [OK]
*Starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state... [OK]
*Running local boot scripts (/etc/rc.local) [OK]
*Starting timidity
*Starting TiMidity++ ALSA midi emulation... [OK]

As soon as it got to this point, I got an error screen saying:
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Then regardless of answer (choosing no takes me straight here, choosing yes gets me a screen of impenetrable code and then takes me here) I get the following message:
> The X server is now disabled. Restart GDM when it is configured correctly
When I hit OK, I then get the following error message 6 or 7 times in a row:
> bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or mode failed
...and then the whole thing crashes, and my only option is to shut down. I tried rebooting several times, and this happened each time.

What I did eventually figure out is that it only does this when Grub loads the realtime kernel that comes with Ubuntu Studio. If I go into grub and select the generic kernel, everything boots fine. But here's the kicker: the machine won't recognize my USB keyboard until after the boot process. When it first starts and loads Grub, I have to have a PS/2 keyboard connected in order to select which kernel to load. Luckily our other, older computer happened to have a PS/2 keyboard or I wouldn't have gotten this far. And anyway, I don't want to have to use an old, crappy PS/2 keyboard with my new system, nor do I want to have to go out and buy a new PS/2 keyboard which isn't as nice as my USB keyboard in order to use my computer. 

So, I said to myself, forget Ubuntu Studio, just uninstall it and go back to plain Ubuntu. So I went into Synaptic and marked all the Ubuntu Studio packages I'd installed for complete removal (that's how you get rid of the dependencies as well, right?). It told me that everything was removed. So I restarted, and got the old Ubuntu logoff logo as it was shutting down, so I thought I'd succeeded. But no -- most if not all of the additional applications are still there, and the real-time kernel is still there, still having the same problems, and I still can't boot my computer unless I attach a PS/2 keyboard, go into Grub, and tell it to boot using the generic kernel. Synaptic tells me that all the Ubuntu Studio packages are not installed, but they all still seem to be.

My apologies for the very long post, but as I said I'm brand new to all this and I'm kind of ready to pull my hair out at this point. Is there any way to just remove the real-time kernel and save everything, or do I just have to do a complete re-install and not download Ubuntu Studio this time? Many thanks to anyone who can help.

---

### Post by shuukazedojo on 2008-03-06
I'm having similar, although not as complex, issues with Ubuntu Studio. I also just downloaded via Synaptic along with all the attached packages. It required a restart to complete. When I logged back on it said something about the screen resolution not being high enough, so I changed it. This was the beginning of chaos. After some fun with all of that, basically random guessing, I finally got some help and now it's back to normal resolution. However, all of my themes, icons, Compiz settings, etc. have been demolished. My thought was the same as the user above: uninstall the last program installed. Seems logical. But, I'm coming up with the same issues: uninstalled successfully via synaptic but it is still showing these programs under the Applications menu. Also tried to go Applications > Add/Remove but it doesn't show the applications that I need to remove in that list!

In addition to all of this, I'm now getting these error messages (see attachment). One is after login. The other was when I tried to adjust the mouse settings...something else that was reset by this. Any help is greatly appreciated!!!!!!!!!!!!!!!!

---

