---
title: "[SOLVED] Screen scewed after messing with settings"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Snoreis on 2008-02-01
So I'm currently having a problem with my screen.  Even though I've been advised against this, I used the graphical screen resolution editor, that ubuntu/gnome offers to try and get my dual monitor setup to work.  
 
Instead I screwed up my laptop screen to the point where I can only run in "terminal safe-mode"
I believe I changed the vendorname, but I don't know what to go back to.

I posted some information from the xorg.conf file

See what you think, and what else do I need to post.

I'm currently running an IBM thinkpad T41






> Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0

---

### Post by taurus on 2008-02-01
Try to reconfigure your X server again by pressing <Ctrl><Alt>F2 and login with your username and password.  Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, get back to GUI login screen with <Alt>F7 and restart X again with <Ctrl><Alt>Backspace.

---

### Post by Snoreis on 2008-02-01
Ok so after typing in that command i got:

> xserver-xorg postinst warning: overwriting possibly-costomized configuration file; backup in /ect/X11/xorg.conf.20080201192709

Then it worked, but now i have a very low screen resolution.

What is the best way to change this?

---

### Post by taurus on 2008-02-01
What graphic card do you have on your machine?  Which video driver did you pick when you ran that command to reconfigure your X server?

---

### Post by Snoreis on 2008-02-01
Well it never asked for a video driver, if thats what you mean.  Not sure if I was supposed to enter one somewhere.

Looking up videocard right now....

---

### Post by taurus on 2008-02-01
The output of this command should tell you which graphic card controller you have on that IBM.

```
lspci
```
Now, look in /etc/X11/xorg.conf to see which Driver it is using.

```
cat /etc/X11/xorg.conf
```

---

### Post by Snoreis on 2008-02-01
Ok so verything is fixed, thanks alot. 

After I can that first command you gave me, I was just able to go to 

-System
   -Prefrences
       -Screen resolution

and change it there.

I guess maybe there was a default video driver that worked just fine?  I'm not sure

---

### Post by Snoreis on 2008-02-01
also once I opened the xorg.conf file the settings had changed to > Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1400x1050"
        EndSubSection
EndSection



---

### Post by Paul86fxr on 2008-02-05
Also, be careful with the power management settings on the thinkpad t-41, I had the same problem, then, in case I didnt screw things up enough, I played with power management settings[sleep setting] then I could not get the display to wake up, what a nightmare! took me a while with a flashlight shining at the perfect angle on the screen, in the dark to reset the power management settings to wake up the display. People here thought I had finally lost my mind, huddled in the dark with a flaslight using my computer, or so they thought.:lolflag:

---

