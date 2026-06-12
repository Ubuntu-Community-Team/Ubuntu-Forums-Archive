---
title: "problems installing Edgy (6.10) on NVidia 8800 GTS / Intel 64"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by mortuk on 2007-04-16
Hey all, total n00b here

Just trying to get Ubuntu Edgy (6.10) on my office machine. It has an NVIDIA 8800 GTS, Intel Duo Core 2 64 bit CPU, etc.

Basically I'm getting the X server crash error, I managed to get it installed alright, but now am having some really WIERD problems. When I try to log off, reboot, switch to another TTY, it will present me with a blank screen, and I cant get anything to come up without a reboot.

Also on that install when I tried to install the NVIDIA drivers it told me I needed to be on another run level. so I did 'telinit 3' and again was presented with the blank screen. Also if I try to install without changing run level it gives me the finger.

I have the Edgy 64 normal and alternate cd's, so was planning on starting again from scratch, but would be cool if someone could give me some really basic instructions to get it installed, fix the x server, and install the latest NVIDIA drivers for IA64 (latest drivers I can find on nvidia.com are from 2004, is this correct? If so maybe worth trying the i386 version?)

Have gone through various other threads but none seem to work for me, so thought I'd make my own. Dieing to get Beryl installed and have a play on my lovley dual 19" system @ work, pls help  	](*,) :D

---

### Post by overdrank on 2007-04-16
> **mortuk said:**
> Hey all, total n00b here

Just trying to get Ubuntu Edgy (6.10) on my office machine. It has an NVIDIA 8800 GTS, Intel Duo Core 2 64 bit CPU, etc.

Basically I'm getting the X server crash error, I managed to get it installed alright, but now am having some really WIERD problems. When I try to log off, reboot, switch to another TTY, it will present me with a blank screen, and I cant get anything to come up without a reboot.

Also on that install when I tried to install the NVIDIA drivers it told me I needed to be on another run level. so I did 'telinit 3' and again was presented with the blank screen. Also if I try to install without changing run level it gives me the finger.

I have the Edgy 64 normal and alternate cd's, so was planning on starting again from scratch, but would be cool if someone could give me some really basic instructions to get it installed, fix the x server, and install the latest NVIDIA drivers for IA64 (latest drivers I can find on nvidia.com are from 2004, is this correct? If so maybe worth trying the i386 version?)

Have gone through various other threads but none seem to work for me, so thought I'd make my own. Dieing to get Beryl installed and have a play on my lovley dual 19" system @ work, pls help  	](*,) :D

Hi this link should help you get your drivers installed
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Hope this helps with your video card and good luck and welcome!:popcorn:

---

### Post by mortuk on 2007-04-16
Hey

Firstly thanks for your help. I followed the above, ran envy, installed etc, and I still get the same thing, it can't start the X server

error is 
"Failed to load module "nvidia" (module does not exist, 0)"
and
"no screens found"

any ideas?

---

### Post by mortuk on 2007-04-16
I am currently in using the vesa drivers ok, and have downloaded envy and installed it

only thing is pressing Alt+Ctrl+F1 to kill X, seems to kill the OS completely, I get a blank screen and nothing on the busy light. So either it cant display that screen, or it just breaks ubuntu

getting rly desperate now, any ideas?

---

### Post by confused57 on 2007-04-16
> **mortuk said:**
> I am currently in using the vesa drivers ok, and have downloaded envy and installed it

only thing is pressing Alt+Ctrl+F1 to kill X, seems to kill the OS completely, I get a blank screen and nothing on the busy light. So either it cant display that screen, or it just breaks ubuntu

getting rly desperate now, any ideas?

This "might" help you to get to a console by pressing Crtl+alt+F1, boot your pc, highlight your Ubuntu entry in the grub boot menu, press "e", then take out the word splash in your kernel line, then press "b" to boot.  This change is temporary, but it'll tell you if it works or not.  It can be made permanent in your /boot/grub/menu.lst, if it works.

---

### Post by mortuk on 2007-04-16
The module_assistant package wasn't installed, so I downloaded and installed that manually

Tried an even later of envy with a GUI, it seemed to all work ok, then it rebooted and X server still crashed

Was thinking ubuntu was going to save me from the dreaded microsoft, but as I cant even get stupid gfx card drivers installed its just not doing it for me yet

dont know where to start, any ideas?

---

### Post by lamalex on 2007-04-16
try 7.04, it has easy graphics installation. It's official release is in 3 days but you can install it now if you want. [http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/) I've been testing it for months, it's very good. It will save you from that monster! If you need any help let us know!

---

### Post by mortuk on 2007-04-16
to be honest if I cant get edgy working becuase my graphics card is so new, I dont think I'm going to have much luck on an OS that is still technically in development.

could really do with an x server / nvidia drivers expert like tselliot taking a peek at this thread. its a real puzzler!!

---

### Post by lamalex on 2007-04-16
the 8800 is supported in the nvidia gfx driver so that shouldn't be a problem, and while feisty is still technically in development, it's pretty much frozen. could you post your xorg.conf file here. Also maybe try doing control + alt + backspace and then when you come back up from the boot take a look through the syslog (make note of the time when you hit control alt delete) and look for any bad module loads.

---

### Post by mortuk on 2007-04-16
when I restart x it just gives me a blank screen (as said above)

anyone else lend a hand, as I really wouldnt mind at least trying to get edgy to work

---

### Post by lamalex on 2007-04-16
yes it gives you a blank screen, i read that. but that doesn't mean it's not dumping things to syslog. Hit control alt bksp and then shut off and restart your pc. then look at the syslog. if you don't want my help ok. have fun figuring it out.

---

### Post by confused57 on 2007-04-16
See reply #46 in this thread, if you don't want to read the entire thread:
[http://ubuntuforums.org/showthread.php?t=403556](http://ubuntuforums.org/showthread.php?t=403556)

---

### Post by mortuk on 2007-04-16
sorry I thought u were just trying to pimp 7.04 taking this off topic

had to boot into ubuntu anyways as was in windows as cudnt do anything in an OS with no gfx drivers

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
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"NVIDIA GeForce 8800 GTS"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 8800 GTS"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

If I change 'vesa' to 'nv' or 'nvidia' it breaks and gives me an API mismatch

where do i find the syslog?

---

### Post by lamalex on 2007-04-16
/var/log/syslog

have you tried doing
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mortuk on 2007-04-16
cheers

yeah thats how I changed it back to vesa after nv and nvidia didnt work

syslog is too big to fit in a post :confused:

how about the xlog?

---

### Post by mortuk on 2007-04-16
> **confused57 said:**
> See reply #46 in this thread, if you don't want to read the entire thread:
[http://ubuntuforums.org/showthread.php?t=403556](http://ubuntuforums.org/showthread.php?t=403556)

wicked! this dragon dude seems to have the same problems that I am, but the only thing in that method 2 description, when it says to get a command line (CTRL+ALT+F1) it gives me a blank screen which I can only get out of by rebooting, which might disrupt the process

---

### Post by lamalex on 2007-04-16
you can go right to it if you boot into recovery mode. hit esc at grub stage 1.5, before the ubuntu splash.

---

### Post by mortuk on 2007-04-16
Following that method 2 exactly, and when I get to step 9, using nvidia-xconfig, it denies me with the following error

```
sudo: nvidia-xconfig: command not found
```

This is well annoying, as am following it word for word, plus have tried envy which is supposed 2 b foolproof lol

---

