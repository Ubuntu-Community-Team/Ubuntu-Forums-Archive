---
title: "Cannot logon"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by mooreted on 2006-09-17
I can't logon to Ubuntu. I enter my username and password and the screen goes black for a moment then the Ubuntu logon screen comes back up. This is after the latest updates.

I can drop down to the CLI and logon, but I can't get to the desktop from there.

There are absolutely no error messages.

---

### Post by baldy1324 on 2006-09-17
ok this is weird. here are some suggestions.-
```
sudo dpkg-reconfigure gdm
```
this will reconfigure your login-manger (gdm)

in the meantime if that dosent work just try to go into command line mode and type ```
startx
```. this should bring up gnome.

---

### Post by ZERO_SHIFT on 2006-09-17
I'am not sure but you might want to lower the screen res. in the configuration before attempting to log in.

---

### Post by mooreted on 2006-09-17
> **ZERO_SHIFT said:**
> I'am not sure but you might want to lower the screen res. in the configuration before attempting to log in.

I haven't changed anything so the screen res should not matter. I just updated Ubuntu, rebooted and wham, no logon.

I will try the suggestions and see what happens.

Thanks.

---

### Post by mooreted on 2006-09-18
Okay, that didn't work. I ran sudo dpkg-reconfigure gdm. When I startx I get this error:

Fatal server error
Server is already active for display 0.

xlib: Connection to ":0.0" refused by server.
xlib: No protocol specified
giving up
xinit: unable to connect to X server
xinit: No such process (erno 3): server error

---

### Post by ZERO_SHIFT on 2006-09-18
I am sorry to hear that. Mabye you could re-install dapper. You may also want to try searching for other soloutions; otherwise I think you should format.

---

### Post by mooreted on 2006-09-19
Well, that's a bummer. I guess I'll back up my stuff up and start over.

Thanks anyway.

---

### Post by rgould on 2006-09-24
I'm experiencing similar problems. GDM starts up and I can enter my username and password okay, but after entering (and using a Gnome session), Gnome does not start up properly. All I get is a white mouse cursor on a brown background.

I ran dpkg-reconfigure on gdm and gnome-panel to no effect. Is there a log file somewhere I can check?

---

### Post by rgould on 2006-09-24
Cool. One (or more) of these reconfigures fixed it:

```

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

```

I would guess that session would be the one that fixed it, but I just ran them all and restarted the X server.

---

### Post by Chitownmack on 2006-11-04
I was having the same problem after I updated my startup script to start my wireless usb card. (May not be related but figured that I would mention it.)

The below piece of code did the fix for me. (I ran through the prompts until it reconfigured then rebooted my machine and it worked fine.)


sudo dpkg-reconfigure gnome-applets

---

### Post by Chitownmack on 2006-11-05
I retract What I said earlier because it did not work for me. (After performing the following command... sudo dpkg-reconfigure gnome-applets)  I can log on one time successfully but when I log out and back in with any account, .25% of my screen in the upper left hand corner turns white and hangs for about 5 minutes then prompts me with the following message. "there was an error starting the GNOME settings daemon" 

There has been a [bug reported]("https://launchpad.net/distros/ubuntu/+bug/68284") on this issue but I can't figure out if there is a fix for it or not.. any ideas

Im including my some of my XORG log for review and let me know if you want anymore information. Thanks

