---
title: "ATI Radeon Mobility 9700 - not fully functioning"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by meep_meep on 2007-06-20
Hi all,

I've only been using Ubuntu for a week now and I tried Wolfenstein: Enemy Territory and my graphics card (ATI Radeon Mobility 9700) driver couldn't cope with it.  I also tried the preview of the screensaver AntSpotLight and it kind of worked but slowly and my cpu started to work at 100%....

Anyway I have installed the restricted driver and I have tried to follow the instructions from this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

but after trying:

Compile the kernel module:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -ae


I couldn't 'build fglrx'  so I just installed the .deb packages by clicking on them via the installer.



I still can't run the AntSpotLight well, my cpu still goes crazy!!

My xorg.conf reads

Section "Device"
	Identifier  "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"        [COLOR="Blue"]<-------------   this was previously off but I changed it but it hasn't made any difference to my system[/COLOR]
	BusID       "PCI:1:0:0"
EndSection


[COLOR="Blue"]Should I keep OpenGLOverlay 'on' or 'off'?[/COLOR]

my fglrxinfo is

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


[COLOR="Blue"]Any other ATI Radeon Mobility 9700 users who can help me out?  I want to try linux gaming![/COLOR]

---

### Post by z708090 on 2007-06-20
Seems like we have to same problems [Link]("http://ubuntuforums.org/showthread.php?t=479426"). I have Mobility Radeon 9000 and can't get ET to give me decent fps. I'm going to see if my screen-savers are any better, that'd be good test.

---

### Post by Damanther on 2007-06-20
+1 for the albertomilone.com ENVY script.

---

### Post by meep_meep on 2007-06-20
cheers guys,  I'm running envy now and it seems to do a more up to date version of webpage that I was trying to follow.  I'll get back to you when I reboot and have tested it.

meep

---

### Post by meep_meep on 2007-06-20
It installed fine but when I tried AntSpotLight, my cpu still went crazy!  Is there anything else that I can do?

fglrxinfo gives

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6473 (8.37.6)

---

