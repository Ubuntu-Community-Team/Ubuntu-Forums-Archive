---
title: "Kernel 2.6.24 with 3d graphic acceleration"
date: 2008-02-04
forum: Apple Intel Users
---

### Post by squidleon on 2008-02-04
Hi all,
I've macbook (black model June 2007). I've kernel 2.6.24 on board. What is the module to load in xorg.conf to make 3d acceleration working?

thanks
Tommaso


-- 
squid(at)firenze(dot)linux(dot)it
Key fingerprint = 1024D/87B0EB0A
Linux user #409132
Homepage = [http://blog.xsquid.net](http://blog.xsquid.net)
Jabber: squid(at)firenze(dot)linux(dot)it

---

### Post by hyperair on 2008-02-04
Well what graphic card do you have? Run this command and post the output:
```
lspci -nn
```

---

### Post by squidleon on 2008-02-04
Hi hyperair, thank you for reply!

I've a this Intel GMA 950. I've also installed 915resolution for fix resolution problem.

Tom

---

### Post by hyperair on 2008-02-04
Good to hear that it works.

---

### Post by squidleon on 2008-02-04
Sorry but with 915resolution acceleration does't work...:( What module can i try to load in xorg.conf ?

tom

---

### Post by hyperair on 2008-02-04
Please post the contents of your xorg.conf.

---

### Post by squidleon on 2008-02-04
Ok l'll post the configuration when i come back at home (now i'm at work!) :)


Tom

---

### Post by hyperair on 2008-02-04
Alright, I'll be waiting.

---

### Post by cyberdork33 on 2008-02-04
The "Intel" driver is what you should be using. 915resolution doesn't need to be used anymore.
There is a wiki page detailing the things you need to configure Macbooks (depending which one you have):
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by squidleon on 2008-02-04
Hi, this is my xorg.conf

Tom

```
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by cyberdork33 on 2008-02-04
like i said, use the "intel" driver. You are currently using the i810 driver.

---

### Post by hyperair on 2008-02-04
It is as cyberdork33 says. Use the "intel" driver. So... you have to modify this section:
```
Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"intel" # used to be i810
	Screen	0
	Vendorname	"Intel"
EndSection

``` Notice

---

### Post by cyberdork33 on 2008-02-04
Additionally change the driver in your other device section the same way since you have two.
```
Section "device" # 
    Identifier    "device1"
    Boardname    "Intel 945"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    1
    Vendorname    "Intel"
EndSection
```

---

### Post by squidleon on 2008-02-04
Hi all,
I've modified xorg.cong and restart X

Now the xorg.conf is this 
```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option          "SHMConfig"               "True"
        Option		"VertTwoFingerScroll"   "True"
	Option		"HorizTwoFingerScroll"  "True"
        Option          "RightEdge"     	"1100"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Boardname    "Intel 945"
        Busid        "PCI:0:2:0"
        Driver        "intel"
        Vendorname    "Intel"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```


But if i execute glxinfo i take this..

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:

``` 
Also i've attach the screenshot

Thanks for now!
Tom

---

### Post by squidleon on 2008-02-05
Hi all i've reloved the problem installing:
xlibmesa-dri 
xlibmesa-gl 
xlibmesa-glu 
mesa-utils 
libgl1-mesa-dri 
libgl1-mesa-glx 

Thanks all!
Tom

---

