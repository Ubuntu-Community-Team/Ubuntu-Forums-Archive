---
title: "[SOLVED] (Important) Samsung Widescreen SyncMaster 206bw Screen Problems"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2008-01-04
Hello all:

I recently (about 10 hours ago) reinstalled Ubuntu 7.10 on my desktop computer (specs in signature). From the start of the installation I used my brand new Samsung SyncMaster 206BW (20 inch widescreen). The resolution  was not the best, but after I installed my graphics card (envy), it picture quality was awesome. The display even looked wide (not just stretched).(resolution now=1680 X 1050).

However, about 40 minutes ago, I went to -->System-->Administration-->Screens and Graphics.
Here I found that the screen registered on the computer was named "Custom1". Thinking it would be a good idea, I changed the display to the Samsung --> SyncMaster 206BW. Then it asked me to log off in order for the changes to take effect. So I did.

**The Problem:**
My monitor now cannot display in 1680 X 1050, any other setting shows up stretched, the bottom toolbar is not visible even though I can see it if I do "Super+scoll up".

How can I change it back to the original settings?

Please help! Thanks!

---

### Post by sirgogo on 2008-01-04
Oh phew!

I solved the problem. For some reason the modeline disappeared from the xorg file. Heres not I fixed my problem.

```
sudo nano /etc/X11/xorg.conf
```

I scrolled down to the Monitor Section that looked like this:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 206BW (Analog)"
        Horizsync       30-81
        Vertrefresh     56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

```

Since the 1680 by 1050 modeline was missing, I added it:
```
modeLine "1680x1050@65" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
```.

Next, I scrolled down to the Screen Section that looked like this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
                Virtual 1600    1200
                Modes           "1600x1200@65"  "1400x1050@60"  "1280x960@75"   "1280x1024@60"  "1280x960@60"   "1280x1024@75"  "1152x864@75"   "1024x768@60"   "1024x768@70"   "1024x768@75" $
        EndSubSection
```.

Because the 1680 by 1050 mode was missing, I, once again, added it my self.

In the "Modes" section: ```
 "1650x1050@65
```
In the "SubSection "Display": ```
Virtual 1650    1050
```.

I restarted the X using:
```
sudo /etc/init.d/gdm stop
```
and then started it back up with:
```
sudo /etc/init.d/gdm start
```.

Now my monitor is rockin' :guitar:.

---

### Post by LarryJ2 on 2008-01-15
Curious if  "gksu nvidia-settings" brings up the nVidia Settings Dialog menu window for you?

If it does, and after manipulation so you are satsified with the resolution etc ,  this utility seems to write a proper xorg.conf including a working twinview dual monitor setup.

I agree that  KdeMenu->SystemSettings->MonitorandDisplay utility is faulty.   Changing anything from within there guarantees a non-graphical boot requiring me to boot in failsafe text mode, retrieve my working copy of xorg.conf, and replace the messed up xorg.conf that  the Kde utility created.

If you try to adept_manager -> install -> nvidia-settings,   the package manager deletes your nvidia-glx-new driver!!!  So  gksu nvidia-settings is the only backdoor in??

---

### Post by sirgogo on 2008-01-21
Yeah I can access the nVidia Setting Menu.

However, it wasn't detecting my display. It kept displaying CRT. And if I tried changing any settings, it would get all messed up when I restarted the X or rebooted. Kinda weird.

I don't know what was up, but the terminal worked. It might have something to do with the way ENVY compiled the X-org file. Hmm...

---

