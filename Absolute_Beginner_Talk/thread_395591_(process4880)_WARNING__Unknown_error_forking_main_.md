---
title: "** (process:4880): WARNING **: Unknown error forking main binary / abnormal early exi"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by farscape on 2007-03-28
Open office does not open. When I attempt to open it from the command line, I get this.
[B]** (process:4880): WARNING **: Unknown error forking main binary / abnormal early exit ...
[/B]
Yes I've searched it and it seems that "sudo dpkg-reconfigure xserver-xorg" might fix this problem but won't that trash my ATI driver install?

---

### Post by farscape on 2007-03-28
Open office doesnot like something in my xorg.conf file.
If I " **sudo dpkg-reconfigure -phigh xserver-xorg** " I get open office works but I lose my ATI driver. ALso, with the ATI driver I logon blindly. Blank screen when I hear the drums. I log in with username and password and the video comes back. My monitor complains of the frequency being out of range untill I log in.
This really sucks. I've been dealing with driver issues for at least a week now on both 6.06 and 6.10 ob 2 different machines. I thought edgy would be better. argh....

Well when I have another 24hrs off to install and trouble shoot the 8.35.5 Driver Manually, I'll do it. I've only tried the 8.28.8 driver.

---

### Post by igknighted on 2007-03-28
> **farscape said:**
> Open office doesnot like something in my xorg.conf file.
If I " **sudo dpkg-reconfigure -phigh xserver-xorg** " I get open office works but I lose my ATI driver. ALso, with the ATI driver I logon blindly. Blank screen when I hear the drums. I log in with username and password and the video comes back. My monitor complains of the frequency being out of range untill I log in.
This really sucks. I've been dealing with driver issues for at least a week now on both 6.06 and 6.10 ob 2 different machines. I thought edgy would be better. argh....

Well when I have another 24hrs off to install and trouble shoot the 8.35.5 Driver Manually, I'll do it. I've only tried the 8.28.8 driver.

Hmm, have you actually tried reconfiguring xorg.conf with that command?  There is no reason why it should stop fglrx from working.  Also, do you have the manual for your monitor?  Or can you look it up online?  When you get to the part with monitor setup, enter your vertical and horizontal sync values manually and that issue should be gone as well.

How did you install the fglrx drivers?  You know they are in the repo's, and that version was 8.34.4 last time I checked.  Fairly new.  I would try to install from there, has always worked well with no issues for me (except the time I installed them on Fesity... ATI didn't work with the 2.6.20 kernel then... but thats another story).

---

### Post by farscape on 2007-03-28
> **igknighted said:**
> Hmm, have you actually tried reconfiguring xorg.conf with that command?  There is no reason why it should stop fglrx from working.  Also, do you have the manual for your monitor?  Or can you look it up online?  When you get to the part with monitor setup, enter your vertical and horizontal sync values manually and that issue should be gone as well.

How did you install the fglrx drivers?  You know they are in the repo's, and that version was 8.34.4 last time I checked.  Fairly new.  I would try to install from there, has always worked well with no issues for me (except the time I installed them on Fesity... ATI didn't work with the 2.6.20 kernel then... but thats another story).

Sometime tomorrow I'll reconfigure with **"sudo dpkg-reconfigure -phigh xserver-xorg"** and I'll repost it. This is all new to me so I'm struggling. 

I installed the driver(fglrx) here: [Method 1: Install the 8.28.8 Driver the Ubuntu Way]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way")

I did it to the letter "Method 1: Install the 8.28.8 Driver the Ubuntu Way"

Are the drivers in the repos under ati drivers? Maybe I'll give that a shot.

I'm at work right now so it will have to wait till tomorrow.

Thanks for the reply.

---

### Post by farscape on 2007-03-29
This is my xorg.conf file after the ATI driver install on the wiki: 
I have to log in blindly and open office won't work. I'll run "sudo dpkg-reconfigure -phigh xserver-xorg" and post the results.


[B]
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"Vendorname" "ATI Proprietary Driver"
        Option          "ModelName" "Generic Autodetecting Monitor"
        Option          "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "ati"
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
	Device     "Generic Video Card"
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
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

[/B]

---

### Post by farscape on 2007-03-29
Now after "sudo dpkg-reconfigure -phigh xserver-xorg" everything seems fine. I can  see myself login and open office works. below is my new xorg.conf. But when I run
"glxinfo | grep rendering" I get a "NO"
before I ran "sudo dpkg-reconfigure -phigh xserver-xorg", I got a yes.
Can someone help me with this. I just want the best driver and settings for my video card. 
WHen I ran "sudo dpkg-reconfigure -phigh xserver-xorg", the only questions asked were which x server driver I was using. I chose ATI. And the video modes I was using. I chose 1024x768 and 800x600. That was it


[B]# If you have edited this file but would like it to be automatically updated
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
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
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
[/B]

---

### Post by farscape on 2007-03-29
Well I just installed the 8.35.5 Driver with instructions from the same wiki and theres no change. I have to log in blind and open office won't open. 
When I run **glxgears** and **fgl_glxgears**, they run very good.
And **glxinfo | grep rendering** gives me a **yes**.

Any suggestions?



[B]# If you have edited this file but would like it to be automatically updated
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "ati"
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
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600"
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
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
[/B]

---

### Post by farscape on 2007-03-29
Apparently open office wants a display size defined in the xorg.conf file.
Some folks on the net have added display sizes and it works. THis is what I added:

FROM THIS:
[B]Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection[/B]

TO THIS:
[B]Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
        *_DisplaySize 1024 768_*
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
        *_DisplaySize 1024 768_*
	Option	    "DPMS" "true"
EndSection[/B]

It works. open office opens and runs fine.
**glxgears** and **fgl_glxgears** runs fine

**glxinfo | grep rendering** returns a **yes**.

All is well except for the blind login this. I think that's an issue with my monitor though. If I can't figure that out, I'll start a different thread for that.

Thanks igknighted

---

### Post by pepa on 2007-04-01
I have the error when starting ooffice...

so far changing xorg.conf, as suggested in this thread does not fix it.

I'm running ubuntu on a thinkpad T60. When I set the DisplaySize to 1280 800 my login font becomes so smaller I can't even see it. I have to use Display 332 212, but neither change fixed the problem for open office. I still can't run ooffice :(

anyone have more suggestions?

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

