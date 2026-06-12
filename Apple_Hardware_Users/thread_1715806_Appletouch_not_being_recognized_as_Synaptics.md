---
title: "Appletouch not being recognized as Synaptics"
date: 2011-03-27
forum: Apple Hardware Users
---

### Post by glitch003 on 2011-03-27
Hi, I'm trying to change some of the config options for my MacbookPro3,1 touchpad.  I added the relevant lines in my Xorg.conf file but I'm getting an error that no synaptics touchpad is recognized and then the module is unloaded.  This is the error:
```
[  2040.578] (**) Option "MaxSpeed" "1"
[  2040.578] (**) Option "AccelFactor" "0.02"
[  2040.598] (EE) Query no Synaptics: 6003C8
[  2040.598] (--) Synaptics Touchpad: no supported touchpad found
[  2040.598] (EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
[  2040.600] (EE) PreInit returned 11 for "Synaptics Touchpad"
[  2040.600] (II) UnloadModule: "synaptics"
[  2040.600] (II) Unloading synaptics
```

I know it's an appletouch and not a Synaptics trackpad but on the appletouch driver site it says I should be able to configure it using the synaptics driver: [http://www.popies.net/atp/](http://www.popies.net/atp/)

Here's my xorg.conf file in case this helps at all.  I copy-pasted the synaptics secton from the appletouch driver site I posted above.  Thanks in advance!!

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

        Section "InputDevice"
                Identifier      "Synaptics Touchpad"
                Driver          "synaptics"
                Option          "SendCoreEvents"        "true"
                Option          "Device"                "/dev/input/mice"
                Option          "Protocol"              "auto-dev"
                Option          "LeftEdge"              "0"
                Option          "RightEdge"             "850"
                Option          "TopEdge"               "0"
                Option          "BottomEdge"            "645"
                Option          "MinSpeed"              "0.4"
                Option          "MaxSpeed"              "1"
                Option          "AccelFactor"           "0.02"
                Option          "FingerLow"             "55"
                Option          "FingerHigh"            "60"
                Option          "MaxTapMove"            "20"
                Option          "MaxTapTime"            "100"
                Option          "HorizScrollDelta"      "0"
                Option          "VertScrollDelta"       "30"
                Option          "SHMConfig"             "on"
        EndSection

        Section "ServerLayout"
		Identifier 	"MyLayout"                
                InputDevice     "Synaptics Touchpad"
        EndSection

```

---

### Post by glitch003 on 2011-03-29
I had the problem solved by a user on another forum (justlinux.com).  Here is the fix for anyone else who may come across this forum post in google or whatever.


> **je_fro said:**
> I'm not sure what all has changed with your setup, whether or not you've only changed your xorg.conf...
In my case, xorg-server and a few other things were updated and required the addition of a section "InputClass" at the end of my current working xorg.conf. (I have the MBP previous to yours, with an ATI card - works great again...)

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
#	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "TouchPad" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
        Option "AIGLX" "on"
        Option "DRI2" "on"
EndSection

Section "Files"
	ModulePath   "/usr/lib64/xorg/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/OTF"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/100dpi/"
	FontPath     "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
	Load  "extmod"
	Load  "dri"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "TouchPad"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mouse0"
 	Option	    "Protocol" "auto-dev"
	Option	    "LeftEdge" "100"
	Option	    "RightEdge" "1120"
	Option	    "TopEdge" "30"
	Option	    "BottomEdge" "310"
	Option	    "FingerLow" "25"
	Option	    "FingerHigh" "35"
	Option	    "MaxTapTime" "180"
	Option	    "MaxTapMove" "220"
	Option	    "VertScrollDelta" "25"
	Option	    "MaxDoubleTapTime" "180"
	Option	    "MinSpeed" "0.40"
	Option	    "MaxSpeed" "2.00"
	Option	    "AccelFactor" "0.1500"
	Option	    "SHMConfig" "on"
	Option	    "TapButton1" "1"
	Option	    "TapButton2" "3"
	Option	    "TapButton3" "2"
	Option	    "VertTwoFingerScroll" "1"
#	Option      "HorizTwoFingerScroll" "1"
	Option	    "EdgeMotionUseAlways" "1"
EndSection

Section "Monitor"
	#DisplaySize	  340   220	# mm
	Identifier   "Monitor0"
	VendorName   "APP"
	ModelName    "Color LCD"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
#	Driver      "radeonhd"
#	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "M56P [Radeon Mobility X1600]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath	"/dev/input/event*"
	Option "SHMConfig" "on"
	Option "TapButton1" "1"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
EndSection

```

---

