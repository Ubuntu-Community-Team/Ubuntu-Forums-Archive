---
title: "confused, brain hurts... nvidia display issue."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by dbmata on 2006-07-07
Ok, I've been trying to figure this out for a couple hours.

I ran the nvidia driver download through synaptics... tried to follow the wiki, and well it didn't happen... lots of crying and a crash course in vi later...

I can boot now, into the DE, however, I have a dual monitor setup, and I can't figure out how to make it "work" in ubuntu... first, I want to set the single monitor it's using to my left monitor, which is sees as a "BenQ FP93GX" however, my other monitor is a Gateway POS, and it is seen as a "Default Screen".

So, I tried to do the logical thing, edited the xorg.conf to read "BenQ..." instead of "Default Screen" as the display... Yeah, broke the DE. Had to figure out Vi enough to fix it back and boot back into the DE.

So, my brain is scrambled, and I've got no clue my next step. How the hell do I force my BenQ screen as the default display?

---

### Post by dbmata on 2006-07-07
ok, after checking through other pages, I found that my install isn't working right. a clip from another xorg.conf reads:
Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "Videocard vendor"
	BoardName   "NVIDIA GeForce 6600 GT"
	BusID	    "PCI:1:5:0"
	Option	    "NvAGP" "2"
	Option	    "NoLogo" "1"
	Option	    "RenderAccel" "0"
	Option	    "CursorShadow" "1"
	Option	    "Coolbits" "1"
	Option      "ConnectedMonitor" "dfp, dfp"
	Option	    "NoPowerConnectorCheck"
	Option      "TwinView" "1"
        Option      "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
        Option      "SecondMonitorHorizSync" "31-82"
        Option      "SecondMonitorVertRefresh" "56-76"
#	Option	    "NoTwinViewXineramaInfo"
EndSection

Mine reads as if it is a generic video card. The actual hardware is a GeForce 7800 GTX.

---

### Post by NT4usB on 2006-07-07
Been there, done that!
Did you look at this guide?
[tseliots howto]("http://ubuntuforums.org/showthread.php?t=98456&highlight=nvidia")
It worked for me. The numbers(0)(1) get confusing, following where they go...
fwiw, here's my xorg.conf. Primary is the Viewsonic LCD. TV is to the right.
You should be able to replace the refresh rates and freq's for your monitors and make it work.

```
Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"
        # path to defoma fonts^M
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

Section "Monitor"
 #LCD^M
    Identifier     "Monitor[0]"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV^M
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci EndSection^M
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO" #or Composite etc^M
    Option         "TVStandard" "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60"
    EndSubSection
EndSection

```

---

### Post by dbmata on 2006-07-07
I'll give that a try and report back in the morning.
Thanks.

---

### Post by dbmata on 2006-07-08
bumpity, so I don't lose it.

BTW, if anyone wants to look at it, I'm having the problem still of my video card defaulting to the absolute wrong monitor.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ FP93GX"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"BenQ FP93GX"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by dbmata on 2006-07-08
ok, so I tried the tseliot guide to installing my nvidia drivers... didn't work at all. When I do the way described in the wiki, it works "fine".

What I don't get is why my xorg.conf is listing my nvidia driver as a default card and not as a 7800 gtx... am I missing a step?

When I follow the wiki explanation, it fails when I am supposed to run the command
```

sudo nvidia-glx-config enable

```
It fails and tells me I need to change the driver in the xorg.conf from nv to nvidia. I do that, and the desktop output also changes from monitor 1 to monitor 2.

I'm so confused, what am I doing wrong?

---

### Post by Nexusx6 on 2006-07-08
I had the same exact problem trying to get my nVidia card working. You're not missing a step, just something about the installer is screwy =/

However, good news! I found this link with so much better instructions than the wiki

> [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Good luck ;) Hope it helps

---

