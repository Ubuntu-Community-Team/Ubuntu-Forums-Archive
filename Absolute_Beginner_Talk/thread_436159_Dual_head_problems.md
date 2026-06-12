---
title: "Dual head problems"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by fallen_seraph on 2007-05-07
Hello,
I just recently installed Ubuntu 7.04 on my system with an nVidia 7900 GT. I proceeded to use automatix to install nvidia drivers(which was much easier than doing it manually). Twinview works, however I find that it irritates me as it stretches the desktop across both my CRT and LCD. This also affects anything that is fullscreened, such as firefox.

I prefer having the menus on my LCD screen, which is to the right of my CRT. Linux (no matter the distro) all put the main screen as the left and this doesn't really work for me. Due to the layout of my desk, I want the right most monitor to be the main monitor without any strange work arounds such as setting the CRT to the right of the LCD in xorg.conf. In windows, it's fairly simple to set a default screen that applications are launched to.

Now, I have tried using nvidia-settings (as root) to set seperate x screens. This is where the problem is. When i do this, and reboot, the CRT is the only screen that stays on, afterwards my LCD clicks off and gives a NO SIGNAL. After the reboot, under nvidia-settings the LCD is listed as disabled. I promptly respond with a WTF, and try this a couple more times. No success.
Why is my LCD screen not being utilized? I might have tried to use Xinerama (can't remember), however I know this is do-able as I just installed over an OpenSuSE 10.2 install which had dual head working for the most part.

So, in summary:
1- How do I set my right monitor as the default monitor (as in, the one new applications and other popups appear in)?
2- How can I fix this seperate screen disabling problem?

Much thanks in advace
-Seraph

---

### Post by orb9220 on 2007-05-07
[http://www.zulustips.com/2007/04/01/dual-monitors-howto.html](http://www.zulustips.com/2007/04/01/dual-monitors-howto.html)

My xorg

> Section "Monitor"
    Identifier     "A75f"
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	[B]Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"[/B]
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

There is a command above that might help in bold Right of or Left of might help.

Also Howto's in my sig hope they help.

---

### Post by Nythain on 2007-05-07
think they were trying to avoid that whole "big desktop" factor of twinview...
if at all famliar with xorg.conf and editing the different Sections... you can tweak mine and change monitor 0 to use your lcd and turn on Xinerama by changing the "0" to "1" and it should meet your needs... 
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "STAC Electronics KDS VS-70"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          0
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          1
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```
in a nutshell actually, all you have to do is take your current Seperate X screen xorg.conf setup generated by gksudo nvidia-settings, make sure
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection
reads "1" instead of "0" and set
Identifier "Screen0" to use wichever monitor is already set up as your lcd, that way its going to make the first screen the monitor, then set Screen 1 to be leftof Screen 0 and make sure Identifier "Screen1" is set to use "Monitor1"

if any of that made sense, its really easier than i just made it sound, i swear

---

