---
title: "Help with nVidia card"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by butterandguns on 2007-07-18
Okay. So I'm brand new to Uduntu (Just installed it yesterday). Almost everything is perfect except for the fact that my screen seems kind of stretched horizontally. I'm guessing this is a resolution issue. I have an nVidia card. I checked the Screen Resolution Preferences but the only options there are 1024X768, 800X600, and 640X480 and the only option fro refresh rate is 61Hz. 1024X768 is closest to normal but it is still sort of stretched. I read a few of the other posts on this and they tell to use xorg but I'm not sure what to do in xorg. I would really really appreciate step by step detailed instructions on this. Thank you.

lspci says this.
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by njknight on 2007-07-18
Have you tried the envy script available from
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This corrected my laptops display

---

### Post by Outrunner on 2007-07-18
To edit your xorg.conf, go to the terminal and type(or copy&paste):

```
gksudo gedit /etc/X11/xorg.conf
```

Now, scroll down and find 

```
Section "Screen"
```

There will be some resolutions listed for every color depth. Add "1280x1024"(or your preffered resolution) to every color depth. Mine looks like this(as an example)

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
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

```

After this, press CTRL-ALT-BACKSPACE.This will restart the Xserver so make sure you save any unsaved files, documents so that you don't lose your data.

---

### Post by sad_iq on 2007-07-18
First lets see if you have the driver correctly installed and what refresh rates you use...type in a terminal and paste the output:
 ```
cat < /etc/X11/xorg.conf |grep HorizSync && cat < /etc/X11/xorg.conf |grep VertRefresh && cat < /etc/X11/xorg.conf |grep Driver && glxinfo |grep Direct
``` 
 Second of all...what type of monitor you have??? Can you google the refresh rates for it??? Also If you have(had) windows...what was the resolution you used there???

---

