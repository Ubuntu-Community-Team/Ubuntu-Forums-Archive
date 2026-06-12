---
title: "Widescreen resolutions with ATI on feisty  (GOT IT WORKING!)"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by MiniMe on 2007-05-07
I recently upgraded from Dapper to Feisty, followed many threads and guides about modifying the /etc/X11/xorg.conf file by adding the resolutions and modelines but nothing worked. It took me a while but I finally got my widescreen resolutions (1680x1050 and 1440x900 ).  Here's how:

I ended up installing opensuse (gnome) because I find suse makes it very easy to configure hardware. I was indeed able to easily configure the widescreen resolutions and the ATI X800 drivers were installed for me. I was tempted to just stick with Suse but I found Ubuntu to be snappier so I gave fiesty one more try after saving the xorg.conf file from Suse. 

After reinstalling Feisty, I installed the ATI drivers ( as per [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)) 

I then began pasting elements from the suse xorg.conf file to my ubuntu xorg.conf file. 

The stumbling block for me was the that I needed to have set 
	Driver      "radeon" (in the Section "Device" area) instead of  Driver   "fglrx"

Here's my xorg.conf file just incase it helps someone

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30-66
	VertRefresh  30-61
	Option	    "DPMS"
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
  Modeline 	"1600x1024" 138.76 1600 1704 1872 2144 1024 1025 1028 1061
  Modeline 	"1600x1000" 135.49 1600 1704 1872 2144 1000 1001 1004 1036
  Modeline 	"1400x1050" 122.61 1400 1488 1640 1880 1050 1051 1054 1087
  Modeline 	"1280x1024" 110.80 1280 1360 1496 1712 1024 1025 1028 1061
  Modeline 	"1440x900" 109.16 1440 1528 1680 1920 900 901 904 932
  Modeline 	"1280x960" 103.81 1280 1360 1496 1712 960 961 964 994
  Modeline 	"1366x768" 87.40 1368 1440 1584 1800 768 769 772 796
  Modeline 	"1280x800" 84.96 1280 1344 1480 1680 800 801 804 829
  Modeline 	"1152x864" 82.98 1152 1216 1336 1520 864 865 868 895
  Modeline 	"1280x768" 81.57 1280 1344 1480 1680 768 769 772 796
  Modeline 	"1024x768" 65.26 1024 1080 1184 1344 768 769 772 796
  Modeline 	"1280x600" 62.53 1280 1336 1464 1648 600 601 604 622
  Modeline 	"1024x600" 49.78 1024 1064 1168 1312 600 601 604 622
  Modeline 	"800x600" 38.85 800 832 912 1024 600 601 604 622
  Modeline 	"768x576" 35.54 768 792 872 976 576 577 580 597
  Modeline 	"640x480" 24.30 640 656 720 800 480 481 484 498
  Modeline 	"1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
EndSection


Section "Device"
	Identifier  "ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)]"
	Driver      "radeon"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
  SubSection "Display"
    Depth      15
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Good luck!

---

### Post by General_Ts0 on 2007-05-10
Thx for the info  I got it to work simply with the "Install the Driver the Ubuntu way" instructions from [the link]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") you shared.

x800 XL card

---

