---
title: "3D acceleration on Macbook"
date: 2007-07-31
forum: Apple Intel Users
---

### Post by mdh on 2007-07-31
I am running ubuntu feisty fawn 7.04 on my *macbook*. I am having issues with OpenGL apps crashing intermittently. I see that the driver being used is i810 for my integrated Intel graphics card. Is this the only driver you can use with the macbook. I also notice that I am using mesa's OpenGL implementation, running glxinfo like below gives me this 

```
glxinfo | grep OpenGL

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:

```

The same apps which crash on my macbook run fine on my feisty fawn desktop which has a nvidia card and the latest nvidia driver installed. This makes me believe that the problem is related to a malfunctioning or an improperly configured driver. So, my questions are is there a hardware/3D accelerated driver available for macbook or is there a specific configuration for the current driver that I am missing.

I am not sure if this will help, but here are the relevant parts of my xorg.conf

```
Section "Module"
    Load            "glx"
    Load            "extmod"
    Load            "xtrap"
    Load            "record"
    Load            "dbe"
    Load            "dri"
    Load            "freetype"
    Load            "type1"
    Load            "synaptics"
# Disabled for AIGLX
#    Load            "GLcore"
#    Load            "vbe"
EndSection

Section "Device"
    Identifier      "i945GM"
    Driver          "i810"
    VendorName      "Intel Corporation"
    BoardName       "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
# Beryl/Compiz
    Option          "DRI"     "true"
    Option          "XAANoOffscreenPixmaps" "true"
# Xorg.0.log was spitting warnings about BusID
#    BusID           "PCI:0:2:0"
EndSection

```

---

### Post by cyberdork33 on 2007-07-31
use the 'intel' driver not the i810 driver

---

### Post by benanzo on 2007-08-01
Here are the relevant sections in my xorg.conf file.  I have a first-gen MacBook and everything works great.  You might see if my settings work better for you.

```

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
	Load	"v4l"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel GMA950"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"MacBook LCD"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"MacBook Screen"
	Device		"Intel GMA950"
	Monitor		"MacBook LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Good Luck!

---

### Post by mdh on 2007-08-02
Thanks benanzo!. I had to install the xserver-xorg-video-intel package to install the intel driver. For some reason my defualt ubuntu install ignored this package and installed the i810 version.  My apps are still flaky but I guess it might not be due to the driver, it might be because I am using an old old old package called xforms and its interaction with glx might be outdated and hence my woes. But, thanks for your help in getting me to run the latest drivers.

---

