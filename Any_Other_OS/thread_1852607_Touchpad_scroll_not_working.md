---
title: "Touchpad scroll not working"
date: 2011-09-30
forum: Any Other OS
---

### Post by josiahkeller on 2011-09-30
I have an Acer Aspire One 532h netbook, and almost everything works great.

The only thing, is that the side portion for scrolling doesn't work, and I can't do a multi-touch scroll either.

After doing a little research, I think that the computer isn't recognizing the touchpad as a touchpad, but instead thinks it's a regular mouse?

I'm currently running Mint 11, but it didn't work in Ubuntu 11.04 (which I was previously running) either.

Here are the contents of xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
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
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dbe"
	Load  "dri2"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
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

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
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

And the contents of 50-synaptics.conf:
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
EndSection
```

Please help! :popcorn:

---

### Post by josiahkeller on 2011-10-01
I don't suppose anyone *actually* knows the solution?):P

---

### Post by Perfect Storm on 2011-10-01
Moved to Other OS/Distro Talk.

---

### Post by xyzzyman on 2011-10-08
I am able to get two-finger scroll working on my Aspire 6930G by adding this file:

/usr/share/X11/xorg.conf.d/50-twofingerscroll.conf

```

Section "InputClass"
Identifier "touchpad catchall"
MatchProduct "SynPS/2 Synaptics TouchPad"
MatchDevicePath "/dev/input/event*"
Option "VertTwoFingerScroll" "on"
Option "HorizTwoFingerScroll" "on"
Option "EmulateTwoFingerMinW" "8"
Option "EmulateTwoFingerMinZ" "40"
EndSection
```

---

### Post by josiahkeller on 2011-10-08
> **xyzzyman said:**
> I am able to get two-finger scroll working on my Aspire 6930G by adding this file:

/usr/share/X11/xorg.conf.d/50-twofingerscroll.conf

```

Section "InputClass"
Identifier "touchpad catchall"
MatchProduct "SynPS/2 Synaptics TouchPad"
MatchDevicePath "/dev/input/event*"
Option "VertTwoFingerScroll" "on"
Option "HorizTwoFingerScroll" "on"
Option "EmulateTwoFingerMinW" "8"
Option "EmulateTwoFingerMinZ" "40"
EndSection
```

I tried that (replacing "SynPS/2 Synaptics TouchPad", with "AlpsPS/2 ALPS GlidePoint") and restarted my computer. No luck.

Another curiosity:
If I open the mouse settings window, go to the touchpad tab, and uncheck "enable mouse clicks with touchpad", I can still do tap-to-click.

I'm fairly certain the problem has to do with the touchpad not being recognized as a touchpad.

Can anyone help?

---

### Post by nbowser22 on 2012-01-23
I have an Identical problem in both distro's. However, my touchpad worked perfectly in fedora. I don't know what they did differently that makes it work but it does.

---

### Post by josiahkeller on 2012-01-24
> **nbowser22 said:**
> I have an Identical problem in both distro's. However, my touchpad worked perfectly in fedora. I don't know what they did differently that makes it work but it does.

Interesting...
I might try installing Fedora in my other partition, and see if it works for me.
Really though, Ubuntu *should* have a solution.

---

### Post by nkbielst on 2012-01-25
> **nbowser22 said:**
> I have an Identical problem in both distro's. However, my touchpad worked perfectly in fedora. I don't know what they did differently that makes it work but it does.

I had the same problem with my Dell. I'm running Fedora 16, and after an update, to kernel 3.1.9, it just started working. I'm sure there's a way to update Ubuntu, or Mint to the latest kernel, but I don't know how.

---

### Post by josiahkeller on 2012-01-25
I installed Fedora 16 on my other partition, and the scrolling works fine in that. So should a kernal update in Mint solve the problem there do you think?

---

### Post by nkbielst on 2012-01-25
> **josiahkeller said:**
> I installed Fedora 16 on my other partition, and the scrolling works fine in that. So should a kernal update in Mint solve the problem there do you think?

I think so. I read some time ago that the Alps drivers were going to be added as a kernel module in 3.1.8 or later kernel versions. I'm not familiar enough with mint to know if those modules will be included, but in theory, it should work.

---

