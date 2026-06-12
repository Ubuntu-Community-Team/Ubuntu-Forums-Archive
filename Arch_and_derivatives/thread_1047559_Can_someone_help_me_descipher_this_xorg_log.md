---
title: "Can someone help me descipher this xorg log??"
date: 2009-01-22
forum: Arch and derivatives
---

### Post by pluckypigeon on 2009-01-22
I can't log in to X

This is the xorg log:

```
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 22 20:06:19 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xorg Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Iiyama ProLite E430"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "PS/2 Mouse"
(**) Option "AllowMouseOpenFail" "true"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/PEX" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/cyrillic".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/usr/share/fonts/cyrillic").
(WW) The directory "/usr/share/fonts/ttf/western" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/ttf/decoratives" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/openoffice" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/ttf-bitstream-vera" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/latex-ttf-fonts" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/CID" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/TrueType" does not exist.
    Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/misc,/usr/share/fonts/100dpi:unscaled,/usr/share/fonts/75dpi:unscaled,/usr/share/fonts/TTF,/usr/share/fonts/Type1.
(**) FontPath set to:
    /usr/share/fonts/misc:unscaled,
    /usr/share/fonts/misc,
    /usr/share/fonts/75dpi:unscaled,
    /usr/share/fonts/75dpi,
    /usr/share/fonts/100dpi:unscaled,
    /usr/share/fonts/100dpi,
    /usr/share/fonts/Type1,
    /usr/share/fonts/misc,
    /usr/share/fonts/100dpi:unscaled,
    /usr/share/fonts/75dpi:unscaled,
    /usr/share/fonts/TTF,
    /usr/share/fonts/Type1
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d5fe0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xd0000000/0, 0xdff80000/0
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.3, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(WW) Warning, couldn't open module record
(II) UnloadModule: "record"
(EE) Failed to load module "record" (module does not exist, 0)
(II) LoadModule: "i810"

(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 2.6.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.2, module version = 1.3.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.2, module version = 1.3.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found
```



Thanks in advance

---

### Post by cubeist on 2009-01-22
In general, the EE stands for errors, the WW for warnings, and II for information.  I assume you are wondering why it cannot find your screen.  This means your xorg.conf is not correctly configured for your hardware.

are you running the restricted drivers? have you tried the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by utnubuuser on 2009-01-22
Hi  -- You should probably provide a bit more information here.

What is your machine doing, or not doing that you're expecting it to?  No screen? Are you trying to get a second screen set up? 
Built in graphics or video card?  results of "sudo lspci"?

---

### Post by pluckypigeon on 2009-01-22
Thanks for your quick replies.

I'm just trying to log in and getting no screen.


lspci:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

part of xorg: (I have tried intel and i810 drivers)

```

Section "Monitor"

    Identifier     "Iiyama ProLite E430"
    Option         "DPMS"

EndSection 



Section "Device"
	Identifier  "Card0"
	Driver      "i810"
	VendorName  "All"
	BoardName   "All"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Iiyama ProLite E430"
	DefaultDepth 24
	SubSection     "Display"

        Depth       1

        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection
EndSection


```

---

### Post by fwojciec on 2009-01-22
In either case, you should using intel instead of i810 driver.

