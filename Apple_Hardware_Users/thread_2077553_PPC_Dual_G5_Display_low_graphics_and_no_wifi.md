---
title: "PPC Dual G5 Display low graphics and no wifi"
date: 2012-10-28
forum: Apple Hardware Users
---

### Post by twistydoerofthings on 2012-10-28
Decided to install Ubuntu PowerPC 12.04 on my PowerMac G5 in which I have the nVidia 6800 GT DDL 256 MB Card for the Apple 30" Cinematic display. Am dual booted and Mac OS 10.4 runs swell.

Issue 1: Launching from boot with 'Linux nomodeset' is the only way I can get X to load without going to white/gray screen. It loads a depth of 8 colors and is almost unusable. After digging and digging and digging, I have found no articles that match my config, yet many that are close.

Here is my current xorg.conf:
```
Section "Device"
	Identifier "nVidia GeForce 6800 GT DDL"
	BusID	"PCI:240:16:0"
	#Driver "nouveau"
	Driver "nv"
EndSection

Section "Monitor"
	Identifier "Cinema HD"
	HorizSync 30-81
	VertRefresh 56-75
	Modeline "2560x1600_60.00" 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync
	Modeline "1280x800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync
	Option "Preferred Mode" "2560x1600_60.00"
EndSection

Section "Screen"	
	Identifier	"Default Screen"
	Monitor		"Cinema HD"
	Device		"nVidia GeForce 6800 GT DDL"
		DefaultDepth 32
			SubSection "Display"
				Depth 32
				Modes "2560x1600_60.00"
			EndSubSection
EndSection
```

Here is the Xord.0.log:

