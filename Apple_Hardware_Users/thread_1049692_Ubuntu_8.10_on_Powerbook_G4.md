---
title: "Ubuntu 8.10 on Powerbook G4"
date: 2009-01-24
forum: Apple Hardware Users
---

### Post by bryan4134 on 2009-01-24
I have installed 8.10 on my Powerbook G4 (after using workaround to find the internal CD/DVD).  When it boots it correctly goes through yaboot but I cannot get a stable display - it is not slightly unstable where you can perhaps see the Ubuntu colors or perhaps some distorted writing - it looks like an incorrectly tuned in TV station (black, white, grey rolling lines and boxes).

I have also tried to load the 8.04 Live CD and I get exactly the same.

I have tried "Linux nosplash" options without success.

Prior to this I had Yellow Dog Linux installed and working on the machine.

Frustrated - any ideas please?

---

### Post by bryan4134 on 2009-01-25
With some tinkering I can now see the splash screen (stable) and progress bar but the GUI will not come up.  I can Alt-Ctrl-F1 to thee terminal and can log in etc. from there.

I have now reached the limit of my capability!  I am sure I need a properly configured xorg.conf or similar but don't know how to proceed from here..

Thanks for any wise suggestions...

---

### Post by mkvnmtr on 2009-01-25
On my G4 Ibook if I try to start up with an external hard drive or memory stick hooked up sometimes it rolls so bad I can barely see to click restart. If you have something connected unhook it and see if that helps.

---

