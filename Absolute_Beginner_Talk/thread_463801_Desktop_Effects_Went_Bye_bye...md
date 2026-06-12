---
title: "Desktop Effects Went Bye bye.."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by esc1 on 2007-06-04
Desktop effects worked after intstall but was buggy. 

I've installed the open source ati drivers and I think I have it working right.  

From fglrx:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro
OpenGL version string: 2.0.6334 (8.34.8)


Somewhere along the way I've lost the ability to enable desktop effects.  Now I get this error:

The Composite extension is not available.

I've also tried to get Beryl working for fun and that's a no go as well.  

Here is the xorg.conf

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
	Option		"Composite"	"0"
EndSection

---

### Post by diatribe on 2007-06-04
I'm fairly sure that under extensions composite should be enabled not disabled, also the composite 0 is unnecessary

---

### Post by pappapump on 2007-06-04
Thats just the composite out port for the comp to TV function and almost never works right with either ATI or Nvidia.
While you're at it, check your refresh rate  and set it to 60 hz or better,then set your screen to the highest resolution and try a GL screensaver.
If that works you may have a broken application or a missing dependency.

---

### Post by esc1 on 2007-06-04
Edit it to look like this?:

Section "Extensions"
Option "Composite" "Enable"
EndSection


... Haven't changed that yet... but my GL screen savers work just fine.

---

### Post by pappapump on 2007-06-04
disable composite, otherwise the card may try to go into dual screen mode and REALLY mess you up.

---

### Post by esc1 on 2007-06-04
So I guess that means a broken application or a missing dependency?

How do I troubleshoot that?

---

### Post by PandaGoat on 2007-06-04
Fglrx drivers do not support composition--you can not have direct rendering and composition at the same time.  Open ATI driver's do, but lower your performance compared to fglrx.  Beryl requires composition to work, which is why it worked when you were not using fglrx.

---

### Post by freebird54 on 2007-06-04
Well - you have two choices to get effects working.  I'm going to assume Feisty here, from the way you refer to the effects :)

With that video card you can either:

run with fglrc drivers, Composite disabled, and few other things set, and IN AN XGL session you can run Beryl or Compiz...

*OR*

run with the ati (radeon) drivers, Composite enabled, NO XGL, and a lot of OTHER things set.  This is somewhat slower on the screen, but also more compatible with more things.  The way you have your xorg.conf - it won't do either very well!

So - which way would you like to go?  I have setups for both handy (fglrx on Edgy, ati on Feisty, fglrx on Feisty) - let me know!

---

### Post by esc1 on 2007-06-04
Rather go with the fglrc freebird. :)

---

### Post by freebird54 on 2007-06-04
OK - here is my (functional) xorg.conf using fglrx

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
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection
[B]
Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection[/B]

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
					        # /dev/input/event        Option      "UseFBDev" "true"
        # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                # /dev/input/event
                                                # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to         Option      "UseFBDev" "true"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                # /dev/input/event
                                                # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"       # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"       # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

[B]Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
*        Option      "UseFBDev" "true"*
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection[/B]

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection
[B]
Section "Extensions"
        Option      "Composite" "Disable"
EndSection[/B]

```

Things which need to be set are in **bold**.  (mostly you had them).  Things you don't have are also ***italic***.  At the end, you had the same option twice - at best unnecessary  (it's either 'disable' OR its '0' )  So IF you make the change, AND are running in an XGL session, Beryl should work fine.  However, you lose some games and so on that will NOT be happy with XGL instead of AIGLX.

If you're not sure how to get XGL, this link should help (It's what I used originally to get it going)  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

or this one (graphical)  [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I would suggest leaving the XGL session as an option at login - Beryl is not yet 100% stable.  However - it does usually 'fail-safe' back to Metacity when it has troubles.  Hope this gets it all for you!

---

### Post by kic on 2007-06-05
Freebird, if you don't mind, could you post your xorg.conf for the ATI (non-fglrx) drivers as well? I'm sort of in the same boat as I'm trying to fix my video driver issues after attempting (and failing) to get OpenGL to work.

Right now I'm stuck using a plain old Gnome session because I've been unable to get the XGL session to work again, and based on what you said, it kind of sounds like it'd be better for me to go the other way instead. (At the very least, I'd like to try so I can compare.)

Thanks much! I'll also be trying a few things in the meanwhile to get my XGL session working again (I miss Beryl...).

---

### Post by freebird54 on 2007-06-05
Once again - I'll highlight the changes with **bold** - as some of them are DIRECTLY opposite to the fglrx settings.  There are also quite a few more in the 'device' section!

Here goes

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"dbe"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

[B]Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection[/B]

Section "Monitor"
	Identifier	"Samsung 900IFT"
	Option		"DPMS"
	HorizSync	28-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Samsung 900IFT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
**	Option          "AIGLX" "true"**
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

[B]Section "Extensions"
	Option "Composite" "Enable"
EndSection[/B]
```

Don't just dump mine in - make the changes in a copy of your own.  I have some settings you DON'T want - like a 101 key keyboard!

What I do is have 2 files:
```

/etc/X11/xorg.conf.backup.fglrx
/etc/X11/xorg.conf.backup.ati
```

so I can copy either one in as needed...

Note especially that AIGLX should be turned back on, and Composite Enabled as well.

Hope one or the other works OK for you.  Also - here is the relevant setting file for XGL sessions (/usr/local/bin/startxgl.sh ) - in case you have some variant that is stopping you..

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

That's what I use when I decide to go with XGL...


Good Luck!

---

