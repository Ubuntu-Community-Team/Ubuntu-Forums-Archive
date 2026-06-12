---
title: "Can start X11 - font problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mielie007 on 2007-10-06
Hi

I have been running Ubuntu 6.10 Server on my home machine for more then 6 months and i have decided that i want to put a desktop manager on it. 

So i picked one and tried to install X11.

I tried to configure X using 

[HTML]dpkg-reconfigure xserver-xorg[/HTML]


It was complaining about the sceen, i figured out the i need to use i830 in the setup since the on board screen card is a intel GMA 950.

Now it's giving me the error that it can't find the font files at it's looking for. I have just about had it with X.

here is a copy of the error print out.

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Dapper-Drakie 2.6.20-16-server #2 SMP Sun Sep 23 19:57:25 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  7 00:56:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) AIGLX error: dlopen of /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/share/fonts/X11/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

Fatal server error:
could not open default font 'fixed'
```

Please somebody help

---

### Post by metalpancake on 2007-10-06
which driver have you installed?
I tried the intel  915 drivers? they worked well for me.:)

---

### Post by mielie007 on 2007-10-07
I installed xf86 video intel drivers.

I thought that this would solve the problem. 

It's funny that when I change the video card to something other then intel in the reconfigure, the only error I get is "no screen failure".

X then doesn't complain about the fonts being missing.

I understand from doing research on other sites that there aren't any fonts kept in the folders listed in the  error and that it only points X to where the fonts can be found.

Any suggestions? :confused:

Please tell me where I can download the drivers you mentioned. I'll try any thing at this point.

---

### Post by mielie007 on 2007-10-26
This is a bit of a chronological account of what i have done since last post to get to where I am now with installing a GUI on my Ubuntu server addition

I have since that last post upgraded to Gutsy. I thought that would solve the problem...no.

I found the 915 driver, after much googling and downloaded a tar file and tried to run the shell script from the tar file. no luck

After trolling the net for a while, I found that I could install the driver by enabling the *univers* in my sources.list file and typing.

[HTML]apt-get install 915resolution[/HTML]

typed in
 [HTML]915resolution -l[/HTML]
to determine what mode my monitor uses and set the monitor to that mode - mine is 34

Xserver continued to complain about its font folders that were empty. i checked to see if the folders existed and if they were empty. All the folders were there, but were empty.

Found a page at [www.x.org](www.x.org) that provided some guidence as to what to do about the fonts. 

all I had to do was run 

[HTML]mkfontdir /usr/share/fonts/X11/cyrillic
mkfontdir /usr/share/fonts/X11/100dpi
mkfontdir /usr/share/fonts/X11/75dpi
mkfontdir /usr/share/fonts/X11/Type1
mkfontdir /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType [/HTML]

to make a font.dir file in each of the font folders.

so after al of that, i rebooted my machine
it gets to the point where it wants to start X and al that happens is that the monitor changes to black as if to start GUI display and then goes back to command line.

after loging in and starting X again, it gives me some other error

my xorg.conf file is given below and Xorg.0.log is attached. I have found no errors in the log file, just some warnings.

xorg.conf
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
	Identifier	"gma950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"gma950"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection


```

i cant figure out what is wrong with X now and what to do to solve the problem. Please somebody help!!!! ](*,)

---

### Post by kerry_s on 2007-10-26
x has to be installed before the WM or at the same time.
i think in 6.10 it was->

sudo apt-get install x-window-system-core (your WM)

that will pull in all you need.

---

### Post by mielie007 on 2007-10-28
Thanks it's working now.

it brings up the gnome login screen.

the new problem is that it doesn't let the root login and if i login as another user it goes past the login screen and just sits there. 

what do i do now? can log in to the failsafe gnome, because the same thing happens.

---

### Post by mielie007 on 2007-10-30
it works

i removed the gnome that i installed be for 

```
apt-get remove gdm
```

and then installed ubuntu desktop

```
apt-get install ubuntu-desktop
```

and now it works. :guitar:

---

