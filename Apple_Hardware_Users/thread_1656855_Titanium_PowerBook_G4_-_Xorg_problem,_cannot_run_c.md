---
title: "Titanium PowerBook G4 - Xorg problem, cannot run configure"
date: 2010-12-31
forum: Apple Hardware Users
---

### Post by opus68 on 2010-12-31
Hi all,

I installed Ubuntu 10.10 on a PowerBook G4 400MHz ([PowerBook3,2]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_400.html")). I managed to boot into console mode, however Xorg would not work. The problem must have been a failure to auto-configure Xorg for the built-in ATI Rage Mobility 128. I managed to create an /etc/X11/Xorg.conf file based on what I found [here]("http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128"). 

However, this would require me to use the "NoInt10" option, as has been explained in another [post]("http://ubuntuforums.org/showpost.php?p=3228792&postcount=5").

It appears that the same problem crashes Xorg when running "Xorg -configure" - see log attached.

Is there any way to tell Xorg not to use Int10 when configuring?

Thanks and happy New Year!
-Michael.

---

### Post by linuxopjemac on 2010-12-31
give me the output of your xorg.conf file please:
```
cat /etc/X11/xorg.conf
```
paste the output here pls

---

### Post by opus68 on 2011-01-01
Here's my xorg.conf - I have glued it together from the output Xorg -configure created before it crashed as well as from this [source]("http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128"). I am not sure how complete or even "correct" it is.

Commenting out Option "NoInt10" "true" will cause the server to crash when starting.

I am also attaching it as a file.

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen         0  "Default Screen" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "unix/:7100"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "dri2"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option       "DPMS"
	HorizSync    30-100
        VertRefresh  50-160
	Modeline     "1152x768_60.00" 71.75 1152 1216 1328 1504 768 771 781 798 -hsync +vsync
	Option       "PreferredMode" "1152x768_60.00"	
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver      "ati"
	BusID       "PCI:0:16:0"
	Option      "UseFBDev" 			"false"
	Option	    "SWcursor"			"true"
	Option	    "ForcePCIMode"		"true"
#	Option	    "XAANoOffscreenpixmaps"
	Option	    "NoInt10"			"true"	
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor    "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth     1
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes     "1152x768_60.00" "896x600" "720x400"
	EndSubSection
EndSection

---

### Post by linuxopjemac on 2011-01-01
I don't see anything wrong here. Give me the output of the following after you tried to get a GUI with the xorg.conf file you just provided:

```
cat /var/log/Xorg.0.log
```

I am not sure if it's the one you gave me in the 1st post.

---

### Post by linuxopjemac on 2011-01-01
I have the same computer, I use the following xorg.conf file in MintPPC 9:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"false"
	Option		"SWcursor" 		"true"
	Option 		"ForcePCIMode" 		"true"
	Option 		"XAANoOffscreenPixmaps"
Option "NoInt10" "true"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
# 1152x768 59.78 Hz (CVT) hsync: 47.71 kHz; pclk: 71.75 MHz
Modeline "1152x768_60.00" 71.75 1152 1216 1328 1504 768 771 781 798 -hsync +vsync
# 896x600 59.96 Hz (CVT) hsync: 37.41 kHz; pclk: 42.50 MHz
Modeline "896x600_60.00"   42.50  896 928 1016 1136  600 603 613 624 -hsync +vsync
# 720x480 59.71 Hz (CVT) hsync: 29.85 kHz; pclk: 26.75 MHz
Modeline "720x480_60.00"   26.75  720 744 808 896  480 483 493 500 -hsync +vsync
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
Option "PreferredMode" "1152x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768_60.00" "896x600_60.00" "720x480_60.00" "640x480_60.00"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by opus68 on 2011-01-02
Both files work. It appears bizarre - I re-edited my file by hand and it suddenly worked. I suspect that during the crash of 'Xorg -configure' some invisible characters may have been introduced which caused the problem.

However, the '-configure' options still doesn't work. It still crashes, yielding the log file I originally attached.

Anyhow, I do appreciate your support, Jeroen, thanks a lot!

I find responsiveness a bit sluggish on my TiBook, though - I will give MintPPC 9.1 a shot :)

---

### Post by linuxopjemac on 2011-01-02
> I find responsiveness a bit sluggish on my TiBook, though - I will give MintPPC 9.1 a shot

You won't be disappointed, I'm sure.
[http://mac.linux.be/content/xorgconf-powerbook-g4-titanium-500-mhz](http://mac.linux.be/content/xorgconf-powerbook-g4-titanium-500-mhz)
just before you reboot, install xorg.conf:
```
wget http://mac.linux.be/files/xorg/powerbook10.txt
sudo mv powerbook10.txt /etc/X11/xorg.conf
```

Good luck!
Also install firmware-linux-nonfree from the non-free repository. It'll improve your X experience.

---

### Post by opus68 on 2011-01-03
So, I did move to MintPPC 9.1 and am more than happy about it. It has truly breathed new life into my venerable TiBook. Compared to the experience with Gnome under Ubuntu 10.10 (and relative to my expectations...) Linux Mint LXDE is very responsive and offers a smooth GUI experience. 

I also installed firmware-linux-nonfree, achieving &#8764;38 fps on glxgears using Linuxopjemac's xorg.config.

Although some might argue that Mint LXDE offers less eye candy, I still find it visually very appealing.

The distribution appears to be well-integrated with the underlying hardware, battery meter and laptop sleep worked with no further tweaking necessary.

Installation has been seemless; in addition, I recompiled netatalk with OpenSSL support to access the maching through afp.

Conclusion: I can recommend MintPPC 9.1 to anyone running older PowerBooks, you will be positively surprised about the performance of the system.

---

