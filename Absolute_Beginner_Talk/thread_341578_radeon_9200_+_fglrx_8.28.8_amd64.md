---
title: "radeon 9200 + fglrx 8.28.8_amd64"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-18
OK, so I'm trying my best here, but I need to help of you fine people once again. I say again, but I haven't even got my video running yet. SO, a recap:

I am running a Radeon 9200 on an AMD 64 bit system. I feel like I have tried every possible combination of video drivers and acclerators and open sources and etc. and my video will still not run. The only thing that works are the vesa drivers. I came to the conclusion that [this guide was seemingly the best "looking."]("http://www.ubuntuforums.org/showthread.php?t=204910") Mind you, i'm extremely new at this. But I feel like I finally understand basically what each of the important parts of getting this to run, ACTUALLY DO!

So with that in mind, here's my xorg.conf after following the guide (using the 8.28.8 drivers, which are the newest that still "support" my radeon.) ALSO in addition to the way this guide installs the three debs, I also tried using the GUI interface and to the same effect, I boot to the black screen before the login, and that is where I remain until I reboot.

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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
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
	Identifier   "Q95-2"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver      "vesa"
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
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200]"
	Monitor    "Q95-2"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


PLEASE DON'T MAKE ME WAIT UNTIL I HAVE ENOUGH $$ FOR A NEW CARD.

---

### Post by gralbe on 2007-01-18
Is 8.28.8 the latest version of fglrx?

If so, or it's in any way recent, well... ATI doesn't support their older chips any longer (under Linux or Windows). (Under Linux you get only a black screen)

I'm running a 9200 mobile in my laptop using the open source drivers. Why don't you want to use those? They work great!

---

### Post by je1117 on 2007-01-18
Well, I don't know what version of Ubuntu you're running, but the only success stories I read about open source drivers are when people are running Edgy. 

The only things that I have tried are an AIGLX installation and just changing the word vesa in my xorg to radeon. I have also changed the word ati to radeon, with the same results. Could you give me a little info on how you installed yours?

Thanks in advance.

---

### Post by gralbe on 2007-01-18
> **je1117 said:**
> Well, I don't know what version of Ubuntu you're running, but the only success stories I read about open source drivers are when people are running Edgy. 

Wow, really? Well, I've used Kubuntu for three releases now... I guess I would say that Edgy was the most straight forward but I don't recall it ever being a challenge (but I forget things and this really doesn't help you.)

> **je1117 said:**
> The only things that I have tried are an AIGLX installation and just changing the word vesa in my xorg to radeon. I have also changed the word ati to radeon, with the same results. Could you give me a little info on how you installed yours?

Thanks in advance.

My current install is of Edgy from CD. "It just worked." (tm)

I just reread your post... 8.28.8 is supposed to be the last supported. Then that means you need a modeline added, if I remember correctly. I'll have to do some googling because I just don't recall.

Could you post /var/log/Xorg.0.log for a failed run?

---

### Post by gralbe on 2007-01-18
Hey, try the advice given in this thread:

[http://www.ubuntuforums.org/showthread.php?t=151242](http://www.ubuntuforums.org/showthread.php?t=151242)

---

