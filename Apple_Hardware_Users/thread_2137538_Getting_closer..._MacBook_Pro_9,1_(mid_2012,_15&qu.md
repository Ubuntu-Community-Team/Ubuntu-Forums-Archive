---
title: "Getting closer... MacBook Pro 9,1 (mid 2012, 15&quot; non-retina) Intel GPU"
date: 2013-04-21
forum: Apple Hardware Users
---

### Post by philcolbourn on 2013-04-21
I am trying to get Nvidia GPU turned off so I can reduce power consumption.

I think I am close so I'll post what I have managed to do.

I used gfxcardstatus v2.2.1 from here [http://www.downloadcrew.com/article/27732-gfxcardstatus]("http://www.downloadcrew.com/article/27732-gfxcardstatus")

Unzip it in OS-X, run it, select Internal Only, I also set Integrated for AC and battery operation, then shutdown OS-X - I think quitting gfxcardstatus before shutting down does not work.

Boot to Linux. I' using rEFInd (beautiful system).

I have this command line - compiled from many locations. Not perfect, but a start.

I'm using 3.7.5 kernel from ppa mainline [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and a pre-release Raring 13.04 (upgraded 20/4/2013).

```
cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-3.7.5-030705-generic root=UUID=c5fdc871-7c20-4563-bf3b-8f42f36e21b2 ro modeset=1 splash i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1

```

Intel Xorg driver seems to be working.

What I don't seem to have is ```
/sys/kernel/debug/vgaswitcheroo/switch
```

And... power consumption is still high. But since this is first time I got Intel GPU to work, I felt it worthwhile to share.

```
[    26.908] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    26.908] X Protocol Version 11, Revision 0
[    26.908] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    26.908] Current Operating System: Linux rex 3.7.5-030705-generic #201301280206 SMP Mon Jan 28 07:07:29 UTC 2013 x86_64
[    26.908] Kernel command line: BOOT_IMAGE=/vmlinuz-3.7.5-030705-generic root=UUID=c5fdc871-7c20-4563-bf3b-8f42f36e21b2 ro modeset=1 splash i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1
[    26.909] Build Date: 17 April 2013  10:43:13PM
[    26.909] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    26.909] Current version of pixman: 0.28.2
[    26.909] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.909] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.909] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 21 18:14:07 2013
[    26.928] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.928] (==) No Layout section.  Using the first Screen section.
[    26.928] (==) No screen section available. Using defaults.
[    26.928] (**) |-->Screen "Default Screen Section" (0)
[    26.928] (**) |   |-->Monitor "<default monitor>"
[    26.928] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.928] (==) Automatically adding devices
[    26.928] (==) Automatically enabling devices
[    26.928] (==) Automatically adding GPU devices
[    26.928] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    26.928] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.928] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.928] (II) Loader magic: 0x7fa523b45d20
[    26.928] (II) Module ABI versions:
[    26.928] 	X.Org ANSI C Emulation: 0.4
[    26.928] 	X.Org Video Driver: 13.1
[    26.928] 	X.Org XInput driver : 18.0
[    26.928] 	X.Org Server Extension : 7.0
[    26.928] (II) config/udev: Adding drm device (/dev/dri/card0)
[    26.929] (--) PCI:*(0:0:2:0) 8086:0166:106b:00fb rev 9, Mem @ 0xc1400000/4194304, 0xb0000000/268435456, I/O @ 0x00003000/64
[    26.930] (--) PCI: (0:1:0:0) 10de:0fd5:106b:00fc rev 161, Mem @ 0xc0000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    26.930] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.930] Initializing built-in extension Generic Event Extension
[    26.930] Initializing built-in extension SHAPE
[    26.930] Initializing built-in extension MIT-SHM
[    26.930] Initializing built-in extension XInputExtension
[    26.930] Initializing built-in extension XTEST
[    26.930] Initializing built-in extension BIG-REQUESTS
[    26.930] Initializing built-in extension SYNC
[    26.930] Initializing built-in extension XKEYBOARD
[    26.930] Initializing built-in extension XC-MISC
[    26.930] Initializing built-in extension SECURITY
[    26.930] Initializing built-in extension XINERAMA
[    26.930] Initializing built-in extension XFIXES
[    26.930] Initializing built-in extension RENDER
[    26.930] Initializing built-in extension RANDR
[    26.930] Initializing built-in extension COMPOSITE
[    26.930] Initializing built-in extension DAMAGE
[    26.930] Initializing built-in extension MIT-SCREEN-SAVER
[    26.930] Initializing built-in extension DOUBLE-BUFFER
[    26.930] Initializing built-in extension RECORD
[    26.930] Initializing built-in extension DPMS
[    26.930] Initializing built-in extension X-Resource
[    26.930] Initializing built-in extension XVideo
[    26.930] Initializing built-in extension XVideo-MotionCompensation
[    26.930] Initializing built-in extension SELinux
[    26.930] Initializing built-in extension XFree86-VidModeExtension
[    26.930] Initializing built-in extension XFree86-DGA
[    26.930] Initializing built-in extension XFree86-DRI
[    26.930] Initializing built-in extension DRI2
[    26.930] (II) LoadModule: "glx"
[    26.958] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.958] (II) Module glx: vendor="X.Org Foundation"
[    26.958] 	compiled for 1.13.3, module version = 1.0.0
[    26.958] 	ABI class: X.Org Server Extension, version 7.0
[    26.958] (==) AIGLX enabled
[    26.958] Loading extension GLX
[    26.958] (==) Matched intel as autoconfigured driver 0
[    26.958] (==) Matched intel as autoconfigured driver 1
[    26.958] (==) Matched vesa as autoconfigured driver 2
[    26.958] (==) Matched modesetting as autoconfigured driver 3
[    26.958] (==) Matched fbdev as autoconfigured driver 4
[    26.958] (==) Assigned the driver to the xf86ConfigLayout
[    26.958] (II) LoadModule: "intel"
[    26.958] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.994] (II) Module intel: vendor="X.Org Foundation"
[    26.994] 	compiled for 1.13.2.902, module version = 2.21.6
[    26.994] 	Module class: X.Org Video Driver
[    26.994] 	ABI class: X.Org Video Driver, version 13.1
[    26.994] (II) LoadModule: "vesa"
[    26.994] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.994] (II) Module vesa: vendor="X.Org Foundation"
[    26.994] 	compiled for 1.13.0, module version = 2.3.2
[    26.994] 	Module class: X.Org Video Driver
[    26.994] 	ABI class: X.Org Video Driver, version 13.0
[    26.994] (II) LoadModule: "modesetting"
[    26.994] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.994] (II) Module modesetting: vendor="X.Org Foundation"
[    26.994] 	compiled for 1.13.3, module version = 0.7.0
[    26.994] 	Module class: X.Org Video Driver
[    26.994] 	ABI class: X.Org Video Driver, version 13.1
[    26.994] (II) LoadModule: "fbdev"
[    26.994] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.994] (II) Module fbdev: vendor="X.Org Foundation"
[    26.994] 	compiled for 1.12.99.903, module version = 0.4.3
[    26.994] 	Module class: X.Org Video Driver
[    26.994] 	ABI class: X.Org Video Driver, version 13.0
[    26.994] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    26.995] (II) VESA: driver for VESA chipsets: vesa
[    26.995] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.995] (II) FBDEV: driver for framebuffer: fbdev
[    26.995] (++) using VT number 7