### Post by swisskomputer on 2009-03-16
Exactly the same problem here on a Powerbook G4 Titanium. Installed Ubuntu 8.10 with the same problems you have. Now, I cannot get the video to work, except on a terminal (CTRL+ALT+F#). Tried to modify  or g.conf file, but it is all blank, nothing in it(???!!!). Have to boot the computer with nosplash video=atyfb.

Any help will be greatly appreciated.

---

### Post by avtolle on 2009-03-16
A blank /etc/X11/xorg.conf file is *status quo* on 8.10 ppc. There should be a file named, IIRC, xorg.conf.failsafe located within the /etc/X11 path. What I've done is copied that to xorg.conf, then went in and manually editied it. BTW, I'm on G4 Cubes, so my file likely would not work for you. One thing to suggest (I've an ATI Rage 128 Pro card) is to use the fbdev driver, if you want to try it. 

When booting, have you done Linux video=ofonly at the boot prompt?

---

### Post by swisskomputer on 2009-03-16
Thanks for your answer avtolle. I was messing around with xorg.conf file and got gnome to tell me it is working at a very low resolution and if I wanted to repair it. I'll take a look at the failsafe file now. Linux video=ofonly does not work for me, I have to use Linux video=radeonfb nosplash.

I also tried sudo dpkg-reconfigure -phigh xserver-xorg in order to create a new xorg.conf file, but this does not detect the monitor correctly.

---

### Post by avtolle on 2009-03-16
FWIW; once I had manually edited the xorg.conf file to get what I wanted/thought appropriate, upon restart, got the same message you have received. Undaunted, I proceeded forward, picked the Start in Low Graphics for this Session Only, continued on to end up on the desktop with the desired screen resolution, etc. I'm at a loss as to why this works, but no complaints.

---

### Post by hictio on 2009-03-16
> **bryan4134 said:**
> I have installed 8.10 on my Powerbook G4 (after using workaround to find the internal CD/DVD).  When it boots it correctly goes through yaboot but I cannot get a stable display - it is not slightly unstable where you can perhaps see the Ubuntu colors or perhaps some distorted writing - it looks like an incorrectly tuned in TV station (black, white, grey rolling lines and boxes).

I have also tried to load the 8.04 Live CD and I get exactly the same.

I have tried "Linux nosplash" options without success.

Prior to this I had Yellow Dog Linux installed and working on the machine.

Frustrated - any ideas please?

On what PB model did  you installed?
Last night installed 8.10 on a PB 1.5 GHz, 12", no problem at all (other than inserting the kernel module for the CD manually like posted a zillion times :D)
After the install, everything works, the WiFi works perfectly, after enabling the driver Broadcom B43 wireless driver.

The only thing I couldn't get to work its the Desktop Effects, I thought it was because I also had a blank '/etc/X11/xorg.conf' file, but Googling a bit, found a xorg.conf file for that model, but nevertheless, the Desktop Effect were a nogo.

I post the xorg.conf in case you are interested, again this was on a 12" PB @ 1.5 GHz, with the NVIDIA NV34M [GeForce FX Go5200]:

```

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/X11R6/lib/X11/fonts/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/X11R6/lib/X11/fonts/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/X11R6/lib/X11/fonts/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "en"
Option "XkbOptions" "lv3:lwin_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "AccelFactor" "0.07"
Option "MinSpeed" "0.6"
Option "MaxSpeed" "1.3"
Option "SHMConfig" "true"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34M [GeForce FX Go5200]"
Driver "nv"
BusID "PCI:0:16:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34M [GeForce FX Go5200]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

```

---

### Post by swisskomputer on 2009-03-18
Thanks for posting the xorg.conf file, hictio. I'll give it a try today. I gave it a try with the start in low-graphics mode, but still did not work, avtolle. The PB I am installing in is a PB G4 Titanium 500 MHz, ATI Radeon LY.

Found the problem! It has something to do with the /etc/gdm/gdm.conf file. Keep you posted.

---

### Post by aporeg on 2010-01-19
> **swisskomputer said:**
> Thanks for posting the xorg.conf file, hictio. I'll give it a try today. I gave it a try with the start in low-graphics mode, but still did not work, avtolle. The PB I am installing in is a PB G4 Titanium 500 MHz, ATI Radeon LY.

Found the problem! It has something to do with the /etc/gdm/gdm.conf file. Keep you posted.

Have you solved the problem you have @ swisskomputer???
i also have an PB 500mhz same probs never got it work 
please post you xorg.conf file and tell me if it works for you how you did it 

thanks in advice 

aporeg

---

### Post by linuxopjemac on 2010-01-20
try this:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"mac"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option		"UseFBDev"     "false"
	Option		"DynamicClocks" "true"
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"DisableGLXRootClipping" "true"
	Option		"AddARGBGLXVisuals" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"EnablePageFlip"	"true"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	#HorizSync	58-62
	#VertRefresh	75-117

	# 1152x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 92.39 MHz
        Modeline "1152x768_75"  92.39  1152 1224 1344 1536  768 769 772 802  -HSync +Vsync

        # 1152x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 86.02 MHz
        Modeline "1152x768_70"  86.02  1152 1224 1344 1536  768 769 772 800  -HSync +Vsync

        # 1152x768 @ 65.00 Hz (GTF) hsync: 51.87 kHz; pclk: 78.84 MHz
        Modeline "1152x768_65"  78.84  1152 1216 1336 1520  768 769 772 798  -HSync +Vsync

	# 1152x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 71.74 MHz
        Modeline "1152x768_60"  71.74  1152 1208 1328 1504  768 769 772 795  -HSync +Vsync

	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
        Modeline "1024x768_75"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
        Modeline "1024x768_70"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

	# 1024x768 @ 65.00 Hz (GTF) hsync: 51.87 kHz; pclk: 69.71 MHz
        Modeline "1024x768_65"  69.71  1024 1080 1184 1344  768 769 772 798  -HSync +Vsync

	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
        Modeline "1024x768_60"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x768_75" "1152x768_70" "1152x768_65" "1152x768_60" "1024x768_75" "1024x768_70" "1024x768_65" "1024x768_60"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "Module"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "vbe"
	Load "dbe"
EndSection
```

Radeon:
see [http://www.x.org/releases/X11R7.5/doc/man/man4/radeon.4.html](http://www.x.org/releases/X11R7.5/doc/man/man4/radeon.4.html)

---

### Post by linuxopjemac on 2010-01-20
If you want t o play with Compiz, try post #2 [here]("http://ubuntuforums.org/showthread.php?t=701470").

---