```
[    20.725] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    20.725] X Protocol Version 11, Revision 0
[    20.725] Build Operating System: Linux 2.6.42-29-powerpc64-smp ppc Ubuntu
[    20.725] Current Operating System: Linux ubuntuG5 3.2.0-23-powerpc64-smp #36-Ubuntu SMP Tue Apr 10 23:12:42 UTC 2012 ppc64
[    20.725] Kernel command line: root=UUID=42b48573-14b9-48ac-b919-b869c06bece8 ro nosplash nomodeset
[    20.726] Build Date: 29 August 2012  12:15:07AM
[    20.726] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    20.726] Current version of pixman: 0.24.4
[    20.726] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.726] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.726] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 28 17:34:45 2012
[    20.726] (==) Using config file: "/etc/X11/xorg.conf"
[    20.726] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.727] (==) No Layout section.  Using the first Screen section.
[    20.727] (**) |-->Screen "Default Screen" (0)
[    20.727] (**) |   |-->Monitor "Cinema HD"
[    20.728] (**) |   |-->Device "nVidia GeForce 6800 GT DDL"
[    20.728] (==) Automatically adding devices
[    20.728] (==) Automatically enabling devices
[    20.728] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.728] 	Entry deleted from font path.
[    20.728] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    20.728] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.728] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.728] (II) Loader magic: 0x2052e57c
[    20.728] (II) Module ABI versions:
[    20.728] 	X.Org ANSI C Emulation: 0.4
[    20.728] 	X.Org Video Driver: 11.0
[    20.728] 	X.Org XInput driver : 16.0
[    20.728] 	X.Org Server Extension : 6.0
[    20.730] (--) PCI:*(0:240:16:0) 10de:0045:10de:0010 rev 161, Mem @ 0x92000000/16777216, 0xa0000000/268435456, 0x91000000/16777216, BIOS @ 0x????????/131072
[    20.730] (II) LoadModule: "extmod"
[    20.757] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.757] (II) Module extmod: vendor="X.Org Foundation"
[    20.757] 	compiled for 1.11.3, module version = 1.0.0
[    20.757] 	Module class: X.Org Server Extension
[    20.757] 	ABI class: X.Org Server Extension, version 6.0
[    20.757] (II) Loading extension MIT-SCREEN-SAVER
[    20.757] (II) Loading extension XFree86-VidModeExtension
[    20.757] (II) Loading extension XFree86-DGA
[    20.757] (II) Loading extension DPMS
[    20.757] (II) Loading extension XVideo
[    20.757] (II) Loading extension XVideo-MotionCompensation
[    20.757] (II) Loading extension X-Resource
[    20.757] (II) LoadModule: "dbe"
[    20.758] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.758] (II) Module dbe: vendor="X.Org Foundation"
[    20.758] 	compiled for 1.11.3, module version = 1.0.0
[    20.758] 	Module class: X.Org Server Extension
[    20.758] 	ABI class: X.Org Server Extension, version 6.0
[    20.758] (II) Loading extension DOUBLE-BUFFER
[    20.759] (II) LoadModule: "glx"
[    20.759] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.759] (II) Module glx: vendor="X.Org Foundation"
[    20.759] 	compiled for 1.11.3, module version = 1.0.0
[    20.759] 	ABI class: X.Org Server Extension, version 6.0
[    20.759] (==) AIGLX enabled
[    20.759] (II) Loading extension GLX
[    20.759] (II) LoadModule: "record"
[    20.760] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.760] (II) Module record: vendor="X.Org Foundation"
[    20.760] 	compiled for 1.11.3, module version = 1.13.0
[    20.760] 	Module class: X.Org Server Extension
[    20.760] 	ABI class: X.Org Server Extension, version 6.0
[    20.760] (II) Loading extension RECORD
[    20.760] (II) LoadModule: "dri"
[    20.761] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.761] (II) Module dri: vendor="X.Org Foundation"
[    20.761] 	compiled for 1.11.3, module version = 1.0.0
[    20.761] 	ABI class: X.Org Server Extension, version 6.0
[    20.761] (II) Loading extension XFree86-DRI
[    20.761] (II) LoadModule: "dri2"
[    20.762] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.762] (II) Module dri2: vendor="X.Org Foundation"
[    20.762] 	compiled for 1.11.3, module version = 1.2.0
[    20.762] 	ABI class: X.Org Server Extension, version 6.0
[    20.762] (II) Loading extension DRI2
[    20.762] (II) LoadModule: "nv"
[    20.771] (WW) Warning, couldn't open module nv
[    20.771] (II) UnloadModule: "nv"
[    20.771] (II) Unloading nv
[    20.771] (EE) Failed to load module "nv" (module does not exist, 0)
[    20.771] (==) Matched nvidia as autoconfigured driver 0
[    20.771] (==) Matched nouveau as autoconfigured driver 1
[    20.771] (==) Matched nv as autoconfigured driver 2
[    20.771] (==) Matched fbdev as autoconfigured driver 3
[    20.771] (==) Assigned the driver to the xf86ConfigLayout
[    20.771] (II) LoadModule: "nvidia"
[    20.772] (WW) Warning, couldn't open module nvidia
[    20.772] (II) UnloadModule: "nvidia"
[    20.772] (II) Unloading nvidia
[    20.772] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    20.772] (II) LoadModule: "nouveau"
[    20.773] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.773] (II) Module nouveau: vendor="X.Org Foundation"
[    20.773] 	compiled for 1.11.3, module version = 0.0.16
[    20.774] 	Module class: X.Org Video Driver
[    20.774] 	ABI class: X.Org Video Driver, version 11.0
[    20.774] (II) LoadModule: "nv"
[    20.774] (WW) Warning, couldn't open module nv
[    20.774] (II) UnloadModule: "nv"
[    20.774] (II) Unloading nv
[    20.774] (EE) Failed to load module "nv" (module does not exist, 0)
[    20.774] (II) LoadModule: "fbdev"
[    20.775] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.775] (II) Module fbdev: vendor="X.Org Foundation"
[    20.775] 	compiled for 1.11.3, module version = 0.4.2
[    20.775] 	ABI class: X.Org Video Driver, version 11.0
[    20.775] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    20.775] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.775] 	RIVA TNT        (NV04)
[    20.775] 	RIVA TNT2       (NV05)
[    20.776] 	GeForce 256     (NV10)
[    20.776] 	GeForce 2       (NV11, NV15)
[    20.776] 	GeForce 4MX     (NV17, NV18)
[    20.776] 	GeForce 3       (NV20)
[    20.776] 	GeForce 4Ti     (NV25, NV28)
[    20.776] 	GeForce FX      (NV3x)
[    20.776] 	GeForce 6       (NV4x)
[    20.776] 	GeForce 7       (G7x)
[    20.776] 	GeForce 8       (G8x)
[    20.776] 	GeForce GTX 200 (NVA0)
[    20.776] 	GeForce GTX 400 (NVC0)
[    20.776] (II) FBDEV: driver for framebuffer: fbdev
[    20.776] (++) using VT number 7

[    20.777] drmOpenDevice: node name is /dev/dri/card0
[    20.786] drmOpenByBusid: Searching for BusID pci:0000:f0:10.0
[    20.786] drmOpenDevice: node name is /dev/dri/card0
[    20.790] drmOpenByBusid: drmOpenMinor returns -1
[    20.790] drmOpenDevice: node name is /dev/dri/card1
[    20.795] drmOpenByBusid: drmOpenMinor returns -1
[    20.795] drmOpenDevice: node name is /dev/dri/card2
[    20.799] drmOpenByBusid: drmOpenMinor returns -1
[    20.799] drmOpenDevice: node name is /dev/dri/card3
[    20.805] drmOpenByBusid: drmOpenMinor returns -1
[    20.805] drmOpenDevice: node name is /dev/dri/card4
[    20.811] drmOpenByBusid: drmOpenMinor returns -1
[    20.811] drmOpenDevice: node name is /dev/dri/card5
[    20.815] drmOpenByBusid: drmOpenMinor returns -1
[    20.815] drmOpenDevice: node name is /dev/dri/card6
[    20.820] drmOpenByBusid: drmOpenMinor returns -1
[    20.820] drmOpenDevice: node name is /dev/dri/card7
[    20.824] drmOpenByBusid: drmOpenMinor returns -1
[    20.824] drmOpenDevice: node name is /dev/dri/card8
[    20.828] drmOpenByBusid: drmOpenMinor returns -1
[    20.828] drmOpenDevice: node name is /dev/dri/card9
[    20.833] drmOpenByBusid: drmOpenMinor returns -1
[    20.833] drmOpenDevice: node name is /dev/dri/card10
[    20.837] drmOpenByBusid: drmOpenMinor returns -1
[    20.837] drmOpenDevice: node name is /dev/dri/card11
[    20.842] drmOpenByBusid: drmOpenMinor returns -1
[    20.842] drmOpenDevice: node name is /dev/dri/card12
[    20.847] drmOpenByBusid: drmOpenMinor returns -1
[    20.847] drmOpenDevice: node name is /dev/dri/card13
[    20.851] drmOpenByBusid: drmOpenMinor returns -1
[    20.851] drmOpenDevice: node name is /dev/dri/card14
[    20.865] drmOpenByBusid: drmOpenMinor returns -1
[    20.865] drmOpenDevice: node name is /dev/dri/card15
[    20.869] drmOpenByBusid: drmOpenMinor returns -1
[    20.869] drmOpenDevice: node name is /dev/dri/card0
[    20.878] drmOpenDevice: node name is /dev/dri/card0
[    20.882] drmOpenDevice: node name is /dev/dri/card1
[    20.886] drmOpenDevice: node name is /dev/dri/card2
[    20.890] drmOpenDevice: node name is /dev/dri/card3
[    20.894] drmOpenDevice: node name is /dev/dri/card4
[    20.898] drmOpenDevice: node name is /dev/dri/card5
[    20.902] drmOpenDevice: node name is /dev/dri/card6
[    20.906] drmOpenDevice: node name is /dev/dri/card7
[    20.910] drmOpenDevice: node name is /dev/dri/card8
[    20.914] drmOpenDevice: node name is /dev/dri/card9
[    20.918] drmOpenDevice: node name is /dev/dri/card10
[    20.922] drmOpenDevice: node name is /dev/dri/card11
[    20.926] drmOpenDevice: node name is /dev/dri/card12
[    20.930] drmOpenDevice: node name is /dev/dri/card13
[    20.934] drmOpenDevice: node name is /dev/dri/card14
[    20.937] drmOpenDevice: node name is /dev/dri/card15
[    20.942] (EE) [drm] failed to open device
[    20.942] (II) Loading sub module "fbdevhw"
[    20.942] (II) LoadModule: "fbdevhw"
[    20.942] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.942] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.942] 	compiled for 1.11.3, module version = 0.0.2
[    20.943] 	ABI class: X.Org Video Driver, version 11.0
[    20.943] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.943] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.943] (**) FBDEV(0): claimed PCI slot 240@0:16:0
[    20.943] (II) FBDEV(0): using default device
[    20.943] (**) FBDEV(0): Depth 32, (--) framebuffer bpp 32
[    20.943] (EE) FBDEV(0): Weight given (000) is inconsistent with the depth (32)
[    20.943] (II) UnloadModule: "fbdev"
[    20.943] (II) Unloading fbdev
[    20.943] (II) UnloadModule: "fbdevhw"
[    20.943] (II) Unloading fbdevhw
[    20.943] (EE) Screen(s) found, but none have a usable configuration.
[    20.943] 
Fatal server error:
[    20.943] no screens found
[    20.943] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    20.943] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    20.943] 
[    21.014]  ddxSigGiveUp: Closing log
[    21.014] Server terminated with error (1). Closing log file.
```

