---
title: "Screen Resolution"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-03-22
I've installed Ubuntu 6.10 on my HP Pavilion laptop.  I have a 17" widescreen monitor, but the only option for screen resolution that I am given is 1024 x 768.  This doesn't look fantastically great.  I've tried to find out how to fix this problem through other resources but have as yet not been able to.  My xconfig file shows a lot more options than I am actually given in System>Preferences>Screen Resolution.  Thanks in advance for any help you can give me.

---

### Post by alienexplorers on 2007-03-22
Please post your xorg.conf file.

---

### Post by huzzak on 2007-03-22
Here it is:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by jadda on 2007-03-22
Modes "1280x800"

exchange the 1280x800 with the screen resolution you want and restart

---

### Post by huzzak on 2007-03-22
Right, mode 1280 x 800 is the mode that I want.  The only option it gives me is, inexplicably, 1024 x 768.

---

### Post by alienexplorers on 2007-03-22
You could try generating a modeline statement that would be added to your monitor section.  You can get a modeline at:
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

example: 1280x800 with refresh of 60

# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

---

### Post by jadda on 2007-03-22
have u tried to install a new driver?

xserver-xorg-video-intel

is a alternative driver in synaptic

---

### Post by Ptero-4 on 2007-03-22
Do you have modelines for your preferred resolution? is it set as the default one?

---

### Post by jonny on 2007-03-22
You need to use Synaptic package manager to install a package called 915resolution.  After installation, reboot and all will (probably) be well; if not, you need then to run this code:
```
sudo dpkg-reconfigure xserver-xorg
```and reboot again.  This fix will help almost anyone with screen resolution problems with Intel graphics. 

Sorry if this appears a little opaque.  The problem is logged with Ubuntu as a bug and an automatic  solution will probably be found in the next release or two.

---

### Post by huzzak on 2007-03-22
That did the trick.  Thanks a ton, jonny.

---

