---
title: "i810 running higher than 1024x768 on desktop"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by coldopm on 2006-11-22
Can someone help me out, right now the highest I can run in desktop resolution is 1024x768 and 0htz is the only refresh rate I get. I am currently running the i810 drivers for my card, which to my knowledge are the only ones out there for Edgy. 

Any ideas? I gave up running games but for surfing and such it would be nice to run higher res.

Please help,
Coldopm

---

### Post by coldopm on 2006-11-22
PS I am running a Intel 945GM on board video card.

---

### Post by thk on 2006-11-22
apt-get install 915resolution

???

---

### Post by Afishionado on 2006-11-23
> **thk said:**
> apt-get install 915resolution

???

Uh, no.

You need to edit your xorg.conf file (/etc/X11/xorg.conf). I don't know of a nice point-and-click way to do this, so I'm going to tell you how to do it the nasty way. (Someone holler if they know a better way to do this!)

Fire up your terminal. Change to the correct directory, and make a backup copy of the xorg.conf file:

```
cd /etc/X11
sudo cp xorg.conf xorg.old
```

You'll need this if you mess up. :) If your desktop dies, you'll need to run this later to get it back:

```
cd /etc/X11
sudo cp xorg.old xorg.conf
```

(You might want to write that command down now, just in case.)

With that done, we're ready to tell xorg that your monitor runs at a higher resolution. Run:

```
sudo gedit xorg.conf
```

Find the part in the file labeled

```
Section "Screen"
```

On my machine, it looks like this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

If you're at all hesitant, just copy and paste this code here so that we can look at it and give you more specific directions.

If you're impatient, add the correct resolution to the Modes lists, and save the file. Log out of Ubuntu, so that you're looking at the login screen. Press ctrl+alt+backspace to restart xorg; your screen will flicker when you do this. Then, log in again and Gnome should make the new resolution available to you.

William

---

### Post by coldopm on 2006-11-23
Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

_________


Looks like all I changed was added a new res setting. Should theoretically work now.

I will keep you posted!

---

### Post by coldopm on 2006-11-23
Well after experimenting, the long way, from highest to lowst and through processes of elimination I have determined that unless I can get driver that work properly with my Video Card, I cannot do much while running Ubuntu, when it come to OpenGL or Direct 3D. 

Anyone have any other Ideas?

BTW ^^ your idea worked it just wont register anything higher than 1024x768 ](*,)

---

### Post by Afishionado on 2006-11-23
> **coldopm said:**
> Well after experimenting, the long way, from highest to lowst and through processes of elimination I have determined that unless I can get driver that work properly with my Video Card, I cannot do much while running Ubuntu, when it come to OpenGL or Direct 3D. 

Join the club. :) The laptop I'm on right now has a video card that I can't get any OpenGL support for (under Linux or Windows, actually).

Hit the command line again and try:

```
sudo lspci
```

Find the entry in the output for your video card, and copy/paste that into Google. There's an off chance that you might still find a decent Linux driver for it.

William

---

### Post by DarkN00b on 2006-11-23
coldopm,

You're not running the correct driver for your i810. Look at the third line under Section "Device". You are running the default vesa driver. Make sure you have the i810 driver package installed and change that "vesa" to "i810". [color="red"]Do not change this if the i810 driver package is not installed![/color] See if that helps.

The i810 package can be found in Synaptic package manager, just search for "i810" (without the quotes). Select the driver and mark it for install. Once the driver is installed, then *and only then* change the "vesa" to "i810" and hit ctrl+alt+backspace to restart your desktop and check your resolution options. This will also enable 3d rendering such as it is with the i810 chipset. I can't complain too much about mine. :)

---

### Post by thk on 2006-11-26
> **Afishionado said:**
> 
You need to edit your xorg.conf file (/etc/X11/xorg.conf). I don't know of a nice point-and-click way to do this, so I'm going to tell you how to do it the nasty way. (Someone holler if they know a better way to do this!)
William
Does dpkg-reconfigure xserver-xorg work?

---