Warnings (WW):
[LIST=1]
[*]Fix font paths in xorg.conf -- values defined there should correspond to real directories that exist in the filesystem
[*]Install and run acpid daemon (if you want to, the warning is not fatal)
[/LIST]
Errors (EE):
[LIST=1]
[*]Remove type1 module from modules section in xorg.conf
[*]Remove record module from modules section in xorg.conf
[*]Use driver that supports your chipset (i810 doesn't, like it says in the log)
[/LIST]

---

### Post by utnubuuser on 2009-01-22
Ok, so you're logging in through recovery mode or live cd?  There is no Nvidea card or Radeon card?
Can you access System>>Administration>>Hardware Drivers?

If you're in recovery mode, can you get at the Hardware Drivers through "sudo jockey-gdk"

Has this screen worked before, and when you say "not getting a screen", you mean not getting a login screen, or no signal to the screen at all?

---

### Post by fwojciec on 2009-01-22
Here's a link to a success story with a chipset like yours (I think): [http://bbs.archlinux.org/viewtopic.php?id=60211](http://bbs.archlinux.org/viewtopic.php?id=60211)

---

### Post by pluckypigeon on 2009-01-22
> **fwojciec said:**
> In either case, you should using intel instead of i810 driver.

Warnings (WW):
[LIST=1]
[*]Fix font paths in xorg.conf -- values defined there should correspond to real directories that exist in the filesystem
[*]Install and run acpid daemon (if you want to, the warning is not fatal)
[/LIST]
Errors (EE):
[LIST=1]
[*]Remove type1 module from modules section in xorg.conf
[*]Remove record module from modules section in xorg.conf
[*]Use driver that supports your chipset (i810 doesn't, like it says in the log)
[/LIST]

Thank you. I will get to work on these.

> **utnubuuser said:**
> Ok, so you're logging in through recovery mode or live cd?  There is no Nvidea card or Radeon card?
Can you access System>>Administration>>Hardware Drivers?

If you're in recovery mode, can you get at the Hardware Drivers through "sudo jockey-gdk"

Has this screen worked before, and when you say "not getting a screen", you mean not getting a login screen, or no signal to the screen at all?

I am using Intrepid currently (dual boot with Arch). I don't have a radeon or nvidia.

> **fwojciec said:**
> Here's a link to a success story with a chipset like yours (I think): [http://bbs.archlinux.org/viewtopic.php?id=60211](http://bbs.archlinux.org/viewtopic.php?id=60211)

Thanks. I'll check it out

---

### Post by pluckypigeon on 2009-01-22
BTW I'll report back once I've checked everything out:)

---

### Post by jsegel on 2009-01-23
any luck on this? i'm having a similar problem with intel i810 chipset. fatal server error, no screens found.
also gives an odd error: 
(EE) intel(0) "unable to write to DVOI2C_E Slave 236"
(EE) intel(0) "unable to read from DVOI2C_E Slave 236"
(EE) intel(0) no valid modes

i've tried all sort of editing of xorg.conf, including the suggested links.. 
agh/


extra note: using vesa as driver i do get the xserver to boot, but only to a black screen.

---

### Post by pluckypigeon on 2009-01-23
> **jsegel said:**
> any luck on this? i'm having a similar problem with intel i810 chipset. fatal server error, no screens found.
also gives an odd error: 
(EE) intel(0) "unable to write to DVOI2C_E Slave 236"
(EE) intel(0) "unable to read from DVOI2C_E Slave 236"
(EE) intel(0) no valid modes

i've tried all sort of editing of xorg.conf, including the suggested links.. 
agh/


extra note: using vesa as driver i do get the xserver to boot, but only to a black screen.

Yes.

It's not perfect - the xorg log still has a few errors.


I can't source all of the places where I got the info but here is my xorg.conf and log.

I didn't spend much time on the fonts and other stuff, mainly just on the graphics card. 

I do believe that there is a bug either in the kernel, or even graphics card, which means that I have to add "Option "NoAccel"" - Sometimes x wouldn't start and sometimes it would but bits of windows would be missing.

I switch between xcompmgr with openbox on Arch, and Metacity Composite Manager with Intrepid.

I don't know if you are aware that "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset" is on the compiz blacklist 

Xorg.conf:

```
Section "Monitor"

    Identifier    "Iiyama ProLite E430"
    Option        "DPMS"
     
EndSection

Section "Device"
    Identifier  "Onboad display adapter card"
    Driver   "intel"
    BusID    "PCI:0:2:0"
    #Option  "DRI" "off"
     Option "NoAccel"
     Option   "DPI"    "96 x 96"
     Option         "UseEdidDpi" "false"
    #Option  "AccelMethod" "xaa"
    #Option  "XAANoOffscreenPixmaps" "on"
    #Option   "AccelMethod" "exa"
    #Option   "MigrationHeuristic" "smart"
     Option   "MigrationHeuristic" "greedy"
    #Option  "FramebufferCompression" "on"
    #Option  "Tiling" "on"
     Option "ExaNoComposite" "false"

EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Onboad display adapter card"
    Monitor    "Iiyama ProLite E430"
    DefaultDepth 24
		SubSection "Display"
		Depth     24
		Modes "1280x1024"
	EndSubSection
	
EndSection
```



LOG:

```

X.Org X Server 1.5.3
Release Date: 5 November 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.27-ARCH i686 
Current Operating System: Linux myhost 2.6.28-ARCH #1 SMP PREEMPT Sun Jan 18 20:17:17 UTC 2009 i686
Build Date: 17 December 2008  08:20:05PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 23 21:55:04 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xorg Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Iiyama ProLite E430"
(**) |   |-->Device "Onboad display adapter card"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "PS/2 Mouse"
(**) Option "AllowMouseOpenFail" "true"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
(==) Automatically enabling devices
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/ttf/western".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/ttf/western").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/ttf/decoratives".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/ttf/decoratives").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/truetype").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/openoffice".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/truetype/openoffice").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/ttf-bitstream-vera".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/truetype/ttf-bitstream-vera").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/latex-ttf-fonts".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/latex-ttf-fonts").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/defoma/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/defoma/CID").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/defoma/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/defoma/TrueType").
(==) Including the default font path /usr/share/fonts/misc,/usr/share/fonts/100dpi:unscaled,/usr/share/fonts/75dpi:unscaled,/usr/share/fonts/TTF,/usr/share/fonts/Type1.
(**) FontPath set to:
	/usr/share/fonts/misc:unscaled,
	/usr/share/fonts/misc,
	/usr/share/fonts/75dpi:unscaled,
	/usr/share/fonts/75dpi,
	/usr/share/fonts/100dpi:unscaled,
	/usr/share/fonts/100dpi,
	/usr/share/fonts/PEX,
	/usr/share/fonts/cyrillic,
	/usr/share/fonts/Type1,
	/usr/share/fonts/misc,
	/usr/share/fonts/100dpi:unscaled,
	/usr/share/fonts/75dpi:unscaled,
	/usr/share/fonts/TTF,
	/usr/share/fonts/Type1
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d5fe0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xd0000000/0, 0xdff80000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.3, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 2.4.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "NoAccel"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xDFF80000
(II) intel(0): 1 display pipe available.
(**) intel(0): DRI is disabled because it needs HW cursor and 2D acceleration.
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 8000 kB
(II) intel(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Iiyama ProLite E430
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"

(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"

(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"

(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"

(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"

(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "IVM", prod id 18100
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "IVM", prod id 18100
(II) intel(0): Output VGA connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 8060 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (340, 270) mm
(**) intel(0): DPI set to (119, 150)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000207 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 110336 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 441340 kB available
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Allocating 4800 scanlines for pixmap cache
(II) intel(0): Tiled allocation successful.
(--) intel(0): Xv is disabled because it needs 2D accel and AGPGART.
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007df000 (pgoffset 2015)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x04000000 (pgoffset 16384)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x00004fff: HW cursors (20 kB)
(II) intel(0): 0x00005000-0x0000cfff: logical 3D context (32 kB)
(II) intel(0): 0x007df000:            end of stolen memory
(II) intel(0): 0x007df000-0x007dffff: overlay registers (4 kB, 0x000000001c12a000 physical
)
(II) intel(0): 0x04000000-0x07ffffff: front buffer (51200 kB) X tiled
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): direct rendering: Disabled
(WW) intel(0): Option "DPI" is not used
(WW) intel(0): Option "UseEdidDpi" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used
(WW) intel(0): Option "ExaNoComposite" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/xorg/modules/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 340 x 270
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Keyboard0: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/psaux"
(II) PS/2 Mouse: Setting mouse protocol to "ExplorerPS/2"
(**) PS/2 Mouse: Device: "/dev/psaux"
(**) PS/2 Mouse: Protocol: "auto"
(**) Option "SendCoreEvents" "true"
(**) Option "CorePointer"
(**) PS/2 Mouse: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "true"
(**) Option "Emulate3Timeout" "70"
(**) PS/2 Mouse: Emulate3Buttons, Emulate3Timeout: 70
(**) Option "ZAxisMapping" "4 5"
(**) PS/2 Mouse: ZAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: Buttons: 9
(**) PS/2 Mouse: Sensitivity: 1
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (PS/2 Mouse)
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: Setting mouse protocol to "ExplorerPS/2"
(II) PS/2 Mouse: ps2EnableDataReporting: succeeded
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Macintosh mouse button emulation
(EE) config/hal: NewInputDeviceRequest failed

```

Hope this is useful.

Also have a look at this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871)

---

