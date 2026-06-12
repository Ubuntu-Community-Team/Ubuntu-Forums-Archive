---
title: "NVidia driver installation problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Crisuntu on 2007-03-23
Well, the problem I have with the resolution seems to be very hard to solve. I need "1024x768", but I can't get past "800x600"
I have an NVidia Geforce2 mx 400. When I install the driver, with the X server completely stopped, this is what appears on the screen, after accepting the license agreement:

[B][I]"No precompiled Kernel interface was found to match your Kernel. Would you like the installer to attempt to download a kernel interface from the Internet?  [http://downloads.nvidia.com/"](http://downloads.nvidia.com/")
[/I][/B]

I press yes. Then this appears:

[B][I]
"No matching kernel interface was found. This means the installer will need to compile a kernel interface for your kernel."[/I][/B]

After accepting...

[B]*"You appear to be using a modular X.org release, but NVidia-installer was unable to determine the correct X library installation path and will install the NVidia x libraries to /usr/lib."*
[/B]
[B][I]
"NVidia was unable to determine the correct x module installation path and will install the NVidia x driver components to/usr/lib/xorg/modules. If X fails to find the NVidia X driver module, please correct any pkg-config problems warned about earlier and reinstall the driver"[/I]
[/B]


To give you an idea of how noob I am, I don't know what the Kernel is.
So, any suggestions as to what could be the problem are welcome. And if there's any other information that I could provide in order for you to better understand the problem just tell me, please.

Bye,

Cristian

---

### Post by doobit on 2007-03-23
> **Crisuntu said:**
> Well, the problem I have with the resolution seems to be very hard to solve. I need "1024x768", but I can't get past "800x600"
I have an NVidia Geforce2 mx 400. When I install the driver, with the X server completely stopped, this is what appears on the screen, after accepting the license agreement:

[B][I]"No precompiled Kernel interface was found to match your Kernel. Would you like the installer to attempt to download a kernel interface from the Internet?  [http://downloads.nvidia.com/"](http://downloads.nvidia.com/")
[/I][/B]

I press yes. Then this appears:

[B][I]
"No matching kernel interface was found. This means the installer will need to compile a kernel interface for your kernel."[/I][/B]

After accepting...

[B]*"You appear to be using a modular X.org release, but NVidia-installer was unable to determine the correct X library installation path and will install the NVidia x libraries to /usr/lib."*
[/B]
[B][I]
"NVidia was unable to determine the correct x module installation path and will install the NVidia x driver components to/usr/lib/xorg/modules. If X fails to find the NVidia X driver module, please correct any pkg-config problems warned about earlier and reinstall the driver"[/I]
[/B]


To give you an idea of how noob I am, I don't know what the Kernel is.
So, any suggestions as to what could be the problem are welcome. And if there's any other information that I could provide in order for you to better understand the problem just tell me, please.

Bye,

Cristian

That's the same card I have on my old Gateway. The proprietary Nvidia drivers don't support it, but the ones in the xserver support it very well. 

The kernel is the part of Linux where the basic drivers for your computer are. It connects the BIOS in your computer with the other software in the OS. One of those pieces of software in Ubuntu is called the X server. That is a collection of software that drives video cards, and input devices, among other things.

The standard X server will work very well with that card, but you may need to reconfigure it. I think you may need to uninstall those drivers you downloaded first, though, and I'm not sure I know how to explain how to do that.

Once you have done that though, you can open the terminal, and type ```
sudo dpkg-reconfigure xserver-xorg
``` to set up X for your monitor.

---

### Post by Crisuntu on 2007-03-23
Thanks you for your answer  Doobit.

First, if anybody is so kind to tell me how to uninstall this driver. I googled that, fruitlessly.
```
sudo dpkg-reconfigure xserver-xorg
```
Does the above code do the same this one does?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Because I have tried the latter. With this one, a screen appears allowing me to choose from a list of values, in which the only one I recognize is VGA. Then, once I have chosen a value it gives me a list containing different resolutions. If I choose "1024x768", when the computer restarts it either tells me, the X server is not well configured or in the login screen after entering my pass it loops and asks me again for the login and then for the pass again.

Something interesting is, that If I access from the live CD it sometimes run in "1024x768", though most of the time it runs in "800x600".

Bye

---

### Post by saadakhtar on 2007-03-23
can u post ur xorg.conf
u can find that in
**/etc/X11/xorg.conf**

open terminal and type in
**sudo nano /etc/X11/xorg.conf**

copy everything in there and post it.
i have a ***script that can automatically take care of your drivers*** if u need i can post that too.

---

### Post by Crisuntu on 2007-03-23
Here's my xorg.conf file.
For your information I have tried to change the resolution in the part "Section "Screen". Then, I had to access it from the live CD to restore it because it didn't work.
Also, after installing the NVidia driver, I did not see any changes to this file.
And of course, I'll appreciate if you give me that script (I'll appreciate it even more if give a brief explanation on how to use it)
Thanks for your interest.
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
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
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

### Post by Crisuntu on 2007-03-26
Well, maybe this graphics card will never work on Linux. Anyway, i post this to see if anyone know something.

---

### Post by bazcor on 2007-03-26
I have no real idea if this will help sort out your driver problems, but I have had good results using the Envy script.. 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

good luck..

---

