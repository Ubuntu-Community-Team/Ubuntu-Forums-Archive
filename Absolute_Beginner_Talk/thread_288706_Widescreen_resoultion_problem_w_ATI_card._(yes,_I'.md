---
title: "Widescreen resoultion problem w/ ATI card. (yes, I've already searched!)"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by tommaisey on 2006-10-30
I've just installed Edgy, I'm a first time Linux user so you'll have to go slow. Everything works great, except I can't select my widescreen monitor's native resolution in the Screen Resolution Preferences. I have searched and found a few articles trying to help with this, but none have helped me. Most seem to revolve around adding "1400x900" to the relevant bit in xorg.conf - but as you can see below I've tried that.

It's worth mentioning that I'm using an ATI Radeon 9600 card, and have installed the appropriate proprietary driver. When I initially installed the driver, I was able to select 1400x900 and everything was hunky-dory. But after rebooting, that option had disappeared. Thanks very much for your (anticipated) help :) 

```
Section "Device"
	Identifier "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver "ati"
	BusID "PCI:1:0:0"
EndSection

Section "Device"
	Identifier "aticonfig-Device[0]"
	Driver "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier "Acer AL1916W"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "aticonfig-Monitor[0]"
	Option "VendorName" "ATI Proprietary Driver"
	Option "ModelName" "Generic Autodetecting Monitor"
	Option "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor "Acer AL1916W"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "1400x900"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1400x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device "aticonfig-Device[0]"
	Monitor "aticonfig-Monitor[0]"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		ViewPort 0 0
	EndSubSection
EndSection
```

---

### Post by tommaisey on 2006-10-30
OK, I've found the solution [here]("http://ubuntuforums.org/showthread.php?t=281516"). I did the same, but used a program called "xorg-edit" to generate the Modeline. Cheers.:D

---

