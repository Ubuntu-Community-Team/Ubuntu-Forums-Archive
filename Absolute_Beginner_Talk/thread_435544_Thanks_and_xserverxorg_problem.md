---
title: "Thanks and xserver/xorg problem"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2007-05-07
First of all thanks for the support that you guys have given us the newbies.

Problem

I can't configure for duel screen since I upgraded to feisty from drapper. Every time I try it my environment crashes and i have to reconfigure it.

please have a look at the xorg file and tell me whats wrong/missing ( for feisty)


section "Files"
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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
        Screen 0
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "Composite" #or SVIDEO etc 
        Option          "TVStandard" "NTSC-M" #or PAL-G etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Monitor" 
        Identifier "Monitor[1]" #TV 
        HorizSync 30-50
        VertRefresh 60 
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen" 
        Device "Device[1]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	      Screen 0 "Screen[0]"
              Screen 1 "Screen[1]" RightOf "Screen[0]"
	InputDevice "Configured Mouse" "CorePointer" 
        InputDevice "Generic Keyboard" "CoreKeyboard"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by ctsdownloads on 2007-05-08
Hi,

what card are you using and can you post the entire xorg file here in quote tool in the message options please.

If you are using NVIDIA, I have one thought.

---

### Post by justleen on 2007-05-08
i have pretty much the same, really.. 
I dont have the option  ""  under Section device, thats the only difference i can spot.

my xorg.conf:
> Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" 
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents" 
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled" 
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi" 
    FontPath        "/usr/share/fonts/X11/misc"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom" 
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY 
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom" 
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY 
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom" 
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY 
EndSection

Section "Monitor"

 #Primary display
    Identifier     "Monitor[0]"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"

 #TV
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

 #adjust using 'lspci' or cat /proc/pci
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
    Option         "AddARGBGLXVisuals" "True" 
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display" 
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8 
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480" 
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection 
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection 

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO" #or SVIDEO etc 
    Option         "TVStandard" "PAL-G" #or NTSC etc
    Option         "ConnectedMonitor" "Monitor[1]"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "800x600_60"
    EndSubSection
EndSection



---

### Post by Steve H on 2007-05-08
Are you using the Restricted Drivers for your Nvidia card? If you are then try typing the following in a terminal window.

```
sudo nvidia-settings
```

Set up your screens the way you want them, save to your xorg.conf, log out and restart X (ctrl-alt-backspace). I quite often turn multiple screens on and off this way and it works fine.

Hope that helps.

:)

---

### Post by ctsdownloads on 2007-05-08
Steve nails it...lol, you stole my thunder. :)

---

### Post by Steve H on 2007-05-08
I do my best, ctsdownloads......

:)

---

