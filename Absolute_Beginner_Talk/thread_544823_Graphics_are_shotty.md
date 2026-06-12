---
title: "Graphics are shotty"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by therunner on 2007-09-06
My graphics are pretty bad in Ubuntu.  So bad that I thought my graphics card went shot so I bought a new one.  Then ubuntu wouldn't work without the new drivers.  

I have an NVIDIA 6200 AGP  

The worst part of viewing is all text is blurry and faint.  I have adjusted everything that I know to adjust in the monitor settings and nvidia-settings.  But I think the problem is somewhere in the text setup.  I have adjusted the fonts to just about everyone in the font listing.  (Arial is not available) and I'm starting to get a headache from just typing this.  

I don't have this problem when running xp on the same machine and same monitor.

Any help would be great. 

-Todd

---

### Post by SOULRiDER on 2007-09-06
Did you check Font rendering? Thats a setting that usually annoys people. If you have an LCD monitor usually the best option is to choose Subixel Smoothing.

---

### Post by therunner on 2007-09-06
yeah I did, and still now luck. 

something else I noticed is the circles to select smilies are distorted as well.  Along with other web images.

---

### Post by therunner on 2007-09-06
I just switched over to my laptop because the graphics SUCK bigtime running ubuntu. 

I am going to try a restart and bring up XP just to make sure they are working good there before throwing a complete fit

-Todd

---

### Post by greybirds on 2007-09-06
Is the screen's resolution set to the one your monitor recommends? Select System > Preferences > Screen Resolution

---

### Post by Tomosaur on 2007-09-06
Did you remember to reconfigure the Xserver after installing your new hardware? Always worth a go! Open up a terminal then type the following:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg

```When it asks for your password, just use the same password you use to log on (although you won't see it being typed, so be sure to spell it properly).

Once you've done that, log out, then when you're at the login screen, hit Ctr+Alt+Backspace. This will restart the X server and (hopefully) have fixed your problem.

If that didn't work, try the following command:
```

sudo apt-get install nvidia-glx

```

If not, you can try downloading the Linux drivers for your card from the Nvidia website:
[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

Good luck!

---

### Post by therunner on 2007-09-06
> **Tomosaur said:**
> Did you remember to reconfigure the Xserver after installing your new hardware? Always worth a go! Open up a terminal then type the following:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg

```When it asks for your password, just use the same password you use to log on (although you won't see it being typed, so be sure to spell it properly).

Once you've done that, log out, then when you're at the login screen, hit Ctr+Alt+Backspace. This will restart the X server and (hopefully) have fixed your problem.

If that didn't work, try the following command:
```

sudo apt-get install nvidia-glx

```

If not, you can try downloading the Linux drivers for your card from the Nvidia website:
[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

Good luck!

No I haven't done this - however I tried something that maybe it was with the hard wire so I switched my DVI to RGB and now I am getting "Failed to start X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  Yes or No

Yes gives me 
X Window System Version 7.2.0
Release 22 Jan 07
Build OS Linux Ubuntu
Current OS Linux todd-desktop 2.6.20-16 Generic 
fri aug 31
build date 4 april 07
Module Loader Present
Markers: (--) probed, (**)from config file, (==) default setting,
(++) from command line, (!!) Notice, (II) Informational, (WW) Warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file "var/log/Xorg.0.log", time sep 6 21 40
(==) Using config file "/etc/x11/xorg.config
                              <ok>

This is the same error message that I received after installing the new graphics card.

---

### Post by therunner on 2007-09-06
BTW, when I had the rgb cable hooked up I received no screen at all.

---

### Post by therunner on 2007-09-06
I hit return and it gave me the statement 

"the x server has been disabled"  

Then gave me 

todd-desktop login

---

### Post by therunner on 2007-09-06
so I guess I need to know how to set up the graphical interface

---

### Post by Roger Mudd on 2007-09-06
First off, know that fonts are rendered differentlly on Windows, LInux and OS X. What looks good to others looks like a garbled mess to some.
If you need to get into the GUI on your linux machine (assuming you're posting to this forum from XP) you can log in at the text prompt you mentioned above and type "startx" without the quotation marks.
Give Tomosaur's above advice a shot an see if that clears things up for you - literally and figuratively. 
From your comments above about the lack of improvement when altering font settings, it sounds like the display is running at the improper resolution. The fact that you have both DVI and RGB inputs leads me to believe that you have an LCD. These can run at multiple resolutions, but they only look "good" at the recommended resolution. Judging from your comments, it sounds like your first step is to ensure that it's running at the correct resolution. The dpkg-reconfigure xserver-xorg command mentioned above should help you do that.
Be sure to read through this section of the Ubuntu community documentation:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
Probably offers more thorough advice than we've been able to offer here.

---

### Post by therunner on 2007-09-07
when I do startx 

no screens found
fatal IO error 104

---

### Post by therunner on 2007-09-07
failed to load module  "nvidia"
no drivers available

so I think all Ineed are the drivers

---

### Post by Roger Mudd on 2007-09-07
Have you tried hooking the DVI back up and re-booting?

---

