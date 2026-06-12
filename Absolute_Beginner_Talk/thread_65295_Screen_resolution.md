---
title: "Screen resolution"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by mikkeX on 2005-09-13
Like many beginners I have problem with screen resolution,
I can not get anything else than 640x480 with 16 och 32 color depth - but with 8 color depth I could have bigger resolution.

Here is my conf-file:



Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	8000	
EndSection


Section "Monitor"
        Identifier   "Eizo Monitor"
        VendorName   "Eizo"
        ModelName    "Eizo T67"
        HorizSync 30.0-95.0
        VertRefresh 50.0-160.0
        Option      "CrtScreen"
	Option      "DPMS"
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Eizo Monitor"
	DefaultDepth	16

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" 
	
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"

	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"

	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
                Modes      "1600x1200" "1600x1024" "1600x1000" "1400x1050" "1440x900" "1280x1024"

	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"



	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by aysiu on 2005-09-13
```
 HorizSync 30.0-95.0
VertRefresh 50.0-160.0
```

Find out what these are supposed to be for your monitor; then, adjust appropriately. You can usually find the specs at the manufacturer's website.

---

### Post by mikkeX on 2005-09-13
[QUOTE=aysiu]```
 HorizSync 30.0-95.0
VertRefresh 50.0-160.0
```

Find out what these are supposed to be for your monitor; then, adjust appropriately. You can usually find the specs at the manufacturer's website.[/QUOTE]

According to my manufacture, that are the values I should use.
[http://www.eizo.com/support/discontinued/crt/t67.asp](http://www.eizo.com/support/discontinued/crt/t67.asp)

---

### Post by aysiu on 2005-09-13
[QUOTE=mikkeX]According to my manufacture, that are the values I should use.
[http://www.eizo.com/support/discontinued/crt/t67.asp](http://www.eizo.com/support/discontinued/crt/t67.asp)[/QUOTE] That's odd. Have you tried rebooting?

---

### Post by Juergen on 2005-09-13
Open a xterm or change to a console and do
```
less /var/log/Xorg.0.log
```
Look for lines starting with '(EE)' or '(WW)' or containing 'Not using default mode' 
Maybe they give some usable info.

---

### Post by mikkeX on 2005-09-13
I have rebooted and do not get any useful information from the log, but maybee this means something:

(II) I810(0): Eizo Monitor: Using hsync range of 30.00-95.00 kHz
(II) I810(0): Eizo Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1600x1200" (no mode of this name)
(II) I810(0): Not using mode "1600x1024" (no mode of this name)
(II) I810(0): Not using mode "1600x1000" (no mode of this name)
(II) I810(0): Not using mode "1400x1050" (no mode of this name)
(II) I810(0): Not using mode "1440x900" (no mode of this name)
(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (640 -> 1024).
(--) I810(0): Virtual size is 640x480 (pitch 1024)
(**) I810(0):  Built-in mode "640x480"

---

### Post by Juergen on 2005-09-13
Hm, not too helpful, but I googled a bit and found 2 possible reasons:

1) a buggy BIOS that limits video-RAM to ~800kB
Look for lines that say something about memory in your Xorg.0.log

2) This thread: [http://lists.ubuntulinux.org/archives/ubuntu-users/2005-May/035831.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-May/035831.html)
You can look up the bug at [https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com)
But here it seems you should be able to change resolutions - can you change something with <ctrl>+<alt>+<numpad+> (or numpad-)?

Oh, and someone suggested to remove the 'load dri' line, maybe you could try that.

More info about your system and mainboard might help someone, but I think I'm out here :-(

---

### Post by mikkeX on 2005-09-13
Thanks for trying - but no luck here.
I attached the entire log.
My computer is this one:
[http://ips.insight.com/site/product/detail/index.cfm?item_number=819893U&NugsTracking=Results_ppp](http://ips.insight.com/site/product/detail/index.cfm?item_number=819893U&NugsTracking=Results_ppp)

---

### Post by Juergen on 2005-09-13
> (--) I810(0): Maximum space available for video modes: 832 kByteThis is a bit low...
Google for this line, there are several people with this problem, but I don't see any solutions :-(

No way to get an 'el cheapo' graphics card?

---

### Post by mikkeX on 2005-09-14
Had no problem with the resolution in Windows, but could it be that it does not have enogh memory on the card?

---

### Post by Muhammad on 2005-09-14
Did tou try this yet?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mikkeX on 2005-09-14
Yeah, tried to reconfigure - but no luck.

---

### Post by heimo on 2005-09-14
Check for video bios / bios updates from Intel.

You've probably already seen these?
[http://ubuntuforums.org/showthread.php?t=27029]("http://ubuntuforums.org/showthread.php?t=27029")
 [http://ubuntuforums.org/showthread.php?t=24923]("http://ubuntuforums.org/showthread.php?t=24923")

---

### Post by mikkeX on 2005-09-14
Hmmm...
When i tried the tip on 
[http://www.mail-archive.com/devel@xfree86.org/msg06190.html](http://www.mail-archive.com/devel@xfree86.org/msg06190.html)
and run  855resolution -l I just get:

Chipset: 845G (id=0x25608086)
Unknow VBIOS structure

Why could that be?

---

