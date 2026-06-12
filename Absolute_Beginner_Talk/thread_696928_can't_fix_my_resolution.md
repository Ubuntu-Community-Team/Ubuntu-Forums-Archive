---
title: "can't fix my resolution"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Knacker on 2008-02-14
I'm running Gutsy on a T61 with nvidia 140m. Last night I plugged my projector in for the first time and used the "screens and graphics" utility in ubuntu to configure the resolution. I did it kinda fast, so I'm not sure exactly what I did. When I unplugged my projector, the resolution on my laptop screen was way wrong and I've not been able to get it back to normal (WXGA+ - 1440x900). I tried using "sudo dpkg-reconfigure xorg-xserver" using all the defaults and "sudo dpkg-reconfigure  -phigh xorg-xserver" . This left me with a screen that went dead before I got to login. After manually replacing xorg.conf with the back up, I'm left back where I was (though more than a bit hesitant trying to figure this out using the fixes that exist on the forums). I recently turned off compiz-fusion (no change) and turned it back on. Now my CPU is running way up with nautilus using 50-70% of my CPU. This is driving me crazy, I'm a total linux noob, trying hard to make ubuntu work for me. If someone out there can help me with a relatively simple fix to this, I'd be grateful. All I want to do is return my resolution to "normal"! 
Thanks so much in advance.

---

### Post by Knacker on 2008-02-14
Hm...am I asking this question the wrong way? Please help me. :)

---

### Post by jaytek13 on 2008-02-14
Can you post your /etc/X11/xorg.conf file?

---

### Post by stevejesus on 2008-02-14
When you did "dpkg-reconfigure xserver-xorg", did make sure to select the driver that bast matches your hardware?
Also, did you be sure a select 1440x900 as a usable mode when you ran this script?

---

### Post by Knacker on 2008-02-14
Here's what I think are the relevant sections of my xorg.conf

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"640x480@60"	"800x600@56"	"800x600@60"	"1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #            
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #            
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #            
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

---

### Post by Knacker on 2008-02-14
> **stevejesus said:**
> When you did "dpkg-reconfigure xserver-xorg", did make sure to select the driver that bast matches your hardware?
Also, did you be sure a select 1440x900 as a usable mode when you ran this script?

I think so. I more or less used the defaults. With the exception of choosing 1440x900 as my resolution. I believe I selected the proprietary nvidia driver. 

I'd go in and manually edit my xorg.conf, but I really don't know where to start with that (despite partial references in the formus to doing this). 

Thanks so much for your replies!! :)

---

### Post by stevejesus on 2008-02-14
Well, run 
```
sudo dpkg-reconfigure xserver-xorg
```
again, and this time make SURE to select the mode that matches your resolution.  This should most certainly solve your problem.

Also, when I looked at what you posted from your xorg.conf, I noticed that 1440x900 is only mentioned in the description of your display.  It is not listed as a mode.  So run this script.

---

### Post by Knacker on 2008-02-14
> **stevejesus said:**
> Well, run 
```
sudo dpkg-reconfigure xserver-xorg
```
again, and this time make SURE to select the mode that matches your resolution.  This should most certainly solve your problem.

Also, when I looked at what you posted from your xorg.conf, I noticed that 1440x900 is only mentioned in the description of your display.  It is not listed as a mode.  So run this script.

Yes, I noticed that too...I'd change it manually, but I don't know what to put in there to correct it. I'll try running the script again...and hope for the best. Thanks again for your help and sorry if I bother with a stupid question.

---

### Post by Knacker on 2008-02-14
> **stevejesus said:**
> Well, run 
```
sudo dpkg-reconfigure xserver-xorg
```
again, and this time make SURE to select the mode that matches your resolution.  This should most certainly solve your problem.

Also, when I looked at what you posted from your xorg.conf, I noticed that 1440x900 is only mentioned in the description of your display.  It is not listed as a mode.  So run this script.

ok: when I get to the point in the recofiguration script when it asks me about which video modes to use, none are selected by default and I can't figure out how to select them. Stupid quesiton, I know, but how do I select them? 
Thanks!

---

### Post by Knacker on 2008-02-14
nevermind, just figured it out (space bar!). ;)

---

