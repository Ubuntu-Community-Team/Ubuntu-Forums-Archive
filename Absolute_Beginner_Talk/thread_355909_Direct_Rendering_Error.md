---
title: "Direct Rendering Error"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by nomiK on 2007-02-07
Hi,

I just started using ubuntu edgy and I am having problems getting 3D acceleration to work. I have been through several forum posts here and on other sites and have checked several wikis too but I couldn't solve my problem.

I have a ATI AIW Radeon 9800 Pro, I installed the drivers and followed instructions on this site to enable  direct rendering. 

Heres what I get when I do "glxinfo | grep direct":
> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


Here is my xorg.conf file:
> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
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
	Load  "i2c"
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

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI RADEON 9800 PRO"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON 9800 PRO"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


Thanks I am really looking forward to stop making my windows jag all the way and using xgl/beryl. Also to note, my graphics card is working, since I'm getting  the high resolutions and colours I had in windows. Please don't link to other forum posts because I have checked them all.

---

### Post by nomiK on 2007-02-07
bump?

---

### Post by Ziox on 2007-02-07
be patient, lots of people have this similar problem.  The ATI drivers seem to be rather non-functioning for many ATI cards. 
Something to help the troubleshooters is if you just make a short list of your hardware and software. Especially the version of Ubuntu and the hardware model.

In addition, could you create a link to the website you found the guide on?

---

### Post by nomiK on 2007-02-07
**Hardware:**
AMD Athlon 64 3400+
ATI AIW Radeon 9800 Pro
1 Gig Ram

**Software:**
Fresh Install of Ubuntu 6.10, Dual Booted with WinXP

**Links I used:**
3D Acceleration: [HTML]https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#video-acceleration-introduction[/HTML]
Driver Installation:
[HTML]http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide[/HTML]

I followed these guides and other troubleshooters i found on google, but nothing helped.

---

### Post by Ziox on 2007-02-07
Perhaps diable Composite...

in the last section of xorg.conf file, change "Enable" to "Disable"

and make sure that you restart X after saving the file. (either by logging off and hitting ctrl+alt+backspace OR by rebooting)

---

### Post by nomiK on 2007-02-07
I just tried that, nothing happened. Anyways, this is my 2nd day with ubuntu, been using red hat occasionally at uni...never had it on my computer though. I like it a lot, feel right at home.

---

### Post by Maestro23 on 2007-02-07
> **nomiK said:**
> I just tried that, nothing happened. Anyways, this is my 2nd day with ubuntu, been using red hat occasionally at uni...never had it on my computer though. I like it a lot, feel right at home.

I used that same guide myself to for my ATI X1600 and it worked like a charm. Used Method #1.  Which one did you use?  Check and make sure you didn't mix/match the instructions between both methods.

---

### Post by nomiK on 2007-02-07
Actually I used Method 2 because Method 1 refused to work for me. I did a lot of things that just sent me around in circles, in fact I screwed up at one point and was booted right into terminal, had to edit xorg.conf back before gnome would load.

---

### Post by nomiK on 2007-02-08
Now I dont know what I did, besides changing composite to disable but now the error is gone:
> Xlib: extension "XFree86-DRI" missing on display ":0.0".

But I still get this:
> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by nomiK on 2007-02-08
Now i'm back to the same error with composite disabled...

---

### Post by nomiK on 2007-02-09
Now my resolution is dead...someone please help :(

---

### Post by nomiK on 2007-02-10
ARGGHHH!!!

So, frustrating.

I messed up big time, GRUB stopped working so I did a fresh install of Edgy.

Now I am back to the same error.

Please help. 
p.s.  I learned how to create .tar backups now... :D

**Current State of the Union:**
> 
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


**fglrxinfo:**
> 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1


---

### Post by nomiK on 2007-02-10
This is the current state of xorf.conf:

> 
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
	Screen      0  "aticonfig-Screen[0]" 0 0
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
	Load  "i2c"
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

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VA712b"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "VA712b"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection



---

### Post by PPAAUULL on 2007-02-10
Ok are you sure that you have the correct Restricted moduals for your kernel installed? that is one of the problems that I encountered when I compiled my own kernel.

---

### Post by nomiK on 2007-02-10
how do i check that?

---

### Post by avalenti on 2007-02-10
I keep getting the same message too.  I think we just need to wait a week or so.  Theres been bugs with the new kernel upgrade.  The same error happened during the late betas of edgy.  It's something that just fixes itself and you can't really do anything about.

---

### Post by robcarr2 on 2007-02-14
I had the same problem of getting direct rendering to work

I used a program called Envy to do it

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I recommend it to anyone whos having this problem!

---

### Post by nomiK on 2007-02-14
I have tried that to, and am almost about to give up on ubuntu....its just too laggy to do anything with. And Fiesty Fawn wont come with drivers either now....

Only thing keeping me to linux is because im going to do a course in operating systems and programming, for which i need to be comfortable with linux.

---

### Post by sillymesilly on 2007-03-02
You do not need envy, all you need to do is to follow this instructions>

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

I was able to activate 3D acceleration on ATI Radeon 9800 PRO :)

---

