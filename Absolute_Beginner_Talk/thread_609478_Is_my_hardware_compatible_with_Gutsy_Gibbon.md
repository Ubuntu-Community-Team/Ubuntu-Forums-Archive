---
title: "Is my hardware compatible with Gutsy Gibbon?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by port23user on 2007-11-11
I'm going to be installing Gutsy Gibbon on my computer soon and would like opinions on the compatibility of my hardware.  My main purpose for this machine is web programming and I have four monitors connected to two dual-ported video cards.  Here are the components:
Gigabyte 945GZM-S2 motherboard
MSI NX7300LE PCI-e video card (Nvidia 7300LE)
Chaintech FX5200 PCI video card (Nvidia FX 5200)

Has anybody had any compatibility issues with this hardware?  Any tips on configuration of this and anomalies would be appreciated too.  Thanks in advance.

---

### Post by mivo on 2007-11-11
The best way to find out is to download the Live CD and boot from it. This will not change anything that is on your computer, so it is perfectly safe to do. (Though really testing the four monitors setup will be tricky since you need the Nividia binary drivers for this.)

---

### Post by port23user on 2007-11-11
Yea, I tried running the live cd and it both of my monitors on the first video card a blank screen.  The screens connected to the second video card flickered colors.  I restarted and booted into graphics safe mode and the two latter monitors seemed to work well.  I'm guessing I'll need to install the drivers myself.  I noticed somebody with one of the same video cards as me used Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)).  Would this be wise?

---

### Post by matthewcraig on 2007-11-11
Have you considered purchasing a computer from a company like System 76 with Ubuntu already loaded on hardware that is known to work?  They will also support your hardware problems if you can't get something to work in Ubuntu.

---

### Post by Paulmd on 2007-11-11
> **port23user said:**
> I'm going to be installing Gutsy Gibbon on my computer soon and would like opinions on the compatibility of my hardware.  My main purpose for this machine is web programming and I have four monitors connected to two dual-ported video cards.  Here are the components:
Gigabyte 945GZM-S2 motherboard
MSI NX7300LE PCI-e video card (Nvidia 7300LE)
Chaintech FX5200 PCI video card (Nvidia FX 5200)

Has anybody had any compatibility issues with this hardware?  Any tips on configuration of this and anomalies would be appreciated too.  Thanks in advance.

Taken individually, your parts are all pretty much standard stuff: however you're doing something unusual; running 4 monitors.

You'd definitely want to install nvidia's proprietary graphics drivers to have any chance of getting your quad monitor setup working.

[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) 

This driver is used for both the fx series and the 7300. I suppose you'll have to see what happens. (let us know whether or not it works)


I found a Wiki Re Multiple video cards, if installing nvidia's driver doesn't do the trick by itself.. It's for gentoo, but should be more or less compatible.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

In windows, I would be quite sure this would work for windows 2000 and newer. Up to 10 monitors. In linux... that sort of information doesn't seem to be easy to obtain.

This blog isn't very hopeful. Basically, it implies that support for more than 2 monitors doesn't exist in Ubuntu.... at least as of February 07.

[http://www.lockergnome.com/it/2007/02/20/accomplishing-the-obvious/](http://www.lockergnome.com/it/2007/02/20/accomplishing-the-obvious/)

---

### Post by P4man on 2007-11-11
From what I read, nVidia's twinview only supports 2 monitors.

Xinerama should support as many as you like, but with some serious drawbacks. For instance, last time I tried this, gnome seemed to have no idea about my setup, so if I maximized an application, it would be stretched across 2 monitors. Twinview worked like a charm though, but the readme specifies 'up to 2 monitors'. With 2 videocards, it may or may not work to drive 4 monitors, but I wouldnt bet on it.

---

### Post by port23user on 2007-11-24
I installed Ubuntu on my computer and right now only two of the screens are working.  Here is what I did:
1. Installed the proprietary Nvidia drivers
2. Ran X autoconfig
3. Edited xorg.conf to use the proprietary drivers
I think I also did something in the nvidia-settings tool.  I got the VGA ports on both cards to work (so I have two monitors working right now).  Now I'm trying to get the dual-headed functionality to work.  Also, I can't drag windows between screens.  Any ideas?  Here's my xorg.conf file:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen1" 0 0
	Screen      1  "Screen0" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
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
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL E197FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor1"
	VendorName   "DEL"
	ModelName    "DELL E196FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5200]"
	BusID       "PCI:2:1:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card1"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7300 LE"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

---

### Post by Paulmd on 2007-11-24
> **port23user said:**
> I installed Ubuntu on my computer and right now only two of the screens are working.  Here is what I did:
1. Installed the proprietary Nvidia drivers
2. Ran X autoconfig
3. Edited xorg.conf to use the proprietary drivers
I think I also did something in the nvidia-settings tool.  I got the VGA ports on both cards to work (so I have two monitors working right now).  Now I'm trying to get the dual-headed functionality to work.  Also, I can't drag windows between screens.  Any ideas?  Here's my xorg.conf file:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen1" 0 0
	Screen      1  "Screen0" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
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
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL E197FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor1"
	VendorName   "DEL"
	ModelName    "DELL E196FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5200]"
	BusID       "PCI:2:1:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card1"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7300 LE"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```


1st: Make a backup of the xorg.conf file. I'm guessing here.

Both places where it says 

```
       #Option     "DualHead"           	# [<bool>]
```

change it to

```
       Option     "DualHead"  "True"          	# [<bool>] 
```

---

### Post by port23user on 2007-11-24
Could it be an issue that I'm using a VGA monitor connected to the DVI port through a converter?

---

### Post by P4man on 2007-11-24
No, that DVI convertor is not causing it. You need to enable twinview. 

Run nvidia config utility:
```
gksudo nvidia-settings
```

in "X server display configuration" click on "configure" then choose TwinView. May need to restart for it to work.

---

### Post by port23user on 2007-11-24
Unfortunately, I tried "gksudo nvidia-settings" and none of my changes seem to take effect.  I make a change and then click "Save to X Configuration File" and then reboot and nothing in my x config file or in the nvidia-settings box reflect the changes I made.  Any ideas what that might be?

---

### Post by P4man on 2007-11-24
I've had some trouble with the nvidia utility not changing my xorg.conf. Make a backup of that file first, then run the utility again, but preview the changes. Copy paste the previewed xorg.conf into the actual file and save it (as root).

---

### Post by port23user on 2007-11-24
It turns out that when I switched my third monitor to use the older (Nvidia FX PCI) video card, it worked.  I'm not sure why, but at least now it's getting picture.  My problem now is fixing how windows are spanned.  The taskbar(?) spans all the way across the two screen.  When I open windows in these monitors, they don't display a window bar, but just force them to the upper-left-most available spot on the screen.  What might be causing this?  I want to be able to open windows on these screens and to be able to drag them across.

---