_XORG_

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux 067 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  5 00:13:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "CPQ TFT5015"
(**) |   |-->Device "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 12 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 12 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 0e11,2411 rev 12 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 0e11,2411 rev 12 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002c card 10de,0072 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:04:0: chip 1033,0035 card 0caf,a600 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:04:1: chip 1033,0035 card 0caf,a600 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:04:2: chip 1033,00e0 card 0caf,a6e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 0e11,0012 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 11c1,0450 card 144f,1515 rev 02 class 07,80,00 hdr 00
(II) PCI: 02:0b:0: chip 1102,0002 card 1102,8064 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:0b:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfe1fffff (0x1200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf5e00000 - 0xf7ffffff (0x2200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfc200000 - 0xfc4fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV6 [Vanta/Vanta LT] rev 21, Mem @ 0xfd000000/24, 0xf6000000/25
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfc403100 - 0xfc4031ff (0x100) MX[B]
	[1] -1	0	0xfc402000 - 0xfc402fff (0x1000) MX[B]
	[2] -1	0	0xfc403000 - 0xfc4030ff (0x100) MX[B]
	[3] -1	0	0xfc401000 - 0xfc401fff (0x1000) MX[B]
	[4] -1	0	0xfc400000 - 0xfc400fff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00001468 - 0x0000146f (0x8) IX[B]
	[9] -1	0	0x00001440 - 0x0000145f (0x20) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x00001460 - 0x00001467 (0x8) IX[B]
	[12] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[13] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[14] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfc403100 - 0xfc4031ff (0x100) MX[B]
	[1] -1	0	0xfc402000 - 0xfc402fff (0x1000) MX[B]
	[2] -1	0	0xfc403000 - 0xfc4030ff (0x100) MX[B]
	[3] -1	0	0xfc401000 - 0xfc401fff (0x1000) MX[B]
	[4] -1	0	0xfc400000 - 0xfc400fff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00001468 - 0x0000146f (0x8) IX[B]
	[9] -1	0	0x00001440 - 0x0000145f (0x20) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x00001460 - 0x00001467 (0x8) IX[B]
	[12] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[13] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[14] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset Vanta found
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "Vanta"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF6000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: CPQ  Model: 1394  Serial#: 1813463664
(II) NV(0): Year: 2001  Week: 42
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 30  vert.: 22
(II) NV(0): Gamma: 1.98
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.599 redY: 0.341   greenX: 0.282 greenY: 0.557
(II) NV(0): blueX: 0.146 blueY: 0.102   whiteX: 0.313 whiteY: 0.339
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 61 kHz, PixClock max 80 MHz
(II) NV(0): Monitor name: CPQ TFT5015
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 16384 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): CPQ TFT5015: Using default hsync range of 31.00-61.00 kHz
(II) NV(0): CPQ TFT5015: Using default vrefresh range of 56.00-75.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(WW) (1024x768,CPQ TFT5015) mode clock 94.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(WW) (1152x864,CPQ TFT5015) mode clock 108MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(WW) (1280x960,CPQ TFT5015) mode clock 108MHz exceeds DDC maximum 80MHz
(WW) (1280x960,CPQ TFT5015) mode clock 148.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,CPQ TFT5015) mode clock 108MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,CPQ TFT5015) mode clock 135MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,CPQ TFT5015) mode clock 157.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,CPQ TFT5015) mode clock 162MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,CPQ TFT5015) mode clock 81MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,CPQ TFT5015) mode clock 175.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,CPQ TFT5015) mode clock 87.75MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,CPQ TFT5015) mode clock 189MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,CPQ TFT5015) mode clock 94.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,CPQ TFT5015) mode clock 202.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,CPQ TFT5015) mode clock 101.25MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,CPQ TFT5015) mode clock 229.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,CPQ TFT5015) mode clock 114.75MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,CPQ TFT5015) mode clock 204.8MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,CPQ TFT5015) mode clock 102.4MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,CPQ TFT5015) mode clock 261MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,CPQ TFT5015) mode clock 130.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,CPQ TFT5015) mode clock 218.3MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,CPQ TFT5015) mode clock 109.15MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,CPQ TFT5015) mode clock 288MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,CPQ TFT5015) mode clock 144MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,CPQ TFT5015) mode clock 234MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,CPQ TFT5015) mode clock 117MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,CPQ TFT5015) mode clock 297MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,CPQ TFT5015) mode clock 148.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1280x768,CPQ TFT5015) mode clock 80.14MHz exceeds DDC maximum 80MHz
(WW) (1280x800,CPQ TFT5015) mode clock 83.46MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NV(0): Not using default mode "576x384" (vrefresh out of range)
(WW) (1152x864,CPQ TFT5015) mode clock 121.5MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,CPQ TFT5015) mode clock 122MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,CPQ TFT5015) mode clock 151MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,CPQ TFT5015) mode clock 155.8MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,CPQ TFT5015) mode clock 184MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(WW) (700x525,CPQ TFT5015) mode clock 92MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1440x900,CPQ TFT5015) mode clock 108.84MHz exceeds DDC maximum 80MHz
(WW) (1600x1024,CPQ TFT5015) mode clock 106.91MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(WW) (1680x1050,CPQ TFT5015) mode clock 147.14MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(WW) (1920x1200,CPQ TFT5015) mode clock 193.16MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,CPQ TFT5015) mode clock 96.58MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,CPQ TFT5015) mode clock 230MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,CPQ TFT5015) mode clock 115MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,CPQ TFT5015) mode clock 341.35MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,CPQ TFT5015) mode clock 170.675MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(WW) (1024x768,CPQ TFT5015) mode clock 133.475MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(WW) (1024x768,CPQ TFT5015) mode clock 170.24MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(WW) (1024x768,CPQ TFT5015) mode clock 194.02MHz exceeds DDC maximum 80MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using mode "720x400" (no mode of this name)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(--) NV(0): Display dimensions: (300, 220) mm
(--) NV(0): DPI set to (86, 88)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

