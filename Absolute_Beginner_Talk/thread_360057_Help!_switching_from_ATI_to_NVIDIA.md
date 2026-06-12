---
title: "Help! switching from ATI to NVIDIA"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by zero_koop on 2007-02-12
Hi all, I've really screwed up my configuration and would like some help.  I had everything working great last week with my ATI drivers and card but I switched to an NVIDIA card over the weekend without taking any preparatory steps in Ubuntu (I was mostly concerned with my  Windows install at the time).  So when I booted up Ubuntu it, of course, gave me an error to start Xserver.  In fact, one of the errors I receive is:
```
Data incomplete in file /etc/X11/xorg.conf
             Undefined Device "ATI Technologies, Inc. RV350 AP [Radeon 9600]" referenced by Screen "Default Screen"
```
And while looking at my xorg.conf file I found many remnants of the ATI driver still around.

So I looked around online, I think I figured out how to uninstall my ATI driver (sorta, becaues there are still many remnants of it) and I downloaded and installed a NVIDIA driver, but it's still not working.

Where should I start?  Is there any way that I can reset all driver stuff to a default value just like when I first installed Ubuntu and booted up for the first time so that it can detect and install default drivers for me?  Keep in mind, I cannot work from a graphical interface so everything I need to do I have to do from the command prompt which I am new to.  Does anyone know of a guide that I should have followed in order to switch from ATI to NVIDIA?  Thanks.

---

### Post by jpeddicord on 2007-02-12
Type "sudo dpkg-reconfigure xserver-xorg" in a terminal (or recovery mode if X won't start). It should walk you through some steps to reset X back to a default. From then on you should be able to install NVIDIA drivers without worrying about ATI remnants. :)

---

### Post by zero_koop on 2007-02-12
Yes!  That's exactly the command I was looking for.  I'm back into my desktop.  Just a few things to smooth out and I'll be back to normal.  Thanks for the help.

---

