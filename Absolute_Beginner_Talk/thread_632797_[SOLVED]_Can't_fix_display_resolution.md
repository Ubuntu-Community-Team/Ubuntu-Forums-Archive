---
title: "[SOLVED] Can't fix display resolution"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by gshockxc on 2007-12-05
I'm using Xubuntu 7.04 and I can't figure out how to get better than 800x600 display resolution.  I have about an inch of black space around the edge of the monitor.  I installed a bunch of other display resolutions that worked with Windows, but once X is installed I only have two options.  I forget the other, but 800x600 is the largest.  Any suggestions?

Also, I've been editing a text file in Abi Word, and if I change the line spacing to double-spaced and save, when I reopen the file, it reverts back to single-spaced.  

Thanks in advance for the help.

---

### Post by GSF1200S on 2007-12-05
> **gshockxc said:**
> I'm using Xubuntu 7.04 and I can't figure out how to get better than 800x600 display resolution.  I have about an inch of black space around the edge of the monitor.  I installed a bunch of other display resolutions that worked with Windows, but once X is installed I only have two options.  I forget the other, but 800x600 is the largest.  Any suggestions?

Also, I've been editing a text file in Abi Word, and if I change the line spacing to double-spaced and save, when I reopen the file, it reverts back to single-spaced.  

Thanks in advance for the help.

What video card do you have? Post the results of:

```
lspci
```

If you run Nvidia, post the contents of:

```
glxinfo
```

Do you know what drivers you are using? Have you physically installed drivers or are you using the ones that came preinstalled with Ubuntu? Post back and ill try to get you straight ;)

**EDIT** Also, post the contents of the xorg.conf

sudo gedit /etc/X11/xorg.conf

---

### Post by gshockxc on 2007-12-05
Do I need to run each of those commands in the terminal window?  Do I just type what you listed, or is there something I need to add before the command ```
lspci
``` and ```
glxinfo
``` 

I just used whatever drivers came with Xubuntu.

Thanks for the help.

---

### Post by GSF1200S on 2007-12-05
> **gshockxc said:**
> Do I need to run each of those commands in the terminal window?  Do I just type what you listed, or is there something I need to add before the command ```
lspci
``` and ```
glxinfo
``` 

I just used whatever drivers came with Xubuntu.

Thanks for the help.

Yes, im sorry.. run those commands in a terminal and post the results..

Yeah, youre using the opensource drivers, which may not correctly setup the resolution. You can try and reconfigure x to include those resolutions, but if we can get 3d graphics going, were killing 2 birds with one stone. What video card do you have by the way?

---

### Post by gshockxc on 2007-12-07
I tried to run those commands in the terminal window, but when I run the terminal window it logs me out of Xubuntu and takes me back to the log-in screen.  Weird.  I can't find the product info for my laptop, and I don't yet know how to find the equivalent of the "Device Manager" so I don't know what video card I have.  I never thought to look before installing X.  Any suggestions?

---

### Post by GSF1200S on 2007-12-07
> **gshockxc said:**
> I tried to run those commands in the terminal window, but when I run the terminal window it logs me out of Xubuntu and takes me back to the log-in screen.  Weird.  I can't find the product info for my laptop, and I don't yet know how to find the equivalent of the "Device Manager" so I don't know what video card I have.  I never thought to look before installing X.  Any suggestions?

Wait a minute.. when you open the terminal, it restarts X?!? Thats fing weird.

Well, I would think that should be your first priority to fix. Post a thread on this so someone can help you...

If you want to run these commands from the command line, try killing X and logging in before you type those commands.. Try when you start the computer to select "Recovery mode" which will only boot the kernel. Log in, and then try those commands. Once you get them and write them down, start x from the command line using:

```
sudo /etc/init.d/gdm restart
``` 

You may get a "Failure initializing HAL" at which point your wireless may not work. Restart the computer, and then post the results of those commands.

But seriously, try to fix the terminal problem if you can- thats the weirdest thing Ive ever heard of..

---

### Post by Flying caveman on 2007-12-08
How are you opening the terminal? Applications-Accessories-Terminal  not Ctrl-Alt-F2 right ??

---

### Post by philetus on 2007-12-08
I could use a little help too.