(==) NV(0): Write-combining range (0xf6000000,0x1000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		18 256x256 slots
		6 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

---

### Post by Vincent_Lin on 2006-11-09
I have dapper installed on my X31 laptop.  It happened very similar to yours after sudo apt-get update and sudo apt-get upgrade.  What I did?  I login to safe mode, complete remove xorg xservers, and re-installed open source radeon xserver for my ati mobility.  Now it has been back to normal with direct-rendering enabled.

I guess apt-get update/upgrade sometimes corrupt files.

Vincent

---

### Post by Zarephath on 2006-11-09
You could just go to another tty and do: sudo passwd username and see if that works...if not you will have to verify your username...but a better option just for troubleshooting would be to add a new user and change the password for the new user..then see if you can login using gdm...

---

### Post by Chitownmack on 2006-11-11
> **Vincent_Lin said:**
> I have dapper installed on my X31 laptop.  It happened very similar to yours after sudo apt-get update and sudo apt-get upgrade.  What I did?  I login to safe mode, complete remove xorg xservers, and re-installed open source radeon xserver for my ati mobility.  Now it has been back to normal with direct-rendering enabled.

I guess apt-get update/upgrade sometimes corrupt files.

Vincent

You have a good idea going... I'm going to give your suggestion a try either tonight or tomorrow then post the results. Thanks.

---

### Post by Chitownmack on 2006-11-11
> **Zarephath said:**
> You could just go to another tty and do: sudo passwd username and see if that works...if not you will have to verify your username...but a better option just for troubleshooting would be to add a new user and change the password for the new user..then see if you can login using gdm...

I tried both suggestions but I still have the same symptoms.

 What happens to gdm when you 1.add a new user and change the password or 2. change my password then log off and back on?

Thanks.

---

### Post by nothi on 2006-11-11
I have the same problem, but on KDE running on Edgy. Did anybody find working solution for this problem? Please help, I do not want to install my OS for the third time this month!

I tried this:
```
sudo dpkg-reconfigure kdm
```
But no result.

Help, help!

---

### Post by johanbr on 2007-04-13
I have the same problem with xubuntu on my server, it happend over night. Yesterday it worked fine. Now when i try to login, the screen goes black. Two seconds later the login screen appears again. No message. Remote login with SSH works good, so the user/pass are okej. 

What can it be? Someone solved this problem?

---

### Post by johanbr on 2007-04-13
Solved it. I checked the syslog, out of diskspace :oops:

---

### Post by stmiller on 2007-04-17
Bumping this thread up. After updating my Feisty, I'm getting the blank brown screen after the gdm login. 

Looking at /var/log/messages

it seems to be a permissions problem.

I have the curious lines
gconfd (stmiller-4630): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory......"

---

