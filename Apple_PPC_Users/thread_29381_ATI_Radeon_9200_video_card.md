---
title: "ATI Radeon 9200 video card"
date: 2005-04-24
forum: Apple PPC Users
---

### Post by Hargo on 2005-04-24
Hi,

Is it possible to use Hoary on a Mac with an ATI Radeon 9200 video card?

After installation, display is unreadable. I tried the PC How-tos, but the fglrx packages seem not to be available.

There should be kind of a driver since I've use a Yellow Dog for several months. Should I stop looking for a solution or is there any hope?

---

### Post by callipeo on 2005-04-24
The card should work well. Can you describe the situation more accurately? On what mac have you installed? Did the installation finish without problems? Do you see (part of) the boot messages?

BTW, there are no fglrx packages for the PPC arch, you have to use the "ati" xorg driver; however, 3D acceleration is natively supported for the ATI Radeon <= 9200.

---

### Post by Hargo on 2005-04-24
Hi,

Installation was OK and Ubuntu does work on my Mac, now. However, after the boot (during which display is OK), this is all I can see after GDM is started:

[IMG]http://www.artisteek.com/ati-radeon.jpg[/IMG] 

By doing CTRL+ALT+F1, I can open a terminal session and try to install the necessary drivers with apt-get.

I will try the ati Xorg drivers. Do you know the exact names of the packages?

Here is my configuration (a G3 series with a G4 500 MHz processor replacing the original processor):

Computer model: Power Macintosh G3 Series
  Processor: PowerPC 60?  (11.4)
  Number of processors: 1
  Processor speed: 500 MHz
  Level 2 cache (per processor): 1 Mo
  Memory: 768 Mo
  Bus speed: 100 MHz
  Boot ROM version:	1.1.1f4

Video board (ATI Radeon 9200 Mac Edition, 128 MB DDR): 

ATY,RV280:

  Type:	display
  Bus:	PCI
  Emplacement:	J12
  VRAM (total):	128 MB
  Manufacturer: ATI (0x1002)
  Device ID: 0x5961
  Revision ID:	 0x0001
  Revision ROM: 113-A27502-120

Screen (Sony SDM-M51 flat screen):

  Type:	display
  Monitor type:	CRT
  VRAM (used):	128 MB
  Resolution:	1024 x 768 @ 60 Hz
  Depth: Colors 32 bits
  Main monitor: Yes
  Mirror: De-activated
  Connected: Yes


Thanks a lot!

---

### Post by Hargo on 2005-04-24
By the way, the Hoary Live CD display does work when I enter "live video=ofonly" at startup...

---

### Post by callipeo on 2005-04-24
Can you post your /etc/X11/xorg.conf file? BTW, I don't know if this would actually help, but you could add the "video=ofonly" parameter in /etc/yaboot.conf and check if it helps, given that it worked with the live cd.

---

### Post by Hargo on 2005-04-24
Here is my /etc/X11/xorg.conf file:

***************************************************

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Option		"DPMS"
	HorizSync	28-61
	VertRefresh	48-65
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"SDM-M51"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480" "640x400"
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

***************************************************

And here is the yaboot.conf file I've edited (doesn't work much, though...)

***************************************************
boot=/dev/hdc7
device=/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@0:
partition=10
root=/dev/hdc8
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hdc6
video=ofonly

image=/vmlinux
	label=Linux
	read-only
	initrd=/initrd.img
	append="quiet splash video=fonly"

image=/vmlinux.old
	label=old
	read-only
	initrd=/initrd.img.old
	append="quiet splash video=fonly"

***************************************************

---

### Post by callipeo on 2005-04-24
Looking at [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards), I found that for the RV280 chip the driver should be changed from "ati" to "radeon": could this be the cause of your problem? Try changing the "Driver" line in the device section of your xorg.conf from "ati" to "radeon" and restart gdm. If this doesn't work, please post your /var/log/Xorg.0.log file.

---

### Post by Hargo on 2005-04-24
It still does not work.

You will find the Xorg.0.log file attached.

Thanks for your great help!

---

### Post by heimo on 2005-04-24
I'd try something like this:

```

Section "Monitor"
  Identifier	"SDM-M51"
  Option	"DPMS"
  HorizSync	28-61
  VertRefresh   60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"SDM-M51"
	DefaultDepth	24
  SubSection "Display"
   		Depth		24
   		Modes		"1024x768"
  EndSubSection
EndSection

```

---

### Post by callipeo on 2005-04-24
I see three error here:
> (EE) RADEON(0): MergedFB does not work with Option UseFBDev, MergedFB mode is disabled.

This should not cause any problem (you can always try to disable UseFBDev if you need MergedFB).
> (EE) RADEON(0): FBIOPUT_VSCREENINFO: Invalid argument
(EE) RADEON(0): FBIOPUT_VSCREENINFO: Invalid argument
I do not really know what are these, but I think they are monitor-related; plus, I see a lot of "hsync out of range" and "vrefresh out of range". So my question is: where did your monitor settings come from? Have they been manually added by you? If so, maybe you could try to do "dpkg-reconfigure -plow xserver-xorg" and select "simple" (or "medium") in the monitof dialog, or change them manually to some more conservative vlues.

---

### Post by Hargo on 2005-04-24
And it just... WORKS! Right now, I'm using my brand new Hoary version!

Thank you both for your invaluable help.

Attached the my xorg.conf I edited as you instructed, I hope it may help others.

---

### Post by Hargo on 2005-04-25
The monitor settings were created automatically during install.

---

### Post by cobol on 2005-10-11
Hi! I have exactly the same problem with my ATI Radeon 9200 SE in a PC computer (so, it isn't just a Mac problem). How you did it? Can you explain it more detailed, step by step, please? (I'm a rookie in Linux). Do you know if the new Ubuntu release (5.10) solves automatically this problem?

Thanks a lot ;)

---

### Post by monway on 2005-10-12
[QUOTE=Hargo]Here is my /etc/X11/xorg.conf file:

***************************************************

...
boot=/dev/hdc7
device=/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@0:
partition=10
root=/dev/hdc8
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hdc6
video=ofonly

image=/vmlinux
	label=Linux
	read-only
	initrd=/initrd.img
	append="quiet splash [COLOR="Red"]video=fonly[/COLOR]"

image=/vmlinux.old
	label=old
	read-only
	initrd=/initrd.img.old
	append="quiet splash [COLOR="Red"]video=fonly[/COLOR]"

...[/QUOTE]


I've highlighted in the red the problematic error in the yaboot. If you wanted to use that video mode you'd just put in [COLOR="Green"]video=ofonly[/COLOR].

\\:D/ :KS

---

### Post by Hargo on 2005-10-12
Hi Cobol:

Here is what I did to launch Ubuntu with the edited xorg.conf file:

1. Copied the edited xorg.conf on my USB key.
2. Connected my USB key to my computer.
3. Started my computer and entered my login/password when I guessed I was prompted for (!).
4. Pressed Ctrl+Shit+F1 to access a console.
5. Under the console, entered my login/password.
6. Entered "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak to save the current xorg.conf file (what for, anyway?).
You have to use "sudo" in front of the command line instructions to gain root access.
7. Entered the root password (my user password) when prompted.
8. entered "sudo cp /media/usbdisk/xorg.conf /etc/X11/xorg.conf to copy the new xorg.conf file to the right directory.
The usb key was mounted in /media/usb since I launched Gnome at step 3 and HAL detected it.
9. Enter "sudo shutdown -r now" to restart the computer.
10. That was it!

There was still the same problem with the Breezy beta. If filed a bug under bugzilla.

---

