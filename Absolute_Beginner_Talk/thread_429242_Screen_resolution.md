---
title: "Screen resolution??"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-05-01
I  have an old Toshiba laptop running Windows XP professional. I recently formatted the hard drive and installed Feisty. The desktop size has shrunk on the monitor screen. The window which filled the screen, when XP was running,  is now occupying just about 2/3rds. The screen resolution options are only 800x600 and 600x400 with Feisty.
I am sure many out here wouls be able to help resolve this issue.
Thanks in advance

Jagannath

---

### Post by alienexplorers on 2007-05-01
Try running:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by bigken on 2007-05-01
yep alienexplorers is right 

use the space bar to select you desired resolution good luck :)

---

### Post by jagannath on 2007-05-01
> **alienexplorers said:**
> Try running:

Thanks guys,

I ran the command as suggested and I get the warning as below:

     xserver- xorg postinst warning: overwriting possibly- customized configuration file; backup in / etc/x11/xorg.conf.20070501185827   

Now what do I do??

---

### Post by akudewan on 2007-05-01
I think that warning is safe to ignore. It just made a backup of the xorg.conf file

---

### Post by TURNER on 2007-05-01
```
xserver- xorg postinst warning: overwriting possibly- customized configuration file; backup in / etc/x11/xorg.conf.20070501185827
```

is basically informing you that a backup of your xorg has been made, the file name is "/etc/x11/xorg.conf.20070501185827"

You could try amending your xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

If you scroll to the bottom of the gedit file you should see "monitor", and a list of depths, and related screen resolutions, at the top of this list is the default "depth" you are using, usually 24 I believe, enter your desired resolution under the 24 depth (as the other resolutions are entered) and save the file.

CTL+ALT+Backspace to restart X, and check under your screen resolutions in order to amend the resolution.

IMPORTANT.

If your Pc does not like the xorg.conf setings X may refuse to start.

If this is the case you will be presented with a blue (kinda bios looking) screen indicating an error, click ok and you should see a blank screen, press ctrl-alt-F1 to open up a terminal, and enter your user and password.

now run the command ```
sudo cp /etc/x11/xorg.conf.20070501185827 /etc/X11/xorg.conf
```

This should revert your xorg.conf to the last known good settings.

If you have any more issues, post them here so we can all take a look

---

### Post by jagannath on 2007-05-01
Ok  Turner. Will try the gedit of the xorg.conf file and get back.
Thanks,

---

### Post by freebird54 on 2007-05-01
Doing the dpkg-reconfigure thing is the easier alternative for most people at first, especially with a guide like this:  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

It never hurts to know what's happening :)

The direct edit is in case you didn't get what you wanted from the dpkg-reconfigure  program...

---

### Post by jagannath on 2007-05-01
You guys are not gong to believe this!

I'm looking for the " key on my keyboard:-k 

Will get back after I try out the suggestions.

Thanks to all,

---

### Post by jagannath on 2007-05-01
Here's how the relevant part of my xorg.conf file looks like:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

The problem is the drop down menu for screen resolution gives me 800x600 and 600x400 only.

Any suggestions? 

Thanks,

---

### Post by TURNER on 2007-05-01
Hi, 

Try [this]("http://linux-on-laptops.com/forum/archive/index.php/t-135.html") page, seems a few other people have experienced issues whilst using a Toshiba laptop with Trident Microsystems Cyber 9525

You're xorg.conf is already backed up so we don't need to go there

start with 
```

$ sudo gedit /etc/X11/xorg.conf
```

and enter the following under the monitor section:

Section "Monitor"
Identifier "Generic Monitor"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 31.5-90.0
VertRefresh 59.0-85.0
# 1024x768 @ 60 Hz, 48.4 kHz hsync
Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync
EndSection

save, CTL+ALT+BACKSPACE reboot X and "hopefully" enjoy.....

remember the info above ref reverting your xorg.conf file should X refuse to restart!!

---

### Post by jagannath on 2007-05-02
Thanks Turner. 

Tried that but no luck!!

I put the suggested code in the xorg.conf file. But had to go back to my back up file as X refused to start. 
I'm back to square one.
I'm probably making a mistake somewhere. I'll try again a couple of times before screaming for more help !!

Thanks again.

---

### Post by freebird54 on 2007-05-02
YOu might try to post the entire xorg.conf file, and someone might well spot something that is holding you back.  Once you have it pasted in, highlight it and click on the # in the editing button bar...

When you ran the

```
sudo dpkg-reconfigure xerserver-xorg
```

which method of monitor selection did you use?  I suggest you use either the medium (and be sure to enter the 'best' mode) or the advanced (and put in the correct number for HorizSync and VertRefresh).

The fix is out there!

---

### Post by akudewan on 2007-05-02
Didn't the dpkg-reconfigure method work? Its a lot easier to work with.

