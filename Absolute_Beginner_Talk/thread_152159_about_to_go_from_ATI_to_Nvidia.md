---
title: "about to go from ATI to Nvidia"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by DCJoeDog on 2006-03-29
I currently have an ATi card in my pc, but I want static free TV-Out, I watch lots of anime, and I happen to have a 6200FX card lying around.

now for the question, what should I set my video driver to so that when I log back into xserver so I can still have a picture, of course not accelarated, but I will get to that later.

thanks

---

### Post by Perfect Storm on 2006-03-29
Well firstly uninstall ATI Driver.

Then
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
```

To make sure that it's correct:
```
sudo gedit /etc/X11/xorg.conf
```

under Section Device change the driver to "nvidia"

That's iit.

Here's a howto Nvidia TV out: [http://doc.gwos.org/index.php/NvidiaTvOut](http://doc.gwos.org/index.php/NvidiaTvOut)

---

### Post by DCJoeDog on 2006-03-29
at what point do I switch the cards out?

---

### Post by Perfect Storm on 2006-03-29
Ah I forgot that :P


If you have an onboard gf card I'm sure you can do this without stepping out of X. Just set the driver to "vesa". Before switching.

But it will be best if you are in non-X envoriment and run 
```
sudo dpkg-reconfigure xserver-xorg
```
So it pick up the card correctly.



If I was you I'll start ubuntu infailsafe after replaced the ATI card with nvidia card. Then run 
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo nano /etc/X11/xorg.conf
```

and change nv driver to nvidia.
Safe and exit. reboot. Then it should pop you in X again with Acc.

---

### Post by DCJoeDog on 2006-03-29
the card is agp, and no onboard chip, any special instructions?

---

### Post by Perfect Storm on 2006-03-29
See above I've edited it to what I would do :)

---

### Post by DCJoeDog on 2006-03-29
as far as I can tell, opengl support is on, BUT I only have 640x480 resolution
but my xorg.conf file lists all my available resolutions

---

### Post by Perfect Storm on 2006-03-29
Can you post your xorg.conf.

---

### Post by DCJoeDog on 2006-03-29
I got it fixed, just kept on reading  lol

now onto the tv-out part, wish me luck LOL

EDIT: well, that was a bust

here is my xorg file, if someone wants to edit it and post a working clone setup then please, be my guest

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation 6200FX"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	250000
EndSection

Section "Monitor"
	Identifier	"Q71-3"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation 6200FX"
	Monitor		"Q71-3"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by DCJoeDog on 2006-03-29
I searched and searched and FINALLY found a solution to my probem

in the "Device" section I added some options, and now have 3d accel twinview clone mode on

this is my current device section

```
Section "Device"
	Identifier	"NVIDIA Corporation 6200FX"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "TwinView" "true"
        Option "TwinViewOrientation" "Clone"
        Option "TVOutFormat" "S-VIDEO"
        Option "TVStandard" "NTSC-M"
        Option "SecondMonitorHorizSync" "30-50"
        Option "SecondMonitorVertRefresh" "60"
        Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
	VideoRam	250000
EndSection
```

everything with the word "Option' was what was added in

---