[    26.995] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6+git20130416.ddd3cc4e-0ubuntu0sarvatt~quantal (Robert Hooker <sarvatt@ubuntu.com>)
[    26.995] (WW) Falling back to old probe method for vesa
[    26.995] (WW) Falling back to old probe method for modesetting
[    26.995] (WW) Falling back to old probe method for fbdev
[    26.995] (II) Loading sub module "fbdevhw"
[    26.995] (II) LoadModule: "fbdevhw"
[    26.995] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.995] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.995] 	compiled for 1.13.3, module version = 0.0.2
[    26.995] 	ABI class: X.Org Video Driver, version 13.1
[    26.996] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.996] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.996] (==) intel(0): RGB weight 888
[    26.996] (==) intel(0): Default visual is TrueColor
[    26.996] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    26.996] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    26.996] (**) intel(0): Framebuffer tiled
[    26.996] (**) intel(0): Pixmaps tiled
[    26.996] (**) intel(0): "Tear free" disabled
[    26.996] (**) intel(0): Forcing per-crtc-pixmaps? no
[    26.996] (II) intel(0): Output LVDS1 has no monitor section
[    26.996] (--) intel(0): found backlight control interface gmux_backlight (type 'platform')
[    27.028] (II) intel(0): Output VGA1 has no monitor section
[    27.028] (II) intel(0): EDID for output LVDS1
[    27.028] (II) intel(0): Manufacturer: APP  Model: 9cb7  Serial#: 0
[    27.028] (II) intel(0): Year: 2009  Week: 22
[    27.028] (II) intel(0): EDID Version: 1.3
[    27.028] (II) intel(0): Digital Display Input
[    27.028] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    27.028] (II) intel(0): Gamma: 2.20
[    27.028] (II) intel(0): No DPMS capabilities specified
[    27.028] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.028] (II) intel(0): First detailed timing is preferred mode
[    27.028] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.310 greenY: 0.610
[    27.028] (II) intel(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    27.028] (II) intel(0): Manufacturer's mask: 0
[    27.028] (II) intel(0): Supported detailed timing:
[    27.028] (II) intel(0): clock: 119.0 MHz   Image Size:  331 x 207 mm
[    27.028] (II) intel(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    27.028] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    27.028] (II) intel(0): Unknown vendor-specific block 1
[    27.028] (II) intel(0):  LTN154MT07
[    27.028] (II) intel(0): Monitor name: Color LCD
[    27.028] (II) intel(0): EDID (in hex):
[    27.028] (II) intel(0): 	00ffffffffffff000610b79c00000000
[    27.028] (II) intel(0): 	16130103802115780ae585a3544f9c26
[    27.028] (II) intel(0): 	0e505400000001010101010101010101
[    27.028] (II) intel(0): 	0101010101017c2e90a0601a1e403020
[    27.028] (II) intel(0): 	36004bcf100000190000000100061030
[    27.028] (II) intel(0): 	00000000000000000a20000000fe004c
[    27.028] (II) intel(0): 	544e3135344d543037000a20000000fc
[    27.028] (II) intel(0): 	00436f6c6f72204c43440a2020200008
[    27.028] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    27.028] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    27.028] (II) intel(0): Printing probed modes for output LVDS1
[    27.028] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    27.028] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    27.028] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    27.028] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    27.028] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    27.028] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    27.028] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    27.028] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    27.028] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    27.028] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    27.028] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    27.028] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    27.028] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    27.060] (II) intel(0): EDID for output VGA1
[    27.060] (II) intel(0): Output LVDS1 connected
[    27.060] (II) intel(0): Output VGA1 disconnected
[    27.060] (II) intel(0): Using exact sizes for initial modes
[    27.060] (II) intel(0): Output LVDS1 using initial mode 1680x1050
[    27.060] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.060] (==) intel(0): DPI set to (96, 96)
[    27.060] (II) Loading sub module "dri2"
[    27.060] (II) LoadModule: "dri2"
[    27.060] (II) Module "dri2" already built-in
[    27.060] (II) UnloadModule: "vesa"
[    27.060] (II) Unloading vesa
[    27.060] (II) UnloadModule: "modesetting"
[    27.060] (II) Unloading modesetting
[    27.060] (II) UnloadModule: "fbdev"
[    27.060] (II) Unloading fbdev
[    27.060] (II) UnloadSubModule: "fbdevhw"
[    27.060] (II) Unloading fbdevhw
[    27.060] (==) Depth 24 pixmap format is 32 bpp
[    27.103] (II) intel(0): SNA initialized with IvyBridge backend
[    27.103] (==) intel(0): Backing store disabled
[    27.103] (==) intel(0): Silken mouse enabled
[    27.103] (II) intel(0): HW Cursor enabled
[    27.103] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.103] (==) intel(0): DPMS enabled
[    27.103] (II) intel(0): [DRI2] Setup complete
[    27.103] (II) intel(0): [DRI2]   DRI driver: i965
[    27.103] (II) intel(0): direct rendering: DRI2 Enabled
[    27.103] (==) intel(0): hotplug detection: "enabled"
[    27.103] (--) RandR disabled
[    27.106] (II) SELinux: Disabled on system
[    27.107] (EE) AIGLX error: dlopen of /usr/lib/x86_64-linux-gnu/dri/i965_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/i965_dri.so: cannot open shared object file: No such file or directory)
[    27.107] (EE) AIGLX: reverting to software rendering
[    27.107] (II) AIGLX: Screen 0 is not DRI capable
[    27.107] (EE) AIGLX error: dlopen of /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
[    27.107] (EE) GLX: could not load software renderer
[    27.107] (II) GLX: no usable GL providers found for screen 0
[    27.107] (II) intel(0): switch to mode 1680x1050 on crtc 3 (pipe 0)
[    27.148] (II) intel(0): Setting screen physical size to 444 x 277
[    27.201] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.202] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    27.202] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.202] (II) LoadModule: "evdev"
[    27.202] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.221] (II) Module evdev: vendor="X.Org Foundation"
[    27.221] 	compiled for 1.13.3, module version = 2.7.3
[    27.221] 	Module class: X.Org XInput Driver
[    27.221] 	ABI class: X.Org XInput driver, version 18.0
[    27.221] (II) Using input driver 'evdev' for 'Power Button'
[    27.221] (**) Power Button: always reports core events
[    27.221] (**) evdev: Power Button: Device: "/dev/input/event3"
[    27.221] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.221] (--) evdev: Power Button: Found keys
[    27.221] (II) evdev: Power Button: Configuring as keyboard
[    27.221] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    27.221] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.221] (**) Option "xkb_rules" "evdev"
[    27.221] (**) Option "xkb_model" "pc105"
[    27.221] (**) Option "xkb_layout" "us"
[    27.222] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    27.222] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.222] (II) Using input driver 'evdev' for 'Video Bus'
[    27.222] (**) Video Bus: always reports core events
[    27.222] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    27.222] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.222] (--) evdev: Video Bus: Found keys
[    27.222] (II) evdev: Video Bus: Configuring as keyboard
[    27.222] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9/event9"
[    27.222] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.222] (**) Option "xkb_rules" "evdev"
[    27.222] (**) Option "xkb_model" "pc105"
[    27.222] (**) Option "xkb_layout" "us"
[    27.222] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    27.222] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.222] (II) Using input driver 'evdev' for 'Video Bus'
[    27.222] (**) Video Bus: always reports core events
[    27.222] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    27.222] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.222] (--) evdev: Video Bus: Found keys
[    27.222] (II) evdev: Video Bus: Configuring as keyboard
[    27.222] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8/event8"
[    27.222] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    27.222] (**) Option "xkb_rules" "evdev"
[    27.222] (**) Option "xkb_model" "pc105"
[    27.222] (**) Option "xkb_layout" "us"
[    27.223] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.223] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.223] (II) Using input driver 'evdev' for 'Power Button'
[    27.223] (**) Power Button: always reports core events
[    27.223] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.223] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.223] (--) evdev: Power Button: Found keys
[    27.223] (II) evdev: Power Button: Configuring as keyboard
[    27.223] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    27.223] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    27.223] (**) Option "xkb_rules" "evdev"
[    27.223] (**) Option "xkb_model" "pc105"
[    27.223] (**) Option "xkb_layout" "us"
[    27.223] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    27.223] (II) No input driver specified, ignoring this device.
[    27.223] (II) This device may have been added with another device file.
[    27.223] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    27.223] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.223] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.223] (**) Sleep Button: always reports core events
[    27.223] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    27.223] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    27.223] (--) evdev: Sleep Button: Found keys
[    27.223] (II) evdev: Sleep Button: Configuring as keyboard
[    27.223] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    27.223] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    27.223] (**) Option "xkb_rules" "evdev"
[    27.223] (**) Option "xkb_model" "pc105"
[    27.223] (**) Option "xkb_layout" "us"
[    27.224] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    27.224] (II) No input driver specified, ignoring this device.
[    27.224] (II) This device may have been added with another device file.
[    27.224] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event16)
[    27.224] (II) No input driver specified, ignoring this device.
[    27.224] (II) This device may have been added with another device file.
[    27.224] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event17)
[    27.224] (II) No input driver specified, ignoring this device.
[    27.224] (II) This device may have been added with another device file.
[    27.224] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    27.224] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.224] (II) config/udev: Adding input device FaceTime HD Camera (Built-in) (/dev/input/event14)
[    27.224] (**) FaceTime HD Camera (Built-in): Applying InputClass "evdev keyboard catchall"
[    27.224] (II) Using input driver 'evdev' for 'FaceTime HD Camera (Built-in)'
[    27.224] (**) FaceTime HD Camera (Built-in): always reports core events
[    27.224] (**) evdev: FaceTime HD Camera (Built-in): Device: "/dev/input/event14"
[    27.224] (--) evdev: FaceTime HD Camera (Built-in): Vendor 0x5ac Product 0x8509
[    27.224] (--) evdev: FaceTime HD Camera (Built-in): Found keys
[    27.224] (II) evdev: FaceTime HD Camera (Built-in): Configuring as keyboard
[    27.224] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input14/event14"
[    27.224] (II) XINPUT: Adding extended input device "FaceTime HD Camera (Built-in)" (type: KEYBOARD, id 11)
[    27.224] (**) Option "xkb_rules" "evdev"
[    27.224] (**) Option "xkb_model" "pc105"
[    27.224] (**) Option "xkb_layout" "us"
[    27.224] (II) config/udev: Adding input device HDA Intel PCH SPDIF In (/dev/input/event10)
[    27.224] (II) No input driver specified, ignoring this device.
[    27.224] (II) This device may have been added with another device file.
[    27.225] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event11)
[    27.225] (II) No input driver specified, ignoring this device.
[    27.225] (II) This device may have been added with another device file.
[    27.225] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    27.225] (II) No input driver specified, ignoring this device.
[    27.225] (II) This device may have been added with another device file.
[    27.225] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event4)
[    27.225] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[    27.225] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    27.225] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    27.225] (**) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event4"
[    27.225] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Vendor 0x5ac Product 0x252
[    27.225] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Found keys
[    27.225] (II) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[    27.225] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.3/2-1.8.3:1.0/input/input4/event4"
[    27.225] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD, id 12)
[    27.225] (**) Option "xkb_rules" "evdev"
[    27.225] (**) Option "xkb_model" "pc105"
[    27.225] (**) Option "xkb_layout" "us"
[    27.225] (II) config/udev: Adding input device bcm5974 (/dev/input/event13)
[    27.225] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[    27.225] (**) bcm5974: Applying InputClass "touchpad catchall"
[    27.225] (**) bcm5974: Applying InputClass "Default clickpad buttons"
[    27.225] (**) bcm5974: Applying InputClass "Disable clickpad buttons on Apple touchpads"
[    27.225] (II) LoadModule: "synaptics"
[    27.225] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.225] (II) Module synaptics: vendor="X.Org Foundation"
[    27.225] 	compiled for 1.13.1.901, module version = 1.6.99
[    27.225] 	Module class: X.Org XInput Driver
[    27.225] 	ABI class: X.Org XInput driver, version 18.0
[    27.225] (II) Using input driver 'synaptics' for 'bcm5974'
[    27.225] (**) bcm5974: always reports core events
[    27.225] (**) Option "Device" "/dev/input/event13"
[    27.265] (II) synaptics: bcm5974: found clickpad property
[    27.265] (--) synaptics: bcm5974: x-axis range -4750 - 5280
[    27.265] (--) synaptics: bcm5974: y-axis range -150 - 6730
[    27.265] (--) synaptics: bcm5974: pressure range 0 - 256
[    27.265] (--) synaptics: bcm5974: finger width range 0 - 16
[    27.265] (--) synaptics: bcm5974: buttons: left double triple
[    27.265] (--) synaptics: bcm5974: Vendor 0x5ac Product 0x252
[    27.265] (**) Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
[    27.265] (--) synaptics: bcm5974: touchpad found
[    27.265] (**) bcm5974: always reports core events
[    27.272] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.3/2-1.8.3:1.2/input/input13/event13"
[    27.272] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD, id 13)
[    27.272] (**) synaptics: bcm5974: (accel) MinSpeed is now constant deceleration 2.5
[    27.272] (**) synaptics: bcm5974: (accel) MaxSpeed is now 1.75
[    27.272] (**) synaptics: bcm5974: (accel) AccelFactor is now 0.016
[    27.272] (**) bcm5974: (accel) keeping acceleration scheme 1
[    27.272] (**) bcm5974: (accel) acceleration profile 1
[    27.272] (**) bcm5974: (accel) acceleration factor: 2.000
[    27.272] (**) bcm5974: (accel) acceleration threshold: 4
[    27.273] (--) synaptics: bcm5974: touchpad found
[    27.273] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
[    27.273] (**) bcm5974: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.273] (II) config/udev: Adding input device applesmc (/dev/input/event7)
[    27.273] (II) No input driver specified, ignoring this device.
[    27.273] (II) This device may have been added with another device file.
[    31.186] (II) intel(0): EDID vendor "APP", prod id 40119
[    31.186] (II) intel(0): Printing DDC gathered Modelines:
[    31.186] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    32.041] (II) intel(0): EDID vendor "APP", prod id 40119
[    32.041] (II) intel(0): Printing DDC gathered Modelines:
[    32.041] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    42.722] (II) intel(0): EDID vendor "APP", prod id 40119
[    42.722] (II) intel(0): Printing DDC gathered Modelines:
[    42.722] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    43.177] (II) intel(0): EDID vendor "APP", prod id 40119
[    43.177] (II) intel(0): Printing DDC gathered Modelines:
[    43.177] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    44.286] (II) XKB: reuse xkmfile /var/lib/xkb/server-53628FFEAE787BDF7F5128B07068E2A1D9DEC814.xkm
[    65.848] (II) intel(0): EDID vendor "APP", prod id 40119
[    65.848] (II) intel(0): Printing DDC gathered Modelines:
[    65.848] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
```

---

### Post by philcolbourn on 2013-04-21
Lid close put MBP to sleep and display turned off.
Lid open woke it up and screen turned on. All good.

This site was helpful [http://www.backtrack-linux.org/forums/showthread.php?t=48904]("http://www.backtrack-linux.org/forums/showthread.php?t=48904")

But in my case I ran ```
update-grub
``` and ```
update-initramfs -u -k all
```

---

### Post by philcolbourn on 2013-04-21
OK. I got 11W!!!

This page explains why I had no vgaswitcheroo:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

I needed to load nouveau (enen though I don't want to use it.

```
modprobe nouveau modeset=1
```

The I got my ```
/sys/kernel/debug/vgaswitcheroo/switch
```

```
cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio:+:Pwr:0000:01:00.1
2:DIS: :Pwr:0000:01:00.0
```

I killed my ethernet card to give me lower energy consumption

```
rmmod tg3
```

I tried to turn off Nvidia card:

```
echo off > /sys/kernel/debug/vgaswitcheroo/switch
root@rex:/home/phil# cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio:+:Pwr:0000:01:00.1
2:DIS: :Pwr:0000:01:00.0
```

That didn't work - DIS still indicates Pwr so it is still powered up.

I tried UPPERCASE:

```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch 
root@rex:/home/phil# cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio:+:Off:0000:01:00.1
2:DIS: :Off:0000:01:00.0
```

That got it!

So, I have Intel being used, Nvidia powered off, and currently (with 2 terminals, Synaptic, and Chrome running with 22-ish tabs opened) 10.1W.

I'm pretty happy about that. I'll post a screenshot if I can.

[http://philatwarrimoo.blogspot.com.au/2013/04/10w-for-macbook-pro-91-mid-2012-non.html]("http://philatwarrimoo.blogspot.com.au/2013/04/10w-for-macbook-pro-91-mid-2012-non.html")

Current kernel options are:

```
 cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.7.5-030705-generic root=UUID=c5fdc871-7c20-4563-bf3b-8f42f36e21b2 ro splash modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1 i915.i915_enable_rc6=3 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force vt.handoff=7
