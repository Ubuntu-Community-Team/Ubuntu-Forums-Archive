---
title: "Help sorting out some things."
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Synlaw on 2007-04-02
Hi, i have just installed Ubuntu 6.06 (Dapper Drake) and need some help sorting main things out, any help would be apprecieted.
So here are my problems;
Need help fixing my GFX driver, its a ATI integrated Express x200 here i can get the driver [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) (i think its the right one)
Help installing Firestarter i think, FW and forward/open some ports.
Help installing Beryl.
Any addons for Ubuntu/Beryl (if any) to make it work better, faster and to make things work that wouldnt work without them.
Cant think of anything atm but will ask when something comes to mind ^^
Heres more info of my pc [http://www.ciao.co.uk/Acer_Aspire_L200__6273743](http://www.ciao.co.uk/Acer_Aspire_L200__6273743)
Try to be very specific please
Thanks in advance

---

### Post by wpshooter on 2007-04-02
As far as your video card setup is concerned, if it were me, I would try installing the fglrx drivers from Synaptic and then I would edit the video card driver section of my /etc/X11/xorg.conf file and replace the driver specificaiton of ATI with fglrx.  And then reboot.

As far as the firestarter, I doubt that you need it.

As far as the Beryl is concerned, I would **NOT** install it.  From what I see on these forums it is going to wind up messing up your O/S.

Good luck.

---

### Post by Maestro23 on 2007-04-02
Graphics card: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Can also use the Envy script: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Firestarter:  It's in the Repositories.  Use Synaptic to install it.
Website: [http://www.fs-security.com/](http://www.fs-security.com/)

Beryl:  Install at your own risk: [http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

*Link to the Ubuntu guide is in my sig.

Welcome and good luck.

---

