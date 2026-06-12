---
title: "Xorg on Powermac G4"
date: 2005-04-11
forum: Apple PPC Users
---

### Post by fire59 on 2005-04-11
I've just installed Hoary 5.04 on a powermac g4.  Does anyone have any experience with configuring xorg.conf for this system. Doing an lspci I get this:

```

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

```

So I went ahead and replace the Driver with "r128", didn't seem to improve.  Does any one have any suggestions for this or any tweak for the powermac g4.

---

### Post by DJ_Max on 2005-04-11
Post your
/etc/X11/xorg.conf

---

### Post by Len on 2005-04-11
EDIT: Ignore my post and let DJ Max help you. This stuff is certainly interesting but he probably knows more then I do (e.g. "Just add ... to your xorg line and things will fly" ;-) ), much better as building your own kernel without knowing it even makes a difference. /Edit

I've noticed that you can build in kernel support for the ATI Rage 128. 
According to the documentation it should give a speed boost in Xorg combined with 'AGP part' (or whatever it's called, can someone please jump in here?). Otherwise I have no idea how to improve performance on ATI cards. I've tried the 'ati' driver, 'radeon' driver and fglrx driver. The latter does support 3D on radeon cards but makes 2D even slower and the others didn't make much difference...

To build the kernel you'll need to get the sources. Synaptic is a great way to do that. I remember it was called something like linux source, not kernel source. Then, open a root terminal, type 
```

---optional--
./etc/init.d/gdm stop
<now login again>
--/optional--
/cd /usr/src
tar -xvjf <name of the kernel source archive>
ln -s <name of the kernel source directory> linux
cd linux
make menuconfig
```
From that point all is very straightforward. Read the forums for further details on how to make a yaboot menu option for the new kernel (in case things go wrong, you then still have the original one).

---

### Post by fire59 on 2005-04-12
I've gone through several kernel compilation on my IBM T41 and felt comfortable with it because i know the hardware spec(and the amount of resources out there).  I dont have a clue of powermac G4 hardware spec.

Here's my current xorg.conf 
```

 Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
 Identifier "Rage 128"
 Driver  "ati"
 BusID  "PCI:0:16:0"
 Option  "UseFBDev"  "true"
EndSection

Section "Monitor"
 Identifier "SDM-S93"
 Option  "DPMS"
 HorizSync 28-65
 VertRefresh 57-75
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Rage 128"
 Monitor  "SDM-S93"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1272x1017" "1024x768" "800x600" "760x608" "720x400" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection

```

here's my lscpi output:
```

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:0d.0 PCI bridge: Digital Equipment Corporation DECchip 21154 (rev 05)
0001:11:07.0 ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
0001:11:08.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:11:09.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:11:0a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
0002:21:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:21:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

```

---

### Post by fire59 on 2005-04-12
I'm also having problems with the sound.  Alsa looks like its installed but amarok doesn't seem to detect a sound system.  Although I can hear my systems sound, but when I play an mp3 or cd it just hiss.

---