I have tried almost everything I can find with no real change. Sometimes I get a display that is clean, yet it's like 800x600 and appears twice on the screen telling me X is in Low Graphics mode. When I try to continue in low graphics mode just once, it dumbs me to the command with the same Xorg.0.log errors.

I read one article that suggests that I should rebuild the nv drivers. I followed that, yet could not run 'apt-get source xserver-xorg-video-nv', it reported unable to find source package.

The only thing I have not tried is disabling the second DVI port on the nVidia card. Might try swaping the plug and trying the other plug too. It doesn't make sense that it works as is with 'nomodeset', so I feel like that's not going to improve any thing.

Issue 2: I have the Airport Extreme card in the same machine. Running 'lspci -vvnn | grep 14e4' returns the following details:
```
0001:02:01.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```
Research suggests that I need to load the b43legacy driver for this device. I ran 'apt-get install firmware-b43legacy-installer' It runs properly and then I see errors:
```
[   21.743245] b43-phy0 ERROR: Microcode not responding
[   21.743395] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   21.911277] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   21.963328] b43-pci-bridge 0001:02:01.0: Warning: IOMMU window too big for device mask
[   21.963335] b43-pci-bridge 0001:02:01.0: mask: 0x3fffffff, table end: 0x80000000
[   21.963341] b43-phy0 ERROR: The machine/kernel does not support the required 30-bit DMA mask
[   23.091245] b43-phy0 ERROR: Microcode not responding
[   23.091255] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Sorry if this is a lot of info all in one post. Thanks in advance for any help you might have.

---

### Post by twistydoerofthings on 2012-10-28
Find the attached. This is an example of what I see on the screen. I can now get X to load in this sort of dual display, actuall 1280 x 800 (16:10) shown in the Display settings.

---

### Post by twistydoerofthings on 2012-10-28
Further Xorg.0.log info is starting reveal a total of 4 monitors reported by the card.

```
[   135.197] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   135.197] X Protocol Version 11, Revision 0
[   135.197] Build Operating System: Linux 2.6.42-29-powerpc64-smp ppc Ubuntu
[   135.197] Current Operating System: Linux ubuntuG5 3.2.0-23-powerpc64-smp #36-Ubuntu SMP Tue Apr 10 23:12:42 UTC 2012 ppc64
[   135.197] Kernel command line: root=UUID=42b48573-14b9-48ac-b919-b869c06bece8 ro nosplash 
[   135.197] Build Date: 29 August 2012  12:15:07AM
[   135.197] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[   135.197] Current version of pixman: 0.24.4
[   135.197] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   135.197] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   135.198] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 28 18:59:49 2012
[   135.212] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   135.213] (==) No Layout section.  Using the first Screen section.
[   135.213] (==) No screen section available. Using defaults.
[   135.213] (**) |-->Screen "Default Screen Section" (0)
[   135.213] (**) |   |-->Monitor "<default monitor>"
[   135.214] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   135.214] (==) Automatically adding devices
[   135.214] (==) Automatically enabling devices
[   135.214] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   135.214] 	Entry deleted from font path.
[   135.214] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   135.214] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   135.214] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   135.214] (II) Loader magic: 0x2061a57c
[   135.214] (II) Module ABI versions:
[   135.214] 	X.Org ANSI C Emulation: 0.4
[   135.214] 	X.Org Video Driver: 11.0
[   135.214] 	X.Org XInput driver : 16.0
[   135.214] 	X.Org Server Extension : 6.0
[   135.216] (--) PCI:*(0:240:16:0) 10de:0045:10de:0010 rev 161, Mem @ 0x92000000/16777216, 0xa0000000/268435456, 0x91000000/16777216, BIOS @ 0x????????/131072
[   135.216] (II) LoadModule: "extmod"
[   135.234] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   135.235] (II) Module extmod: vendor="X.Org Foundation"
[   135.235] 	compiled for 1.11.3, module version = 1.0.0
[   135.235] 	Module class: X.Org Server Extension
[   135.235] 	ABI class: X.Org Server Extension, version 6.0
[   135.235] (II) Loading extension MIT-SCREEN-SAVER
[   135.235] (II) Loading extension XFree86-VidModeExtension
[   135.235] (II) Loading extension XFree86-DGA
[   135.235] (II) Loading extension DPMS
[   135.235] (II) Loading extension XVideo
[   135.235] (II) Loading extension XVideo-MotionCompensation
[   135.235] (II) Loading extension X-Resource
[   135.235] (II) LoadModule: "dbe"
[   135.235] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   135.236] (II) Module dbe: vendor="X.Org Foundation"
[   135.236] 	compiled for 1.11.3, module version = 1.0.0
[   135.236] 	Module class: X.Org Server Extension
[   135.236] 	ABI class: X.Org Server Extension, version 6.0
[   135.236] (II) Loading extension DOUBLE-BUFFER
[   135.236] (II) LoadModule: "glx"
[   135.236] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   135.236] (II) Module glx: vendor="X.Org Foundation"
[   135.237] 	compiled for 1.11.3, module version = 1.0.0
[   135.237] 	ABI class: X.Org Server Extension, version 6.0
[   135.237] (==) AIGLX enabled
[   135.237] (II) Loading extension GLX
[   135.237] (II) LoadModule: "record"
[   135.237] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   135.237] (II) Module record: vendor="X.Org Foundation"
[   135.237] 	compiled for 1.11.3, module version = 1.13.0
[   135.237] 	Module class: X.Org Server Extension
[   135.237] 	ABI class: X.Org Server Extension, version 6.0
[   135.237] (II) Loading extension RECORD
[   135.237] (II) LoadModule: "dri"
[   135.238] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   135.238] (II) Module dri: vendor="X.Org Foundation"
[   135.238] 	compiled for 1.11.3, module version = 1.0.0
[   135.238] 	ABI class: X.Org Server Extension, version 6.0
[   135.238] (II) Loading extension XFree86-DRI
[   135.238] (II) LoadModule: "dri2"
[   135.239] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   135.239] (II) Module dri2: vendor="X.Org Foundation"
[   135.239] 	compiled for 1.11.3, module version = 1.2.0
[   135.239] 	ABI class: X.Org Server Extension, version 6.0
[   135.239] (II) Loading extension DRI2
[   135.239] (==) Matched nvidia as autoconfigured driver 0
[   135.239] (==) Matched nouveau as autoconfigured driver 1
[   135.239] (==) Matched nv as autoconfigured driver 2
[   135.239] (==) Matched fbdev as autoconfigured driver 3
[   135.239] (==) Assigned the driver to the xf86ConfigLayout
[   135.239] (II) LoadModule: "nvidia"
[   135.249] (WW) Warning, couldn't open module nvidia
[   135.249] (II) UnloadModule: "nvidia"
[   135.249] (II) Unloading nvidia
[   135.249] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   135.249] (II) LoadModule: "nouveau"
[   135.249] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   135.250] (II) Module nouveau: vendor="X.Org Foundation"
[   135.250] 	compiled for 1.11.3, module version = 0.0.16
[   135.250] 	Module class: X.Org Video Driver
[   135.250] 	ABI class: X.Org Video Driver, version 11.0
[   135.250] (II) LoadModule: "nv"
[   135.251] (WW) Warning, couldn't open module nv
[   135.251] (II) UnloadModule: "nv"
[   135.251] (II) Unloading nv
[   135.251] (EE) Failed to load module "nv" (module does not exist, 0)
[   135.251] (II) LoadModule: "fbdev"
[   135.251] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   135.252] (II) Module fbdev: vendor="X.Org Foundation"
[   135.252] 	compiled for 1.11.3, module version = 0.4.2
[   135.252] 	ABI class: X.Org Video Driver, version 11.0
[   135.252] (==) Matched nvidia as autoconfigured driver 0
[   135.252] (==) Matched nouveau as autoconfigured driver 1
[   135.252] (==) Matched nv as autoconfigured driver 2
[   135.252] (==) Matched fbdev as autoconfigured driver 3
[   135.252] (==) Assigned the driver to the xf86ConfigLayout
[   135.252] (II) LoadModule: "nvidia"
[   135.253] (WW) Warning, couldn't open module nvidia
[   135.253] (II) UnloadModule: "nvidia"
[   135.253] (II) Unloading nvidia
[   135.253] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   135.253] (II) LoadModule: "nouveau"
[   135.253] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   135.253] (II) Module nouveau: vendor="X.Org Foundation"
[   135.253] 	compiled for 1.11.3, module version = 0.0.16
[   135.253] 	Module class: X.Org Video Driver
[   135.253] 	ABI class: X.Org Video Driver, version 11.0
[   135.254] (II) UnloadModule: "nouveau"
[   135.254] (II) Unloading nouveau
[   135.254] (II) Failed to load module "nouveau" (already loaded, 0)
[   135.254] (II) LoadModule: "nv"
[   135.254] (WW) Warning, couldn't open module nv
[   135.254] (II) UnloadModule: "nv"
[   135.254] (II) Unloading nv
[   135.254] (EE) Failed to load module "nv" (module does not exist, 0)
[   135.254] (II) LoadModule: "fbdev"
[   135.255] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   135.255] (II) Module fbdev: vendor="X.Org Foundation"
[   135.255] 	compiled for 1.11.3, module version = 0.4.2
[   135.255] 	ABI class: X.Org Video Driver, version 11.0
[   135.255] (II) UnloadModule: "fbdev"
[   135.255] (II) Unloading fbdev
[   135.255] (II) Failed to load module "fbdev" (already loaded, 0)
[   135.255] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   135.255] (II) NOUVEAU driver for NVIDIA chipset families :
[   135.255] 	RIVA TNT        (NV04)
[   135.255] 	RIVA TNT2       (NV05)
[   135.255] 	GeForce 256     (NV10)
[   135.255] 	GeForce 2       (NV11, NV15)
[   135.255] 	GeForce 4MX     (NV17, NV18)
[   135.255] 	GeForce 3       (NV20)
[   135.256] 	GeForce 4Ti     (NV25, NV28)
[   135.256] 	GeForce FX      (NV3x)
[   135.256] 	GeForce 6       (NV4x)
[   135.256] 	GeForce 7       (G7x)
[   135.256] 	GeForce 8       (G8x)
[   135.256] 	GeForce GTX 200 (NVA0)
[   135.256] 	GeForce GTX 400 (NVC0)
[   135.256] (II) FBDEV: driver for framebuffer: fbdev
[   135.256] (++) using VT number 7

