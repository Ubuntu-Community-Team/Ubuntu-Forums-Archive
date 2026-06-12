---
title: "Help with monitor resolution settings in xorg.conf"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-08
Hello i got a question about xorg.conf settings, the thing i want to be able to do, is to change the resolution to 1280x1024x75hz. 

The current settings i can choose from is 640x480x85hz,800x600x85hz,1024x768x85hz.
In Windows XP i can choose and use 1280x1024x75hz so it is possible.

This is how my current xorg.conf looks like.

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	Option          "NoLogo"
	BusID		"PCI:1:0:0"
        Option "TwinView" "true"
   	Option "RenderAccel"           "true"
        Option "AllowGLXWithComposite" "true"
	Option "TwinViewOrientation" "Clone"
	Option "UseEdidFreqs" "FALSE"
	Option "UseEDID" "FALSE"
	Option "ModeValidation" "NoEdidModes"
	Option "TVOutFormat" "S-VIDEO"
	Option "TVStandard" "PAL-B"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
EndSection

Section "Monitor"
	Identifier	"DELL D1025HE"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"DELL D1025HE"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x350" "640x480"
	EndSubSection
EndSection

---

### Post by bruce89 on 2006-06-08
```
sudo dpkg-reconfigure xserver-xorg
``` and follow the instructions.

---

### Post by tommcd on 2006-06-08
I had the same problem. You can:
1) add "1280x1024" to each of the modes under "display" before the "1024x768" resolution. This did not work for me.
2)boot to recovery console and type:
sudo dpkg-reconfigure xserver-xorg
answer defaults to the questions if you are not sure. At the end you will have options for setting monitor resolutions. Select them with the space bar. When finished, type sudo reboot, or sudo etc/init.d/gdm restart to restart X and you should have 1280x1024 resolution.

---

### Post by bikeboy on 2006-06-08
If that isn't enough (sometimes it isn't) you can go into expert mode during the dpkg-reconfigure mentioned above and put in the sync and refresh rates for your monitor, they should be listed in the manual if you have one. This worked for me on a laptop which wouldn't go to its max resolution.

---

### Post by hikitsu4 on 2006-06-08
FIXED it.

---

