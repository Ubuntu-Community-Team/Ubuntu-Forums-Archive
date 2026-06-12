---
title: "(EE) fglrx(0): [agp] unable to acquire AGP, error -1023"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-11
is there a fix for that problem and these
(> EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 


---

### Post by spiderbatdad on 2008-02-11
maybe a clue here if fglrxinfo gives you : ```
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or use the supplied driver.

---

### Post by Rocket2DMn on 2008-02-11
What model of ATI card are you using?  Did this happen when you setup fglrx or did it work before and suddenly stop?

---

### Post by Shadowmeph on 2008-02-11
> **Rocket2DMn said:**
> What model of ATI card are you using?  Did this happen when you setup fglrx or did it work before and suddenly stop?
Radeon X800 agp I just reinstalled Gutsy and the driver

---

### Post by Rocket2DMn on 2008-02-11
Why don't you try to reconfigure X, if that fails to fix the problem, you may need to reinstall the fglrx drivers.
HowTo reconfigure X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

To reinstall fglrx
HowTo remove fglrx: [https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)
HowTo re-enable fglrx: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Shadowmeph on 2008-02-11
> **Rocket2DMn said:**
> Why don't you try to reconfigure X, if that fails to fix the problem, you may need to reinstall the fglrx drivers.
HowTo reconfigure X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

To reinstall fglrx
HowTo remove fglrx: [https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)
HowTo re-enable fglrx: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

ok I tried everything in there also totally uninstalled the driver and then followed this guild [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")to reinstall but after doing this command>  less /var/log/Xorg.0.log |grep EE
 I still get this >  (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 

also >  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
 which is a hair puller lol

---

### Post by Rocket2DMn on 2008-02-11
So what is actually wrong other than these errors?  Is your resolution correct?  Does 3d acceleration work?
Can you please post your xorg.conf file
```
cat /etc/X11/xorg.conf
```

---

### Post by spiderbatdad on 2008-02-11
If fglrxinfo gives you the following, your installation is not completed correctly:

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

These two commands might fix your installation, try this, reboot, and run fglrxinfo again:

sudo mkdir -p /usr/X11R6/lib/modules/dri  
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 

Not to totally butt in, but I think I would:```
sudo dpkg-reconfigure -phigh xsever-xorg
```
and look for another ati driver in synaptic in the xserver section.

---

### Post by Shadowmeph on 2008-02-11
> **Rocket2DMn said:**
> So what is actually wrong other than these errors?  Is your resolution correct?  Does 3d acceleration work?
Can you please post your xorg.conf file
```
cat /etc/X11/xorg.conf
```

I have no 3d acceleration 

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons'		"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
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
	Identifier	"ATI Technologies Inc R420 JK [Radeon X800]"
#	Driver		"vesa"
	Driver		"fglrx"
	Option		"UseInternalAGPGART"	"no"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L1752T"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JK [Radeon X800]"
	Monitor		"L1752T"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Disable"
EndSection
Section "ServerFlags"
Option "AIGLX" "off"
EndSection
```

---

### Post by spiderbatdad on 2008-02-11
```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
``` should correct xorg.conf

---

### Post by Shadowmeph on 2008-02-11
> **spiderbatdad said:**
> ```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
``` should correct xorg.conf
I tryed this but it seems all the same and the this is still the same
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

also still getting this
 less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.

---

