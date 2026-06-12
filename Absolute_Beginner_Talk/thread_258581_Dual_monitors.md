---
title: "Dual monitors"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by anti-net on 2006-09-16
Hi, I've just switched to Ubuntu from Windows XP so fair everything has been great apart from I not sure how to set up my other monitor. I have an nvidia 5200 card with 1 DVI and 1 VGA port on it my main monitor is going through the VGA port and the second is going thru the DVI however the the 2rd monitor just has awful mixture of colour on it. 

Does anyone know how I would set this up? 

Thanks, Greg

---

### Post by wishyjr on 2006-09-16
hiya mate, do you have the nvidia drivers installed (the ones from the nvidia site, not the ones that some with ubuntu) installing them might help.

---

### Post by orb9220 on 2006-09-16
You need to install the nvidia drivers and edit xorg.conf file.

nvidia drivers are in synaptic

You have the exact setup I do fx5200 1-17" vga 1-17" dvi to vga converter to monitor.

Below is my xorg.conf backup yours then in terminal
gksudo gedit /etc/X11/xorg.conf

Then look over mine I just copied and paste into mine replacing the same sections.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

### Post by anti-net on 2006-09-16
Thanks that worked perfectly!

---