EVGA FX5500

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Section "Files"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Envision EFT"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Envision EFT"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by Flying caveman on 2007-12-08
This may come in handy. [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

I, like most people, probably don't do it the proper way.  I just edit my /etc/X11/xorg.conf

or sudo dpkg-reconfigure xserver-xorg

or sudo dkpg-reconfigure -phigh xserver-xorg

another link that might be worth reading [http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

---

### Post by gshockxc on 2007-12-08
> **Flying caveman said:**
> How are you opening the terminal? Applications-Accessories-Terminal  not Ctrl-Alt-F2 right ??

Yes, that's how I'm opening it.  It loads for an instant, and you can see the terminal window on the desktop for a brief second ... literally, and then it goes black.  Then the log in screen comes up.  I log back in, and my calendar is open on all 4 desktop environments.  So I try and try again, same result every time.

---

### Post by gshockxc on 2007-12-08
> **GSF1200S said:**
> 
If you want to run these commands from the command line, try killing X and logging in before you type those commands.. Try when you start the computer to select "Recovery mode" which will only boot the kernel. Log in, and then try those commands. Once you get them and write them down, start x from the command line using:

```
sudo /etc/init.d/gdm restart
``` 

You may get a "Failure initializing HAL" at which point your wireless may not work. Restart the computer, and then post the results of those commands.

But seriously, try to fix the terminal problem if you can- thats the weirdest thing Ive ever heard of..

I'm a noob, and it seemed pretty weird to me as well.  So my first question to you is going to be, "How do I kill "X?"  At the login screen, I don't see any options to run X without the GUI.  I'm assuming that's what you mean by "killing 'X'."  When I reboot the computer, I never see an option for Recovery Mode.

Take this with a grain of salt... this is an "OLD" Hitachi VisionBook Pro 7590.  It was old when I got it and that was at least 6 years ago.  I installed X so I could play with it and get familiar with Ubuntu before I installed it on my bigger machine.

---

### Post by Flying caveman on 2007-12-08
```
sudo /etc/init.d/gdm stop
```  stops* g*nome* d*isplay* m*anager

Actually, I'm not sure if that's exactly the same as X because in my experience playing around with different computers, I can get into the graphical desktop by "startx" or "gdm" maybe someone else can explain the difference, if any.  Sorry, if I'm confusing the issue; I'm still learning too.

When you restart your computer, you should see the grub boot menu on your screen. hit the "Esc" key before it starts to boot.  If you did a fresh install you'll probably only see 3 options, the default    kernel then the same kernal (recovery mode) and mem-test.  choose recovery mode and you'll end up at a command line. log-in  and you'll be able to enter commands.

---

### Post by gshockxc on 2007-12-09
> **Flying caveman said:**
> This may come in handy. [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

I, like most people, probably don't do it the proper way.  I just edit my /etc/X11/xorg.conf

or sudo dpkg-reconfigure xserver-xorg

or sudo dkpg-reconfigure -phigh xserver-xorg

another link that might be worth reading [http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

I tried the instructions listed in the link you gave, and it seemed to go well.  But when I got all done, I rebooted X and I lost the 800x640 resolution.  I only had the default resolution left.  So the screen is smaller than before.  So I'm kind of stuck.

---

### Post by gshockxc on 2007-12-09
> **GSF1200S said:**
> What video card do you have? Post the results of:

```
lspci
```

If you run Nvidia, post the contents of:

```
glxinfo
```

Do you know what drivers you are using? Have you physically installed drivers or are you using the ones that came preinstalled with Ubuntu? Post back and ill try to get you straight ;)

**EDIT** Also, post the contents of the xorg.conf

sudo gedit /etc/X11/xorg.conf

Results: 
LSPCI - VGA Compativle controller: Chips and Technologies F65555 HiQVPro (rev c6)

SUDO GEDIT /ETC/X11/XORG.CONF - gedit command not found.

I don't know if that helps.

---

### Post by Flying caveman on 2007-12-09
```
sudo gedit /etc/X11xorg.conf
```  is not the same as....

SUDO GEDIT /ETC/X11/XORG.CONF

Do you see the difference?

---

### Post by GSF1200S on 2007-12-10
> **Flying caveman said:**
> ```
sudo /etc/init.d/gdm stop
```  stops* g*nome* d*isplay* m*anager

Actually, I'm not sure if that's exactly the same as X because in my experience playing around with different computers, I can get into the graphical desktop by "startx" or "gdm" maybe someone else can explain the difference, if any.  Sorry, if I'm confusing the issue; I'm still learning too.

When you restart your computer, you should see the grub boot menu on your screen. hit the "Esc" key before it starts to boot.  If you did a fresh install you'll probably only see 3 options, the default    kernel then the same kernal (recovery mode) and mem-test.  choose recovery mode and you'll end up at a command line. log-in  and you'll be able to enter commands.

Yeah, well he said the terminal crashed his X session, so I figured Id have him boot the recovery mode and use that command to start the gui after he was done..

I must be missing something, because he said all seemed well in that guide, which is TERMINAL ENTRIES.. I guess he must have just done the recovery mode thing and rebooted versus trying to restart gdm..

What resolution is your monitor, and what resolution/drivers are set in your xorg.conf?

---

### Post by gshockxc on 2007-12-10
> **Flying caveman said:**
> ```
sudo gedit /etc/X11xorg.conf
```  is not the same as....

SUDO GEDIT /ETC/X11/XORG.CONF

Do you see the difference?

Yeah, sorry.  I just had a typo in my reply.  I made sure that I had the command correct when I was trying this.

---

### Post by gshockxc on 2007-12-10
> **GSF1200S said:**
> Yeah, well he said the terminal crashed his X session, so I figured Id have him boot the recovery mode and use that command to start the gui after he was done..

I must be missing something, because he said all seemed well in that guide, which is TERMINAL ENTRIES.. I guess he must have just done the recovery mode thing and rebooted versus trying to restart gdm..

What resolution is your monitor, and what resolution/drivers are set in your xorg.conf?

I tried to restart gdm, but when I typed the command, the screen just went blank and never came back.  So I shut down the power and started back up again.  That's when the screen got smaller, and I lost the 800x600 display resolution.

---

### Post by mali2297 on 2007-12-11
> **gshockxc said:**
> 
SUDO GEDIT /ETC/X11/XORG.CONF - gedit command not found.


Xubuntu has the editor Mousepad instead of Gedit, so type
```

gksudo mousepad /etc/X11/xorg.conf

```

As for using gksudo instead of sudo, see here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by gshockxc on 2007-12-11
[QUOTE=mali2297;3932229]Xubuntu has the editor Mousepad instead of Gedit, so type
```

gksudo mousepad /etc/X11/xorg.conf

```

Okay, well that worked well enough.  Thanks.  But I still don't know what to edit.  What am I supposed to do with the xorg.conf file once I get it open?

---

### Post by gshockxc on 2007-12-11
If anyone can help me, I would really appreciate it.  I'm desperate to have a larger screen.  Here are the contents of my xorg.conf file.  Please HELP!!!

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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Chips and Technologies F65555 HiQVPro"
	Driver		"chips"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-33
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Chips and Technologies F65555 HiQVPro"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
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

Section "Extensions"
	Option "Composite" "Disable"
EndSection


Thanks in advance.

---

### Post by Flying caveman on 2007-12-11
wow, you have a lot of resolutions listed there.  do you know what your native resolution is supposed to be?  I think X tries to use the highest resolution, Which may not be correct.   and maybe it defaults to a lower res???  

You could google to find what your resolution is supposed to be.  maybe you have a 1440X900????  

It might be a simple as adding that res to your xorg.conf   edit> and deleting higher resolutions

but you should be careful to set the synch and refresh rates properly and i'm not sure how to do that.  

to get the mode line for a resolution use gtf resolution refresh-rate
example 
```
gtf 1440 900 75
```
```
gtf 1280 1024 60
```

theres also xresprobe that you can install  but it didn't detect my resoltions properly

---

### Post by gshockxc on 2007-12-12
I didn't remember what my native resolution was on the laptop.  I tried to google it, but I can't find anything on the laptop because it's so old.  Hitachi doesn't even make it anymore.   So I just selected a bunch that I thought I might want to use.  I had an 800x600 on there, but it disappeared.  I was following some instructions to fix it, got to the configuration screen that's part of the installation, followed that through, selected all the same resolutions, but when I restarted "X" the 800x600 resolution didn't show up in the Display Preferences dialog box.  

You know how you can changed the appearance of your screen by adjusting the picture on your monitor, i.e. vertical, horizontal position, etc?  Well it looks like the vertical/horizontal settings have been changed so that the viewing area is shrunk.  There's about 2.5" of blank space around the outside of the screen.    But it's a laptop!  I don't have buttons to adjust the vertical/horizontal settings.  And that still doesn't explain why the resolutions don't show up in the display preferences window.  Do you think I should eliminate some of the higher resolutions and just try one at a time?  It's only a 13" monitor.

Thanks for the help.

---

### Post by gshockxc on 2007-12-12
> **Flying caveman said:**
> wow, you have a lot of resolutions listed there.  do you know what your native resolution is supposed to be?  

I found the proper resolution for my display.  What's the proper way to edit the xorg.conf file?  The resolution should be 1024x768.  Can I just go into the xorf.conf and delete the resolutions I don't need, and save?

Thanks.

---

### Post by gshockxc on 2007-12-12
In answer to your question, results of ```
lspci
```

00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:02.0 VGA compatible controller: Chips and Technologies F65555 HiQVPro (rev c6)
00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:0b.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)

And  ```
glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

---

### Post by Flying caveman on 2007-12-12
Thats what I would do, delete the higher resolutions that your monitor can't display.  

or run ```
sudo dpkg-reconfigure xserver-xorg
``` and make sure you de-select the resolutions higher than 1024x768  space bar selects/deselects 

then ctrl-alt-backspace to restart X

---

### Post by gshockxc on 2007-12-13
> **Flying caveman said:**
> Thats what I would do, delete the higher resolutions that your monitor can't display.  

or run ```
sudo dpkg-reconfigure xserver-xorg
``` and make sure you de-select the resolutions higher than 1024x768  space bar selects/deselects 

then ctrl-alt-backspace to restart X

I deleted all the resolutions in the xorg.conf file, but it didn't help.  When I restarted X, it was still the same.  I tried editing the display with vidtune, and it had no effect.  I modified xorg with "Modeline" and restarted X again.  Everything went haywire after that.  I got a jumbled mess on the display and couldn't get X to run.  So I'll do a fresh install tonight and see what happens.  How do you remember all of these commands?

---

### Post by mali2297 on 2007-12-13
> **gshockxc said:**
> How do you remember all of these commands?

You write them down on a piece of paper. :-)

I recommend that you run
```

sudo dpkg-reconfigure xserver-xorg

```
instead of manually editing xorg.conf (less risk of making mistakes).

---

