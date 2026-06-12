---
title: "Quick flashes of ? when web pages load"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-02-16
Yesterday I put together my keeper Ubuntu box and loaded 6.06 LTS, 32-bit. 

Hardware is as follows:

AMD 64 3400+
Biostar GeForce 6100-M9 mobo
Onboard video of, you guessed it, nVidia GeForce 6100 + nForce 410 
1 GB RAM
40 GB HDD (I think it's an old Western Digital, don't remember now)
TDK CD/DVD RW 

Monitor is a Gateway FPD2485W, 24" Widescreen, running 1920x1200 resolution

I am running the nVidia glx driver, and added the 1920x1200 resolution running dpkg-reconfigure xserver-xorg (knew to do that only from wrestling with a couple of other machines with video card problems).

Now, the problem. 

Text seems relatively crisp, resolution looks fine, however, when loading a webpage, a very brief flicker of something that I can only describe as looking like a fraction of the yellow thread preview pop-ups we get on the forum here.  Those things that you see when you mouse-over a thread?  It looks like the very top of one of those, yellow, skinny rectangular flash.  It is VERY brief. 

I have my browser over to the left side, and I see this flash of that object over towards the right. 

Is there something I need to adjust?

I was also seeing horizontal lines, not of distortion, but more of a slightly paler shade going down the screen, visible only on the lighter parts of the wallpaper.  I am still using the default wallpaper of the brown tones.  However, I don't think I see that this morning.  It may be something more visible in low-light situations?  

I'm still very clueless, so any help you can give would be greatly appreciated, and please let me know if I can try to clarify any of my descriptions.  

Thank you.

---

### Post by carlosfocker on 2007-02-21
I'm Surprised that onboard video can reach that rez.  You normally see problems like this when the rez is to high for the current video card you use.  Also, thats a nice monitor to have such a low end graphics card.

---

### Post by Wartooth on 2007-02-22
I was wondering whether or not it would pull it off when I ordered this ultra-cheap barebones system, but it has managed. The occasional flash of whatnot over there is the only issue I've had with the video.  The sound...well, that's another story.

The monitor was a gift. :)

The reason for the seemingly mismatching of video and monitor is that I wanted a low-cost entry into the world of Linux to see how well we'd get along, and how much I might wind up using Ubuntu versus my XP machine.  Once I've proven to myself that I'm going to stick to Ubuntu (and I'm thinking I will), then I'll be likely to purchase an add-on video card of higher capabilities. 

Sometimes the ghost lines I see look more like RF interference or something, but, again, it's not something I see in XP.

---

### Post by carlosfocker on 2007-02-22
I still think your crazy for having such a nice monitor with that card :).

What version Nvidia drivers do you have?  You might want to try the newest which are available from Alberto Milone's guide.  [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html).

Other than that I'm not sure.

---

### Post by Wartooth on 2007-02-22
Haha, yeah, I know, it's a bit insane, but I'm pretty well used to being considered such. ;)

I installed the nvidia-glx as soon as I got Ubuntu up and running.  

Thank you for the link, I will certainly check it out once I've finished the morning coffee routine. 

I realize this may simply be something I have to live with until I toss a real video card in here, but if there's something I can tweak, I'd like to try.  I'm all about the learning by doing with this OS.

---

### Post by carlosfocker on 2007-02-22
The default nvidia-glx module is older than anything that Alberto has in his repo.  Its worth trying considering that nvidia has alot to catch up on as far as their drivers go, so each release seems to be pretty significant.  If it doesnt fix it you still have the latest drivers.

---

### Post by alienexplorers on 2007-02-22
I had the same problem and disabled the glx driver in Ubuntu and went to the Nvidia website and loaded the most current drivers.  The problem is now gone.

---

### Post by carlosfocker on 2007-02-22
Alberto's packaged drivers should have the same effect than

---

### Post by Wartooth on 2007-02-22
Ahh!  That's good to hear.  I'm currently shoving food in my face on a little lunch break.  I hope to have the time tonight or tomorrow to walk through this somewhat unknown area. How exciting! :D

---

### Post by Wartooth on 2007-02-22
Okay, clueless klutz question...

I started stumbling through the directions on that Alberto page, and after having enabled his repository and updated it, I got the magical update thing telling me updates were available.  Among the updates listed in the GUI update box was nvidia-glx.  I assume this is because of what I did?  

I went ahead with the updates and when I restarted, I got a different NVIDIA splash screen logo.  The former one was white and green, this one was black and grey (could be wrong, I've had a really long day and am exhausted).  

I feel stupid asking, but is this the update I was meant to do?  

I suppose I should pay attention for the flashes at this point as well.  Durr.  I'm flippin' toast after today.  Sorry.

---

### Post by alienexplorers on 2007-02-22
My Nvidia splash screen is a black background, Green Logo, and Grey "NVIDIA".  I have version 9746 running.  My other files are:
linux-restricted-modules-2.6.15-28-386
nvidia-kernel-common
xserver-xorg-driver-nv

nvidia-glx is not loaded

I ran the install package from the nvidia site with the following directions:

Debian GNU/Linux or Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

After doing these setup instructions I executed the following file:

Download: NVIDIA-Linux-x86-1.0-9746-pkg1.run

Then run: sh NVIDIA-Linux-x86-1.0-9746-pkg1.run

This will install the drivers and the Nvidia-Settings program that let you adjust the nvidia card and monitor parameters.

---

### Post by Wartooth on 2007-02-22
Okay, it sounds like we have the same splash screen, and I haven't seen any of the flashes since doing the update.  How can I find out what I have at this point before going and changing anything else?

---

### Post by carlosfocker on 2007-02-23
What you did was correct and the splash screen should be different.  Atleast your not completely crazy. You should have the latest drivers and they will be updated when you update your kernel.

---

### Post by Wartooth on 2007-02-23
Darn, does this mean I'm only partially crazy? ;)  Don't worry, I'm likely to buy a real video card in the not-so-distant future.  Really. 

Nice to not have the odd flashes anymore.  

Thanks for all the help!

---