```

Can I improve this set of options to either get more power saving or to make it shorter?

My current kernel is ```
uname -a
Linux rex 3.7.5-030705-generic #201301280206 SMP Mon Jan 28 07:07:29 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I almost forget...

To get rid of some Xorg errors about AIGLX I installed a few packages
```
Installed the following packages:
libdrm-nouveau2 (2.4.43-0ubuntu1)
libegl1-mesa (9.1.1-0ubuntu3)
libgbm1 (9.1.1-0ubuntu3)
libgl1-mesa-dri (9.1.1-0ubuntu3)
libgl1-mesa-dri-experimental (9.1.1-0ubuntu3)
libva-glx1 (1.0.15-4build1)

```

I get no (EE) errors in Xorg now.

---

### Post by philcolbourn on 2013-04-21
Xorg log
```
[    24.425] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    24.425] X Protocol Version 11, Revision 0
[    24.425] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    24.425] Current Operating System: Linux rex 3.7.5-030705-generic #201301280206 SMP Mon Jan 28 07:07:29 UTC 2013 x86_64
[    24.425] Kernel command line: BOOT_IMAGE=/vmlinuz-3.7.5-030705-generic root=UUID=c5fdc871-7c20-4563-bf3b-8f42f36e21b2 ro splash modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1 i915.i915_enable_rc6=3 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force vt.handoff=7
[    24.425] Build Date: 17 April 2013  10:43:13PM
[    24.425] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    24.425] Current version of pixman: 0.28.2
[    24.425] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.425] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.425] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 21 20:15:51 2013
[    24.456] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.456] (==) No Layout section.  Using the first Screen section.
[    24.456] (==) No screen section available. Using defaults.
[    24.456] (**) |-->Screen "Default Screen Section" (0)
[    24.456] (**) |   |-->Monitor "<default monitor>"
[    24.456] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.456] (==) Automatically adding devices
[    24.456] (==) Automatically enabling devices
[    24.456] (==) Automatically adding GPU devices
[    24.456] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.456] 	Entry deleted from font path.
[    24.456] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.456] 	Entry deleted from font path.
[    24.456] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    24.457] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.457] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.457] (II) Loader magic: 0x7f1e7a52dd20
[    24.457] (II) Module ABI versions:
[    24.457] 	X.Org ANSI C Emulation: 0.4
[    24.457] 	X.Org Video Driver: 13.1
[    24.457] 	X.Org XInput driver : 18.0
[    24.457] 	X.Org Server Extension : 7.0
[    24.457] (II) config/udev: Adding drm device (/dev/dri/card0)
[    24.458] (--) PCI:*(0:0:2:0) 8086:0166:106b:00fb rev 9, Mem @ 0xc1400000/4194304, 0xb0000000/268435456, I/O @ 0x00003000/64
[    24.458] (--) PCI: (0:1:0:0) 10de:0fd5:106b:00fc rev 161, Mem @ 0xc0000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    24.458] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.458] Initializing built-in extension Generic Event Extension
[    24.458] Initializing built-in extension SHAPE
[    24.458] Initializing built-in extension MIT-SHM
[    24.458] Initializing built-in extension XInputExtension
[    24.458] Initializing built-in extension XTEST
[    24.458] Initializing built-in extension BIG-REQUESTS
[    24.458] Initializing built-in extension SYNC
[    24.458] Initializing built-in extension XKEYBOARD
[    24.458] Initializing built-in extension XC-MISC
[    24.458] Initializing built-in extension SECURITY
[    24.458] Initializing built-in extension XINERAMA
[    24.458] Initializing built-in extension XFIXES
[    24.458] Initializing built-in extension RENDER
[    24.458] Initializing built-in extension RANDR
[    24.458] Initializing built-in extension COMPOSITE
[    24.458] Initializing built-in extension DAMAGE
[    24.458] Initializing built-in extension MIT-SCREEN-SAVER
[    24.458] Initializing built-in extension DOUBLE-BUFFER
[    24.458] Initializing built-in extension RECORD
[    24.458] Initializing built-in extension DPMS
[    24.458] Initializing built-in extension X-Resource
[    24.458] Initializing built-in extension XVideo
[    24.458] Initializing built-in extension XVideo-MotionCompensation
[    24.458] Initializing built-in extension SELinux
[    24.458] Initializing built-in extension XFree86-VidModeExtension
[    24.458] Initializing built-in extension XFree86-DGA
[    24.458] Initializing built-in extension XFree86-DRI
[    24.458] Initializing built-in extension DRI2
[    24.458] (II) LoadModule: "glx"
[    24.486] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.486] (II) Module glx: vendor="X.Org Foundation"
[    24.486] 	compiled for 1.13.3, module version = 1.0.0
[    24.486] 	ABI class: X.Org Server Extension, version 7.0
[    24.486] (==) AIGLX enabled
[    24.486] Loading extension GLX
[    24.486] (==) Matched intel as autoconfigured driver 0
[    24.486] (==) Matched intel as autoconfigured driver 1
[    24.486] (==) Matched vesa as autoconfigured driver 2
[    24.486] (==) Matched modesetting as autoconfigured driver 3
[    24.486] (==) Matched fbdev as autoconfigured driver 4
[    24.486] (==) Assigned the driver to the xf86ConfigLayout
[    24.486] (II) LoadModule: "intel"
[    24.486] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.577] (II) Module intel: vendor="X.Org Foundation"
[    24.577] 	compiled for 1.13.2.902, module version = 2.21.6
[    24.577] 	Module class: X.Org Video Driver
[    24.577] 	ABI class: X.Org Video Driver, version 13.1
[    24.577] (II) LoadModule: "vesa"
[    24.577] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.577] (II) Module vesa: vendor="X.Org Foundation"
[    24.578] 	compiled for 1.13.0, module version = 2.3.2
[    24.578] 	Module class: X.Org Video Driver
[    24.578] 	ABI class: X.Org Video Driver, version 13.0
[    24.578] (II) LoadModule: "modesetting"
[    24.578] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.578] (II) Module modesetting: vendor="X.Org Foundation"
[    24.578] 	compiled for 1.13.3, module version = 0.7.0
[    24.578] 	Module class: X.Org Video Driver
[    24.578] 	ABI class: X.Org Video Driver, version 13.1
[    24.578] (II) LoadModule: "fbdev"
[    24.578] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.578] (II) Module fbdev: vendor="X.Org Foundation"
[    24.578] 	compiled for 1.12.99.903, module version = 0.4.3
[    24.578] 	Module class: X.Org Video Driver
[    24.578] 	ABI class: X.Org Video Driver, version 13.0
[    24.578] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    24.578] (II) VESA: driver for VESA chipsets: vesa
[    24.578] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.578] (II) FBDEV: driver for framebuffer: fbdev
[    24.578] (++) using VT number 7

[    24.581] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6+git20130416.ddd3cc4e-0ubuntu0sarvatt~quantal (Robert Hooker <sarvatt@ubuntu.com>)
[    24.581] (WW) Falling back to old probe method for vesa
[    24.581] (WW) Falling back to old probe method for modesetting
[    24.581] (WW) Falling back to old probe method for fbdev
[    24.581] (II) Loading sub module "fbdevhw"
[    24.581] (II) LoadModule: "fbdevhw"
[    24.581] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.581] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.581] 	compiled for 1.13.3, module version = 0.0.2
[    24.581] 	ABI class: X.Org Video Driver, version 13.1
[    24.581] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.581] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.581] (==) intel(0): RGB weight 888
[    24.581] (==) intel(0): Default visual is TrueColor
[    24.581] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    24.582] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    24.582] (**) intel(0): Framebuffer tiled
[    24.582] (**) intel(0): Pixmaps tiled
[    24.582] (**) intel(0): "Tear free" disabled
[    24.582] (**) intel(0): Forcing per-crtc-pixmaps? no
[    24.582] (II) intel(0): Output LVDS1 has no monitor section
[    24.582] (--) intel(0): found backlight control interface gmux_backlight (type 'platform')
[    24.612] (II) intel(0): Output VGA1 has no monitor section
[    24.612] (II) intel(0): EDID for output LVDS1
[    24.612] (II) intel(0): Manufacturer: APP  Model: 9cb7  Serial#: 0
[    24.612] (II) intel(0): Year: 2009  Week: 22
[    24.612] (II) intel(0): EDID Version: 1.3
[    24.612] (II) intel(0): Digital Display Input
[    24.612] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    24.612] (II) intel(0): Gamma: 2.20
[    24.612] (II) intel(0): No DPMS capabilities specified
[    24.612] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.612] (II) intel(0): First detailed timing is preferred mode
[    24.612] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.310 greenY: 0.610
[    24.612] (II) intel(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    24.612] (II) intel(0): Manufacturer's mask: 0
[    24.612] (II) intel(0): Supported detailed timing:
[    24.612] (II) intel(0): clock: 119.0 MHz   Image Size:  331 x 207 mm
[    24.612] (II) intel(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    24.612] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    24.612] (II) intel(0): Unknown vendor-specific block 1
[    24.612] (II) intel(0):  LTN154MT07
[    24.612] (II) intel(0): Monitor name: Color LCD
[    24.612] (II) intel(0): EDID (in hex):
[    24.612] (II) intel(0): 	00ffffffffffff000610b79c00000000
[    24.612] (II) intel(0): 	16130103802115780ae585a3544f9c26
[    24.612] (II) intel(0): 	0e505400000001010101010101010101
[    24.612] (II) intel(0): 	0101010101017c2e90a0601a1e403020
[    24.612] (II) intel(0): 	36004bcf100000190000000100061030
[    24.612] (II) intel(0): 	00000000000000000a20000000fe004c
[    24.612] (II) intel(0): 	544e3135344d543037000a20000000fc
[    24.612] (II) intel(0): 	00436f6c6f72204c43440a2020200008
[    24.612] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.612] (II) intel(0): Printing probed modes for output LVDS1
[    24.612] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    24.612] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    24.612] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    24.612] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    24.612] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    24.612] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    24.612] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    24.612] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    24.612] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    24.612] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    24.612] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    24.612] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    24.612] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    24.644] (II) intel(0): EDID for output VGA1
[    24.644] (II) intel(0): Output LVDS1 connected
[    24.644] (II) intel(0): Output VGA1 disconnected
[    24.644] (II) intel(0): Using exact sizes for initial modes
[    24.644] (II) intel(0): Output LVDS1 using initial mode 1680x1050
[    24.644] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.644] (==) intel(0): DPI set to (96, 96)
[    24.644] (II) Loading sub module "dri2"
[    24.644] (II) LoadModule: "dri2"
[    24.644] (II) Module "dri2" already built-in
[    24.644] (II) UnloadModule: "vesa"
[    24.644] (II) Unloading vesa
[    24.644] (II) UnloadModule: "modesetting"
[    24.644] (II) Unloading modesetting
[    24.644] (II) UnloadModule: "fbdev"
[    24.644] (II) Unloading fbdev
[    24.644] (II) UnloadSubModule: "fbdevhw"
[    24.644] (II) Unloading fbdevhw
[    24.644] (==) Depth 24 pixmap format is 32 bpp
[    24.735] (II) intel(0): SNA initialized with IvyBridge backend
[    24.735] (==) intel(0): Backing store disabled
[    24.735] (==) intel(0): Silken mouse enabled
[    24.735] (II) intel(0): HW Cursor enabled
[    24.735] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.735] (==) intel(0): DPMS enabled
[    24.735] (II) intel(0): [DRI2] Setup complete
[    24.735] (II) intel(0): [DRI2]   DRI driver: i965
[    24.735] (II) intel(0): direct rendering: DRI2 Enabled
[    24.735] (==) intel(0): hotplug detection: "enabled"
[    24.735] (--) RandR disabled
[    24.739] (II) SELinux: Disabled on system
[    26.269] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.269] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.269] (II) AIGLX: enabled GLX_ARB_create_context
[    26.269] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    26.269] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    26.269] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.269] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.269] (II) AIGLX: Loaded and initialized i965
[    26.269] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.269] (II) intel(0): switch to mode 1680x1050 on crtc 3 (pipe 0)
[    26.308] (II) intel(0): Setting screen physical size to 444 x 277
[    26.430] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.431] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.431] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.431] (II) LoadModule: "evdev"
[    26.432] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.483] (II) Module evdev: vendor="X.Org Foundation"
[    26.483] 	compiled for 1.13.3, module version = 2.7.3
[    26.483] 	Module class: X.Org XInput Driver
[    26.483] 	ABI class: X.Org XInput driver, version 18.0
[    26.483] (II) Using input driver 'evdev' for 'Power Button'
[    26.483] (**) Power Button: always reports core events
[    26.483] (**) evdev: Power Button: Device: "/dev/input/event3"
[    26.483] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.483] (--) evdev: Power Button: Found keys
[    26.483] (II) evdev: Power Button: Configuring as keyboard
[    26.483] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    26.483] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.483] (**) Option "xkb_rules" "evdev"
[    26.483] (**) Option "xkb_model" "pc105"
[    26.483] (**) Option "xkb_layout" "us"
[    26.484] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    26.484] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.484] (II) Using input driver 'evdev' for 'Video Bus'
[    26.484] (**) Video Bus: always reports core events
[    26.484] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    26.484] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.484] (--) evdev: Video Bus: Found keys
[    26.484] (II) evdev: Video Bus: Configuring as keyboard
[    26.484] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input11/event11"
[    26.484] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    26.484] (**) Option "xkb_rules" "evdev"
[    26.484] (**) Option "xkb_model" "pc105"
[    26.484] (**) Option "xkb_layout" "us"
[    26.484] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    26.484] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.484] (II) Using input driver 'evdev' for 'Video Bus'
[    26.484] (**) Video Bus: always reports core events
[    26.484] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    26.484] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.484] (--) evdev: Video Bus: Found keys
[    26.484] (II) evdev: Video Bus: Configuring as keyboard
[    26.484] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input10/event10"
[    26.484] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    26.484] (**) Option "xkb_rules" "evdev"
[    26.484] (**) Option "xkb_model" "pc105"
[    26.484] (**) Option "xkb_layout" "us"
[    26.484] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.485] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.485] (II) Using input driver 'evdev' for 'Power Button'
[    26.485] (**) Power Button: always reports core events
[    26.485] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.485] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.485] (--) evdev: Power Button: Found keys
[    26.485] (II) evdev: Power Button: Configuring as keyboard
[    26.485] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    26.485] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    26.485] (**) Option "xkb_rules" "evdev"
[    26.485] (**) Option "xkb_model" "pc105"
[    26.485] (**) Option "xkb_layout" "us"
[    26.485] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.485] (II) No input driver specified, ignoring this device.
[    26.485] (II) This device may have been added with another device file.
[    26.485] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.485] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.485] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.485] (**) Sleep Button: always reports core events
[    26.485] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    26.485] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    26.485] (--) evdev: Sleep Button: Found keys
[    26.485] (II) evdev: Sleep Button: Configuring as keyboard
[    26.485] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    26.485] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    26.485] (**) Option "xkb_rules" "evdev"
[    26.485] (**) Option "xkb_model" "pc105"
[    26.485] (**) Option "xkb_layout" "us"
[    26.485] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[    26.485] (II) No input driver specified, ignoring this device.
[    26.485] (II) This device may have been added with another device file.
[    26.485] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[    26.485] (II) No input driver specified, ignoring this device.
[    26.485] (II) This device may have been added with another device file.
[    26.486] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    26.486] (II) No input driver specified, ignoring this device.
[    26.486] (II) This device may have been added with another device file.
[    26.486] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    26.486] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    26.486] (II) config/udev: Adding input device FaceTime HD Camera (Built-in) (/dev/input/event9)
[    26.486] (**) FaceTime HD Camera (Built-in): Applying InputClass "evdev keyboard catchall"
[    26.486] (II) Using input driver 'evdev' for 'FaceTime HD Camera (Built-in)'
[    26.486] (**) FaceTime HD Camera (Built-in): always reports core events
[    26.486] (**) evdev: FaceTime HD Camera (Built-in): Device: "/dev/input/event9"
[    26.486] (--) evdev: FaceTime HD Camera (Built-in): Vendor 0x5ac Product 0x8509
[    26.486] (--) evdev: FaceTime HD Camera (Built-in): Found keys
[    26.486] (II) evdev: FaceTime HD Camera (Built-in): Configuring as keyboard
[    26.486] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input9/event9"
[    26.486] (II) XINPUT: Adding extended input device "FaceTime HD Camera (Built-in)" (type: KEYBOARD, id 11)
[    26.486] (**) Option "xkb_rules" "evdev"
[    26.486] (**) Option "xkb_model" "pc105"
[    26.486] (**) Option "xkb_layout" "us"
[    26.486] (II) config/udev: Adding input device HDA Intel PCH SPDIF In (/dev/input/event12)
[    26.486] (II) No input driver specified, ignoring this device.
[    26.486] (II) This device may have been added with another device file.
[    26.486] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event13)
[    26.486] (II) No input driver specified, ignoring this device.
[    26.486] (II) This device may have been added with another device file.
[    26.486] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event14)
[    26.486] (II) No input driver specified, ignoring this device.
[    26.486] (II) This device may have been added with another device file.
[    26.487] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event4)
[    26.487] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[    26.487] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    26.487] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    26.487] (**) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event4"
[    26.487] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Vendor 0x5ac Product 0x252
[    26.487] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Found keys
[    26.487] (II) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[    26.487] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.3/2-1.8.3:1.0/input/input4/event4"
[    26.487] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD, id 12)
[    26.487] (**) Option "xkb_rules" "evdev"
[    26.487] (**) Option "xkb_model" "pc105"
[    26.487] (**) Option "xkb_layout" "us"
[    26.487] (II) config/udev: Adding input device bcm5974 (/dev/input/event8)
[    26.487] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[    26.487] (**) bcm5974: Applying InputClass "touchpad catchall"
[    26.487] (**) bcm5974: Applying InputClass "Default clickpad buttons"
[    26.487] (**) bcm5974: Applying InputClass "Disable clickpad buttons on Apple touchpads"
[    26.487] (II) LoadModule: "synaptics"
[    26.487] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.487] (II) Module synaptics: vendor="X.Org Foundation"
[    26.487] 	compiled for 1.13.1.901, module version = 1.6.99
[    26.487] 	Module class: X.Org XInput Driver
[    26.487] 	ABI class: X.Org XInput driver, version 18.0
[    26.487] (II) Using input driver 'synaptics' for 'bcm5974'
[    26.487] (**) bcm5974: always reports core events
[    26.487] (**) Option "Device" "/dev/input/event8"
[    26.552] (II) synaptics: bcm5974: found clickpad property
[    26.552] (--) synaptics: bcm5974: x-axis range -4750 - 5280
[    26.553] (--) synaptics: bcm5974: y-axis range -150 - 6730
[    26.553] (--) synaptics: bcm5974: pressure range 0 - 256
[    26.553] (--) synaptics: bcm5974: finger width range 0 - 16
[    26.553] (--) synaptics: bcm5974: buttons: left double triple
[    26.553] (--) synaptics: bcm5974: Vendor 0x5ac Product 0x252
[    26.553] (**) Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
[    26.553] (--) synaptics: bcm5974: touchpad found
[    26.553] (**) bcm5974: always reports core events
[    26.566] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.3/2-1.8.3:1.2/input/input8/event8"
[    26.566] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD, id 13)
[    26.566] (**) synaptics: bcm5974: (accel) MinSpeed is now constant deceleration 2.5
[    26.566] (**) synaptics: bcm5974: (accel) MaxSpeed is now 1.75
[    26.566] (**) synaptics: bcm5974: (accel) AccelFactor is now 0.016
[    26.566] (**) bcm5974: (accel) keeping acceleration scheme 1
[    26.566] (**) bcm5974: (accel) acceleration profile 1
[    26.567] (**) bcm5974: (accel) acceleration factor: 2.000
[    26.567] (**) bcm5974: (accel) acceleration threshold: 4
[    26.567] (--) synaptics: bcm5974: touchpad found
[    26.568] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
[    26.568] (**) bcm5974: Ignoring device from InputClass "touchpad ignore duplicates"
[    26.568] (II) config/udev: Adding input device applesmc (/dev/input/event7)
[    26.568] (II) No input driver specified, ignoring this device.
[    26.568] (II) This device may have been added with another device file.
[    30.495] (II) intel(0): EDID vendor "APP", prod id 40119
[    30.495] (II) intel(0): Printing DDC gathered Modelines:
[    30.495] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[    31.638] (II) intel(0): EDID vendor "APP", prod id 40119
[    31.638] (II) intel(0): Printing DDC gathered Modelines:
[    31.638] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[   105.589] (II) intel(0): EDID vendor "APP", prod id 40119
[   105.589] (II) intel(0): Printing DDC gathered Modelines:
[   105.589] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[   106.047] (II) intel(0): EDID vendor "APP", prod id 40119
[   106.047] (II) intel(0): Printing DDC gathered Modelines:
[   106.047] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[   108.236] (II) XKB: reuse xkmfile /var/lib/xkb/server-53628FFEAE787BDF7F5128B07068E2A1D9DEC814.xkm
[   130.302] (II) intel(0): EDID vendor "APP", prod id 40119
[   130.302] (II) intel(0): Printing DDC gathered Modelines:
[   130.302] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync -vsync (64.7 kHz eP)
[  1030.765] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[  1030.765] (II) config/udev: Adding drm device (/dev/dri/card1)
[  1030.765] (II) LoadModule: "modesetting"
[  1030.766] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1030.766] (II) Module modesetting: vendor="X.Org Foundation"
[  1030.766] 	compiled for 1.13.3, module version = 0.7.0
[  1030.766] 	Module class: X.Org Video Driver
[  1030.766] 	ABI class: X.Org Video Driver, version 13.1
[  1031.488] (II) modesetting(G0): using drv /dev/dri/card1
[  1031.559] (==) modesetting(G0): Depth 24, (==) framebuffer bpp 32
[  1031.559] (==) modesetting(G0): RGB weight 888
[  1031.559] (==) modesetting(G0): Default visual is TrueColor
[  1031.559] (II) modesetting(G0): ShadowFB: preferred YES, enabled YES
[  1031.562] (II) modesetting(G0): Output LVDS-1 has no monitor section
[  1031.688] (II) modesetting(G0): Output DisplayPort-0 has no monitor section
[  1031.944] (II) modesetting(G0): Output DisplayPort-1 has no monitor section
[  1032.137] (II) modesetting(G0): Output DisplayPort-2 has no monitor section
[  1032.520] (II) modesetting(G0): Output LVDS-1 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-0 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-1 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-2 disconnected
[  1032.520] (WW) modesetting(G0): No outputs definitely connected, trying again...
[  1032.520] (II) modesetting(G0): Output LVDS-1 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-0 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-1 disconnected
[  1032.520] (II) modesetting(G0): Output DisplayPort-2 disconnected
[  1032.520] (WW) modesetting(G0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[  1032.520] (II) modesetting(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1032.520] (**) modesetting(G0): Display dimensions: (330, 210) mm
[  1032.520] (**) modesetting(G0): DPI set to (78, 92)
[  1032.520] (II) Loading sub module "fb"
[  1032.520] (II) LoadModule: "fb"
[  1032.534] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1032.535] (II) Module fb: vendor="X.Org Foundation"
[  1032.535] 	compiled for 1.13.3, module version = 1.0.0
[  1032.535] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1032.535] (II) Loading sub module "shadow"
[  1032.535] (II) LoadModule: "shadow"
[  1032.535] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  1032.535] (II) Module shadow: vendor="X.Org Foundation"
[  1032.535] 	compiled for 1.13.3, module version = 1.1.0
[  1032.535] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1032.543] (==) modesetting(G0): Backing store disabled
[  1032.543] (==) modesetting(G0): Silken mouse enabled
[  1032.543] (II) modesetting(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1032.713] (==) modesetting(G0): DPMS enabled
[  1032.713] (II) modesetting(G0): Damage tracking initialized
[  1032.713] xf86: found device 2
[  1032.714] reporting 7 6 13 105
[  1032.714] reporting 7 6 13 105
[  1032.714] reporting 7 6 13 105
[  1032.714] reporting 7 6 13 105
[  1032.714] reporting 7 6 13 105
[  1032.714] reporting 7 6 13 105
[  1032.715] reporting 7 6 13 105
[  1032.715] reporting 7 6 13 105
[  1032.715] reporting 7 6 13 105
[  1032.715] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.716] reporting 7 6 13 105
[  1032.722] reporting 7 6 13 105
[  1032.722] reporting 7 6 13 105
[  1032.722] reporting 7 6 13 105
[  1032.727] reporting 7 6 13 105
[  1032.727] reporting 7 6 13 105
[  1032.728] reporting 7 6 13 105
[  1032.728] reporting 7 6 13 105
[  1032.729] reporting 7 6 13 105
[  1032.729] reporting 7 6 13 105
[  1032.729] reporting 7 6 13 105
[  1032.729] reporting 7 6 13 105
[  1032.729] reporting 7 6 13 105
[  1032.730] reporting 7 6 13 105
[  1032.730] reporting 7 6 13 105
[  1032.730] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.731] reporting 7 6 13 105
[  1032.732] reporting 7 6 13 105
[  1032.734] reporting 7 6 13 105
[  1032.734] reporting 7 6 13 105
[  1032.735] reporting 7 6 13 105
[  1032.735] reporting 7 6 13 105
[  1086.394] reporting 7 6 13 105
[  1090.103] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.650] reporting 7 6 13 105
[  1804.651] reporting 7 6 13 105
[  1804.652] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.653] reporting 7 6 13 105
[  1804.655] reporting 7 6 13 105
[  1804.681] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.058] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.060] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.061] reporting 7 6 13 105
[  1805.063] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.578] reporting 7 6 13 105
[  1805.579] reporting 7 6 13 105
[  1805.579] reporting 7 6 13 105
[  1805.580] reporting 7 6 13 105
[  1805.580] reporting 7 6 13 105
[  1805.580] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.581] reporting 7 6 13 105
[  1805.586] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.825] reporting 7 6 13 105
[  1908.827] reporting 7 6 13 105
[  1908.827] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.828] reporting 7 6 13 105
[  1908.833] reporting 7 6 13 105
[  2109.714] reporting 7 6 13 105
[  2268.748] reporting 7 6 13 105
[  2276.726] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.727] reporting 7 6 13 105
[  2276.729] reporting 7 6 13 105
[  2276.729] reporting 7 6 13 105
[  2276.729] reporting 7 6 13 105
[  2276.729] reporting 7 6 13 105
[  2276.730] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.731] reporting 7 6 13 105
[  2276.734] reporting 7 6 13 105
[  2448.252] reporting 7 6 13 105
```

---

### Post by philcolbourn on 2013-04-24
A few days on...

Suspend works fine (although it seems to take longer each time. gEdit also seems to be misbehaving so perhaps related)

USB device: Apple Internal Keyboard / Trackpad (Apple Inc.) varies between 4 and 8W! I'd like to reduce this.

I 'turned off' IR Receiver which uses about 1W

I wrote a cron-task to autosuspend USB and PCI devices - try powertop -html and open resulting file in a browser to get recommendations.

Fan's sit at 2000 RPM even with my more aggressive macfanctl settings

```
temp_avg_floor: 41
temp_avg_ceiling: 54

temp_TC0P_floor: 37
temp_TC0P_ceiling: 50

temp_TG0P_floor: 37
temp_TG0P_ceiling: 50

exclude: 1 2 3 4 20 21 22 23 24 28 29 30

```

PowerTop gives me some huge figures for Chrome. eg. 125W. This can not be right.

Currently running 14W with USB tethering and charging a Nexus S.

---

