---
title: "Screen Res mystery"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by nnjond on 2008-04-12
Hi, can anyone help me?

I have re-installed 7.10 plus updates, but my scrn res is now stuck at 1280x 800 @ 60Hz when before it was the more suitable 1600x1200@ 75Hz.  1600x1200 isn't even an option in the drop down menu?

sudo dpkg-reconfigure xserver-xorg  seems to pick out the right card but i don't get any option to change res and refresh?

---

### Post by Diabolis on 2008-04-12
xserver-xorg  does ask you for the screen reslution, 100% sure of that. If you want to write manually the refresh rate, pick advance while doing the monitor configuration.

You can also modify this values directly to the configuration file.
```
sudo gedit /etc/X11/xorg.conf
```


[go here]("http://ubuntuforums.org/showthread.php?t=753282")

---

### Post by nnjond on 2008-04-13
Thanks for your help.

Sorry I don't know my way around the Terminal

sudo dpkg-reconfigure xserver-xorg  does identify my card all right;  SiS 760.

but my 1st problem is how to edit the  line:

Systems [ SiS] 661/741/760 	PCI/AGP or  662/761Gx  PCIE VGA Display Adapter

How ever I edit seems to take me to the next page with no options?

Do you see a way whereby I can return to 1600x1200@ 75 Hz?

Section "Device"

	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

	Driver		"sis"

	BusID		"PCI:1:0:0"

EndSection



Section "Monitor"

	Identifier	"Generic Monitor"

	Option		"DPMS"

	HorizSync	30-70

	VertRefresh	50-160

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

	Monitor		"Generic Monitor"

	DefaultDepth	24

---

### Post by Diabolis on 2008-04-13
You can make the ghanges directly to the file, just edit it with gedit and root privileges. After you are done, restart xserver with **ctrl + alt + backspace**

I think it will be better to you to do it through the **dpkg-reconfigure** method. You'll get to appoint where you'll be asked to input your monitor or if you want it to be autodetected, after that you'll be asked for the resolutions that you want to use, then you'll be asked which configuration you want to do. Pick **advanced** so you can type in the refresh rates.

> **Section "Monitor"**

Identifier "Generic Monitor"

Option "DPMS"
[B]
HorizSync 30-70[/B]

**VertRefresh 50-160**

EndSection
[B]
Section "Screen"[/B]

Identifier "Default Screen"

Device "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

Monitor "Generic Monitor"

DefaultDepth 24
[B]SubSection "Display"
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
[/B]


---

### Post by Zralou on 2008-04-13
Search google for your monitor specs, and set the 'horizsync' and 'vertrefresh' to what your monitor should be.

Sara Lou

---