[   135.256] drmOpenDevice: node name is /dev/dri/card0
[   135.257] drmOpenDevice: open result is 6, (OK)
[   135.257] drmOpenByBusid: Searching for BusID pci:0000:f0:10.0
[   135.257] drmOpenDevice: node name is /dev/dri/card0
[   135.257] drmOpenDevice: open result is 6, (OK)
[   135.257] drmOpenByBusid: drmOpenMinor returns 6
[   135.257] drmOpenByBusid: drmGetBusid reports pci:0000:f0:10.0
[   135.257] (II) [drm] nouveau interface version: 0.0.16
[   135.257] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   135.257] (WW) Falling back to old probe method for fbdev
[   135.257] (II) Loading sub module "fbdevhw"
[   135.257] (II) LoadModule: "fbdevhw"
[   135.258] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   135.258] (II) Module fbdevhw: vendor="X.Org Foundation"
[   135.258] 	compiled for 1.11.3, module version = 0.0.2
[   135.258] 	ABI class: X.Org Video Driver, version 11.0
[   135.258] (II) Loading sub module "dri"
[   135.258] (II) LoadModule: "dri"
[   135.258] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   135.258] (II) Module dri: vendor="X.Org Foundation"
[   135.258] 	compiled for 1.11.3, module version = 1.0.0
[   135.258] 	ABI class: X.Org Server Extension, version 6.0
[   135.258] (II) NOUVEAU(0): Loaded DRI module
[   135.259] drmOpenDevice: node name is /dev/dri/card0
[   135.259] drmOpenDevice: open result is 7, (OK)
[   135.259] drmOpenDevice: node name is /dev/dri/card0
[   135.259] drmOpenDevice: open result is 7, (OK)
[   135.259] drmOpenByBusid: Searching for BusID pci:0000:f0:10.0
[   135.259] drmOpenDevice: node name is /dev/dri/card0
[   135.259] drmOpenDevice: open result is 7, (OK)
[   135.259] drmOpenByBusid: drmOpenMinor returns 7
[   135.259] drmOpenByBusid: drmGetBusid reports pci:0000:f0:10.0
[   135.259] (II) [drm] DRM interface version 1.4
[   135.259] (II) [drm] DRM open master succeeded.
[   135.259] (--) NOUVEAU(0): Chipset: "NVIDIA NV40"
[   135.259] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   135.259] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   135.259] (==) NOUVEAU(0): RGB weight 888
[   135.259] (==) NOUVEAU(0): Default visual is TrueColor
[   135.259] (==) NOUVEAU(0): Using HW cursor
[   135.259] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   135.259] (==) NOUVEAU(0): Page flipping enabled
[   135.267] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[   135.292] (II) NOUVEAU(0): Output TV-1 has no monitor section
[   135.496] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[   135.552] (II) NOUVEAU(0): Output TV-2 has no monitor section
[   135.559] (II) NOUVEAU(0): EDID for output DVI-I-1
[   135.560] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[   135.560] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   135.560] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   135.560] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   135.560] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[   135.560] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[   135.588] (II) NOUVEAU(0): EDID for output TV-1
[   135.588] (II) NOUVEAU(0): Printing probed modes for output TV-1
[   135.588] (II) NOUVEAU(0): Modeline "720x576"x50.0   28.66  720 776 856 960  576 576 588 597 -hsync -vsync (29.9 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "1024x768"x50.0   54.16  1024 1064 1200 1344  768 768 777 806 -hsync -vsync (40.3 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "800x600"x50.0   32.14  800 840 920 1040  600 600 604 618 +hsync +vsync (30.9 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "720x480"x50.0   25.20  720 752 872 960  480 480 493 525 -hsync -vsync (26.2 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "640x480"x50.0   23.10  640 672 768 880  480 480 492 525 -hsync -vsync (26.2 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "400x300"x100.0   20.10  400 432 496 640  300 300 303 314 doublescan +hsync +vsync (31.4 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "320x240"x100.0   14.73  320 344 392 560  240 240 246 263 doublescan -hsync -vsync (26.3 kHz)
[   135.588] (II) NOUVEAU(0): Modeline "320x200"x100.0   12.32  320 344 392 560  200 200 202 220 doublescan -hsync -vsync (22.0 kHz)
[   135.878] (II) NOUVEAU(0): EDID for output DVI-I-2
[   135.878] (II) NOUVEAU(0): Manufacturer: APP  Model: 9220  Serial#: 33555274
[   135.878] (II) NOUVEAU(0): Year: 2005  Week: 1
[   135.878] (II) NOUVEAU(0): EDID Version: 1.3
[   135.878] (II) NOUVEAU(0): Digital Display Input
[   135.878] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   135.878] (II) NOUVEAU(0): Gamma: 2.20
[   135.878] (II) NOUVEAU(0): DPMS capabilities: Off
[   135.878] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   135.878] (II) NOUVEAU(0): First detailed timing not preferred mode in violation of standard!
[   135.878] (II) NOUVEAU(0): redX: 0.638 redY: 0.342   greenX: 0.293 greenY: 0.609
[   135.878] (II) NOUVEAU(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[   135.879] (II) NOUVEAU(0): Manufacturer's mask: 0
[   135.879] (II) NOUVEAU(0): Supported detailed timing:
[   135.879] (II) NOUVEAU(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   135.879] (II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   135.879] (II) NOUVEAU(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[   135.879] (II) NOUVEAU(0): Supported detailed timing:
[   135.879] (II) NOUVEAU(0): clock: 268.0 MHz   Image Size:  641 x 401 mm
[   135.879] (II) NOUVEAU(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
[   135.879] (II) NOUVEAU(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
[   135.879] (II) NOUVEAU(0): Monitor name: Cinema HD
[   135.879] (II) NOUVEAU(0): Monitor name: Display
[   135.879] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[   135.879] (II) NOUVEAU(0): EDID (in hex):
[   135.879] (II) NOUVEAU(0): 	00ffffffffffff00061020924a030002
[   135.879] (II) NOUVEAU(0): 	010f0103804028782860e5a3574b9c25
[   135.879] (II) NOUVEAU(0): 	11505400000001010101010101010101
[   135.879] (II) NOUVEAU(0): 	010101010101bc1b00a0502017303020
[   135.879] (II) NOUVEAU(0): 	360081912100001ab06800a0a0402e60
[   135.879] (II) NOUVEAU(0): 	3020360081912100001a000000fc0043
[   135.879] (II) NOUVEAU(0): 	696e656d61204844200a0000000000fc
[   135.879] (II) NOUVEAU(0): 	00446973706c61790a0000000000014d
[   135.879] (II) NOUVEAU(0): Printing probed modes for output DVI-I-2
[   135.879] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   135.932] (II) NOUVEAU(0): EDID for output TV-2
[   135.932] (II) NOUVEAU(0): Output DVI-I-1 connected
[   135.932] (II) NOUVEAU(0): Output TV-1 connected
[   135.932] (II) NOUVEAU(0): Output DVI-I-2 connected
[   135.932] (II) NOUVEAU(0): Output TV-2 disconnected
[   135.932] (II) NOUVEAU(0): Using sloppy heuristic for initial modes
[   135.932] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 800x600
[   135.932] (II) NOUVEAU(0): Output TV-1 using initial mode 720x576
[   135.932] (II) NOUVEAU(0): Output DVI-I-2 using initial mode 1280x800
[   135.932] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   135.932] (--) NOUVEAU(0): Virtual size is 1280x800 (pitch 0)
[   135.932] (**) NOUVEAU(0):  Driver mode "720x576": 28.7 MHz (scaled from 0.0 MHz), 29.9 kHz, 50.0 Hz
[   135.932] (II) NOUVEAU(0): Modeline "720x576"x50.0   28.66  720 776 856 960  576 576 588 597 -hsync -vsync (29.9 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "1024x768": 54.2 MHz (scaled from 0.0 MHz), 40.3 kHz, 50.0 Hz
[   135.932] (II) NOUVEAU(0): Modeline "1024x768"x50.0   54.16  1024 1064 1200 1344  768 768 777 806 -hsync -vsync (40.3 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "800x600": 32.1 MHz (scaled from 0.0 MHz), 30.9 kHz, 50.0 Hz
[   135.932] (II) NOUVEAU(0): Modeline "800x600"x50.0   32.14  800 840 920 1040  600 600 604 618 +hsync +vsync (30.9 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "720x480": 25.2 MHz (scaled from 0.0 MHz), 26.2 kHz, 50.0 Hz
[   135.932] (II) NOUVEAU(0): Modeline "720x480"x50.0   25.20  720 752 872 960  480 480 493 525 -hsync -vsync (26.2 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "640x480": 23.1 MHz (scaled from 0.0 MHz), 26.2 kHz, 50.0 Hz
[   135.932] (II) NOUVEAU(0): Modeline "640x480"x50.0   23.10  640 672 768 880  480 480 492 525 -hsync -vsync (26.2 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "400x300": 20.1 MHz (scaled from 0.0 MHz), 31.4 kHz, 100.0 Hz (D)
[   135.932] (II) NOUVEAU(0): Modeline "400x300"x100.0   20.10  400 432 496 640  300 300 303 314 doublescan +hsync +vsync (31.4 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "320x240": 14.7 MHz (scaled from 0.0 MHz), 26.3 kHz, 100.0 Hz (D)
[   135.932] (II) NOUVEAU(0): Modeline "320x240"x100.0   14.73  320 344 392 560  240 240 246 263 doublescan -hsync -vsync (26.3 kHz)
[   135.932] (**) NOUVEAU(0):  Driver mode "320x200": 12.3 MHz (scaled from 0.0 MHz), 22.0 kHz, 100.0 Hz (D)
[   135.932] (II) NOUVEAU(0): Modeline "320x200"x100.0   12.32  320 344 392 560  200 200 202 220 doublescan -hsync -vsync (22.0 kHz)
[   135.932] (==) NOUVEAU(0): DPI set to (96, 96)
[   135.933] (II) Loading sub module "fb"
[   135.933] (II) LoadModule: "fb"
[   135.933] (II) Loading /usr/lib/xorg/modules/libfb.so
[   135.933] (II) Module fb: vendor="X.Org Foundation"
[   135.933] 	compiled for 1.11.3, module version = 1.0.0
[   135.933] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   135.933] (II) Loading sub module "exa"
[   135.933] (II) LoadModule: "exa"
[   135.934] (II) Loading /usr/lib/xorg/modules/libexa.so
[   135.957] (II) Module exa: vendor="X.Org Foundation"
[   135.957] 	compiled for 1.11.3, module version = 2.5.0
[   135.957] 	ABI class: X.Org Video Driver, version 11.0
[   135.957] (II) Loading sub module "shadowfb"
[   135.957] (II) LoadModule: "shadowfb"
[   135.957] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   135.977] (II) Module shadowfb: vendor="X.Org Foundation"
[   135.977] 	compiled for 1.11.3, module version = 1.0.0
[   135.977] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   135.977] (II) UnloadModule: "fbdev"
[   135.977] (II) Unloading fbdev
[   135.977] (II) UnloadModule: "fbdevhw"
[   135.977] (II) Unloading fbdevhw
[   135.977] (--) Depth 24 pixmap format is 32 bpp
[   135.977] (EE) NOUVEAU(0): Error creating GPU channel: -19
[   135.977] (EE) NOUVEAU(0): Error initialising acceleration.  Falling back to NoAccel
[   135.978] (==) NOUVEAU(0): Backing store disabled
[   135.978] (==) NOUVEAU(0): Silken mouse enabled
[   135.978] (==) NOUVEAU(0): DPMS enabled
[   135.978] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   135.979] (--) RandR disabled
[   135.979] (II) Initializing built-in extension Generic Event Extension
[   135.979] (II) Initializing built-in extension SHAPE
[   135.979] (II) Initializing built-in extension MIT-SHM
[   135.979] (II) Initializing built-in extension XInputExtension
[   135.979] (II) Initializing built-in extension XTEST
[   135.979] (II) Initializing built-in extension BIG-REQUESTS
[   135.979] (II) Initializing built-in extension SYNC
[   135.979] (II) Initializing built-in extension XKEYBOARD
[   135.979] (II) Initializing built-in extension XC-MISC
[   135.979] (II) Initializing built-in extension SECURITY
[   135.979] (II) Initializing built-in extension XINERAMA
[   135.979] (II) Initializing built-in extension XFIXES
[   135.979] (II) Initializing built-in extension RENDER
[   135.979] (II) Initializing built-in extension RANDR
[   135.979] (II) Initializing built-in extension COMPOSITE
[   135.979] (II) Initializing built-in extension DAMAGE
[   136.007] (II) AIGLX: Screen 0 is not DRI2 capable
[   136.007] (II) AIGLX: Screen 0 is not DRI capable
[   136.013] (II) AIGLX: Loaded and initialized swrast
[   136.013] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   136.034] (II) NOUVEAU(0): NVEnterVT is called.
[   136.034] (II) NOUVEAU(0): Setting screen physical size to 338 x 211
[   136.034] resize called 1280 800
[   136.093] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   136.099] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event4)
[   136.099] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[   136.099] (II) LoadModule: "evdev"
[   136.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   136.101] (II) Module evdev: vendor="X.Org Foundation"
[   136.101] 	compiled for 1.11.3, module version = 2.7.0
[   136.101] 	Module class: X.Org XInput Driver
[   136.101] 	ABI class: X.Org XInput driver, version 16.0
[   136.101] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[   136.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   136.101] (**) Dell Dell USB Keyboard Hub: always reports core events
[   136.101] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event4"
[   136.101] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2002
[   136.101] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[   136.101] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[   136.101] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input4/event4"
[   136.101] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 6)
[   136.101] (**) Option "xkb_rules" "evdev"
[   136.101] (**) Option "xkb_model" "pc105"
[   136.101] (**) Option "xkb_layout" "us"
[   136.103] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event5)
[   136.103] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[   136.103] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[   136.103] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   136.103] (**) Dell Dell USB Keyboard Hub: always reports core events
[   136.103] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event5"
[   136.103] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2002
[   136.103] (--) evdev: Dell Dell USB Keyboard Hub: Found absolute axes
[   136.103] (II) evdev: Dell Dell USB Keyboard Hub: Forcing absolute x/y axes to exist.
[   136.103] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[   136.103] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as mouse
[   136.103] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[   136.104] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.1/input/input5/event5"
[   136.104] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 7)
[   136.104] (**) Option "xkb_rules" "evdev"
[   136.104] (**) Option "xkb_model" "pc105"
[   136.104] (**) Option "xkb_layout" "us"
[   136.104] (II) evdev: Dell Dell USB Keyboard Hub: initialized for absolute axes.
[   136.105] (**) Dell Dell USB Keyboard Hub: (accel) keeping acceleration scheme 1
[   136.105] (**) Dell Dell USB Keyboard Hub: (accel) acceleration profile 0
[   136.105] (**) Dell Dell USB Keyboard Hub: (accel) acceleration factor: 2.000
[   136.105] (**) Dell Dell USB Keyboard Hub: (accel) acceleration threshold: 4
[   136.106] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event3)
[   136.106] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[   136.106] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[   136.106] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   136.106] (**) Logitech Optical USB Mouse: always reports core events
[   136.106] (**) evdev: Logitech Optical USB Mouse: Device: "/dev/input/event3"
[   136.106] (--) evdev: Logitech Optical USB Mouse: Vendor 0x46d Product 0xc016
[   136.106] (--) evdev: Logitech Optical USB Mouse: Found 3 mouse buttons
[   136.106] (--) evdev: Logitech Optical USB Mouse: Found scroll wheel(s)
[   136.106] (--) evdev: Logitech Optical USB Mouse: Found relative axes
[   136.106] (--) evdev: Logitech Optical USB Mouse: Found x and y relative axes
[   136.106] (II) evdev: Logitech Optical USB Mouse: Configuring as mouse
[   136.106] (II) evdev: Logitech Optical USB Mouse: Adding scrollwheel support
[   136.106] (**) evdev: Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[   136.106] (**) evdev: Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   136.106] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-1/1-1.2/1-1.2:1.0/input/input3/event3"
[   136.106] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE, id 8)
[   136.106] (II) evdev: Logitech Optical USB Mouse: initialized for relative axes.
[   136.107] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[   136.107] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[   136.107] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[   136.107] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[   136.108] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse1)
[   136.108] (II) No input driver specified, ignoring this device.
[   136.108] (II) This device may have been added with another device file.
[   136.108] (II) config/udev: Adding input device PMU (/dev/input/event0)
[   136.109] (**) PMU: Applying InputClass "evdev keyboard catchall"
[   136.109] (II) Using input driver 'evdev' for 'PMU'
[   136.109] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   136.109] (**) PMU: always reports core events
[   136.109] (**) evdev: PMU: Device: "/dev/input/event0"
[   136.109] (--) evdev: PMU: Vendor 0x1 Product 0x1
[   136.109] (--) evdev: PMU: Found keys
[   136.109] (II) evdev: PMU: Configuring as keyboard
[   136.109] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[   136.109] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD, id 9)
[   136.109] (**) Option "xkb_rules" "evdev"
[   136.109] (**) Option "xkb_model" "pc105"
[   136.109] (**) Option "xkb_layout" "us"
[   157.121] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
```

The finding here reveal DVI-I-1, DVI-I-2, TV-1, and TV-2. Also very interesting how it formulated the unique display settings. This was the result of the settings wizard backing up my xorg.conf and setting it's own.

Will try disabling the additional outputs in Monitors.

---

### Post by twistydoerofthings on 2012-10-29
Disabling the additional outputs has not improved anything. Will tinker with it more tonight.

Anyone have a xorg.conf file for nVidia 6800 & 30" display?

---