Otherwise try following this guide: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by bigken on 2007-05-02
ok try this 

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa as your driver and your desired screen resolutions 

if this works then your can run the command again to select your driver

---

### Post by jagannath on 2007-05-02
The only change is that now the drop down menu shows one more option 832x624 besides the 800x600 and the 640x480.

The xorg.conf file pasted at [http://linux-on-laptops.com/forum/archive/index.php/t-135.html](http://linux-on-laptops.com/forum/archive/index.php/t-135.html) by jokre is as below:

Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:0:4:0"
EndSection

The same section as on my xorg.conf is this:

Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

The BusID is different.

Is this probably why this solution doesn't work for me??

---

### Post by jagannath on 2007-05-02
> **bigken said:**
> ok try this 

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa as your driver and your desired screen resolutions 

if this works then your can run the command again to select your driver

Should I run this code after modifying the xorg.conf file as suggested by Turner or with original xorg,conf file?
:confused:

---

### Post by bigken on 2007-05-02
just run it what you got to loose

---

### Post by jagannath on 2007-05-02
> **bigken said:**
> ok try this 

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa as your driver and your desired screen resolutions 

if this works then your can run the command again to select your driver

Ok. I tried this. A backup was created.
Now how do I select vesa as my driver and the desired screen resolutions. please??](*,)

---

### Post by akudewan on 2007-05-02
Don't you get a nice screen that lets you select things ?

---

### Post by jagannath on 2007-05-02
> **akudewan said:**
> Don't you get a nice screen that lets you select things ?

No!:confused:

---

### Post by jagannath on 2007-05-02
I am getting only 3 options in the drop down menu: 832x624, 800x600, 640x480
I am posting the entire xorg.conf file as it is now.

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
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
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31.5-90.0
	VertRefresh     59.0-85.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by bigken on 2007-05-02
copy and paste this into a terminal 

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by jagannath on 2007-05-02
> **bigken said:**
> copy and paste this into a terminal 

sudo dpkg-reconfigure -phigh xserver-xorg

I'm back where I started. I am now with just the two options, 800x600 and 640x480 in the drop down menu for screen resolution.](*,)

---

### Post by bigken on 2007-05-02
ok run the command again and use the arrow keys to navigate to  your desired screen sizes then press the space bar to select them

---

### Post by jagannath on 2007-05-03
Hi bigken. 

Thng is when I run the command only a backup of the xorg.conf file is created. I don't get any screen or any such thing to navigate through and select !!?

---

### Post by alienexplorers on 2007-05-03
Try modifying the monitor section of your xorg.conf as shown below:

> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31.5-90.0
VertRefresh 59.0-85.0
Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
Modeline "1280x960_60.00"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync
EndSection

The modeline lines added to the monitor section were generated using the gtf program located at:  

> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by jagannath on 2007-05-03
Thanks alienexplorer.
But nothing seems to help. The choices I have are still only 800x600 and 640x480.

Looks like I too have to start enjoying insanity!!:???:

---

### Post by freebird54 on 2007-05-03
Are you cut and pasting these entries into the file?  They should, at a minimum, be makeing a difference - whether or not in the right direction!

Are those number for the Sync and Refresh rates actually correct for your monitor?  This is very strange.....

---

### Post by jagannath on 2007-05-03
Thanks a lot folks. Well ! Just can't figure out what wrong where. being a newbie to boot doesn't make things any better.
I have got to catch my boat now. Will be away at sea for the next five months or thereabouts.
Hope to pick up this thread all over again after I get back and find a solution, with the help of you guys out there for sure.
Thanks again,

Bye for now.

---

### Post by alienexplorers on 2007-05-03
What exactly are the horiz & vert rates.  What model Toshiba Laptop are you using?  The only thing I can think of is that the rates are wrong or the screen can not accept resolutions higher than what you are getting.    On the 800x600 have you tried to stretch the display so it fills the entire screen.  You could also change the default color depth to a lower default.  Now you are using 24, try 16 or 8.

---

### Post by Bogdon6 on 2007-05-07
I have been having the same problems as jagannath, but with an old desktop.  I have an nvidia Riva TNT2 graphics card and a Viewsonic A95f.  Obviously this isn't new hardware, but I should get screen resolution higher than 800x600 and 640x480.  My xorg.conf file lists settings up to the monitor's maximum resolution (1600x1200), but the Screen Resolution window only allows me to choose 800X600 and 640X480.  

As I understand your advice, I will first run  sudo dpkg-reconfigure -phigh xserver-xorg  

If that doesn't help, I will try entering the modeline information (below).  Should I change the horizsync and vertfrefresh for my monitor?  If so, what should I change it to?    

> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31.5-90.0
VertRefresh 59.0-85.0
Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
Modeline "1280x960_60.00" 102.10 1280 1360 1496 1712 960 961 964 994 -HSync +Vsync
EndSection

Thanks for your help.

---

