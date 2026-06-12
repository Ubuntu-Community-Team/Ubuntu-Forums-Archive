---
title: "Cannont install ubuntu on OS X Lion"
date: 2011-07-30
forum: Apple Hardware Users
---

### Post by MaxxABillion on 2011-07-30
I am beyond frustrated right now.  I really want to use ubuntu, however,  I can't get it to install at all.  I've tried installing it in VMware,  then I tried to run a dual boot via bootcamp.  The final error it has  come down to was "unable to find a medium containing a live file system"     To clarify, I have a Macbook Pro 15"/2GHz Intel Core i7 / version  10.7 (OS X Lion)  I've tried EVERYTHING!!! Even using redit to boot from  the live CD. I don't even get pass the command screen.  I'm starting to  believe that this is a bug in Ubuntu 11.04 that causing problems with  OS X Lion.  I've researched researched and researched to no avail.

---

### Post by steve11911 on 2011-08-01
Relax...I think you have good chance of getting an Ubuntu install on your hardware.
My first concern is about the error message you're getting.This MAY be due to faulty install media.I would try the disk in another machine, verify the md5 checksum of the .iso file you downloaded and probably burn another one at the lowest possible speed.

This page would be a good place to start:

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Posting the EXACT model number of your MAcbook pro will make the digging for specific issues easier.

---

### Post by bvalkai on 2011-09-28
I have the same problem, the disk works fine on other machines and md5 checksum confirmed the quality of the .iso. Could this be related to the new os Lion? I have the same machine model, btw,

---

### Post by mörgæs on 2011-09-28
I do not have experience with Macs, but on a PC the problem is often solved by booting from USB rather than CD.

---

### Post by eufrat on 2011-09-29
I have same problems with new (lion) macbook pro 8,2.

With bios boot i get  "unable to find a medium containing a live file system" , 
and with efi boot i can boot and install  without X.  Here is Xorg.0.log:
```
[    67.023] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    67.024] X Protocol Version 11, Revision 0
[    67.024] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    67.024] Current Operating System: Linux mah-pook 3.0.0-12-generic #19-Ubuntu SMP Fri Sep 23 21:23:39 UTC 2011 x86_64
[    67.024] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=5929eb72-139f-419e-b0aa-d5a3dc4e658e ro nomodeset video=efib quiet splash vt.handoff=7
[    67.024] Build Date: 29 September 2011  02:45:13AM
[    67.024] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    67.024] Current version of pixman: 0.22.2
[    67.024] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    67.024] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    67.024] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 29 20:28:47 2011
[    67.024] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    67.024] (==) No Layout section.  Using the first Screen section.
[    67.024] (==) No screen section available. Using defaults.
[    67.024] (**) |-->Screen "Default Screen Section" (0)
[    67.024] (**) |   |-->Monitor "<default monitor>"
[    67.024] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    67.024] (==) Automatically adding devices
[    67.024] (==) Automatically enabling devices
[    67.025] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    67.025] 	Entry deleted from font path.
[    67.025] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    67.025] 	Entry deleted from font path.
[    67.025] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    67.025] 	Entry deleted from font path.
[    67.025] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    67.025] 	Entry deleted from font path.
[    67.025] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    67.025] 	Entry deleted from font path.
[    67.025] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    67.025] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    67.025] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    67.025] (II) Loader magic: 0x7e0220
[    67.025] (II) Module ABI versions:
[    67.025] 	X.Org ANSI C Emulation: 0.4
[    67.025] 	X.Org Video Driver: 10.0
[    67.025] 	X.Org XInput driver : 12.3
[    67.025] 	X.Org Server Extension : 5.0
[    67.025] (--) PCI:*(0:0:2:0) 8086:0116:106b:00dc rev 9, Mem @ 0xb0000000/4194304, 0xa0000000/268435456, I/O @ 0x00003000/64
[    67.025] (--) PCI: (0:1:0:0) 1002:6760:106b:00e1 rev 0, Mem @ 0x90000000/268435456, 0xb0800000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    67.025] (II) Open ACPI successful (/var/run/acpid.socket)
[    67.025] (II) LoadModule: "extmod"
[    67.026] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    67.026] (II) Module extmod: vendor="X.Org Foundation"
[    67.026] 	compiled for 1.10.4, module version = 1.0.0
[    67.026] 	Module class: X.Org Server Extension
[    67.026] 	ABI class: X.Org Server Extension, version 5.0
[    67.026] (II) Loading extension MIT-SCREEN-SAVER
[    67.026] (II) Loading extension XFree86-VidModeExtension
[    67.026] (II) Loading extension XFree86-DGA
[    67.026] (II) Loading extension DPMS
[    67.026] (II) Loading extension XVideo
[    67.026] (II) Loading extension XVideo-MotionCompensation
[    67.026] (II) Loading extension X-Resource
[    67.026] (II) LoadModule: "dbe"
[    67.026] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    67.026] (II) Module dbe: vendor="X.Org Foundation"
[    67.026] 	compiled for 1.10.4, module version = 1.0.0
[    67.026] 	Module class: X.Org Server Extension
[    67.026] 	ABI class: X.Org Server Extension, version 5.0
[    67.026] (II) Loading extension DOUBLE-BUFFER
[    67.026] (II) LoadModule: "glx"
[    67.026] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    67.026] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    67.026] 	compiled for 6.9.0, module version = 1.0.0
[    67.026] (II) Loading extension GLX
[    67.026] (II) LoadModule: "record"
[    67.027] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    67.027] (II) Module record: vendor="X.Org Foundation"
[    67.027] 	compiled for 1.10.4, module version = 1.13.0
[    67.027] 	Module class: X.Org Server Extension
[    67.027] 	ABI class: X.Org Server Extension, version 5.0
[    67.027] (II) Loading extension RECORD
[    67.027] (II) LoadModule: "dri"
[    67.027] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    67.027] (II) Module dri: vendor="X.Org Foundation"
[    67.027] 	compiled for 1.10.4, module version = 1.0.0
[    67.027] 	ABI class: X.Org Server Extension, version 5.0
[    67.027] (II) Loading extension XFree86-DRI
[    67.027] (II) LoadModule: "dri2"
[    67.027] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    67.027] (II) Module dri2: vendor="X.Org Foundation"
[    67.027] 	compiled for 1.10.4, module version = 1.2.0
[    67.027] 	ABI class: X.Org Server Extension, version 5.0
[    67.027] (II) Loading extension DRI2
[    67.027] (==) Matched intel as autoconfigured driver 0
[    67.027] (==) Matched vesa as autoconfigured driver 1
[    67.027] (==) Matched fbdev as autoconfigured driver 2
[    67.027] (==) Assigned the driver to the xf86ConfigLayout
[    67.027] (II) LoadModule: "intel"
[    67.028] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    67.028] (II) Module intel: vendor="X.Org Foundation"
[    67.028] 	compiled for 1.10.2.902, module version = 2.15.901
[    67.028] 	Module class: X.Org Video Driver
[    67.028] 	ABI class: X.Org Video Driver, version 10.0
[    67.028] (II) LoadModule: "vesa"
[    67.028] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    67.028] (II) Module vesa: vendor="X.Org Foundation"
[    67.028] 	compiled for 1.10.2, module version = 2.3.0
[    67.028] 	Module class: X.Org Video Driver
[    67.028] 	ABI class: X.Org Video Driver, version 10.0
[    67.028] (II) LoadModule: "fbdev"
[    67.028] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    67.028] (II) Module fbdev: vendor="X.Org Foundation"
[    67.028] 	compiled for 1.10.0, module version = 0.4.2
[    67.028] 	ABI class: X.Org Video Driver, version 10.0
[    67.028] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    67.028] (II) VESA: driver for VESA chipsets: vesa
[    67.028] (II) FBDEV: driver for framebuffer: fbdev
[    67.028] (--) using VT number 8

[    67.033] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    67.033] (WW) Falling back to old probe method for fbdev
[    67.033] (II) Loading sub module "fbdevhw"
[    67.033] (II) LoadModule: "fbdevhw"
[    67.034] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    67.034] (II) Module fbdevhw: vendor="X.Org Foundation"
[    67.034] 	compiled for 1.10.4, module version = 0.0.2
[    67.034] 	ABI class: X.Org Video Driver, version 10.0
[    67.034] (II) Loading sub module "vbe"
[    67.034] (II) LoadModule: "vbe"
[    67.034] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    67.034] (II) Module vbe: vendor="X.Org Foundation"
[    67.034] 	compiled for 1.10.4, module version = 1.1.0
[    67.034] 	ABI class: X.Org Video Driver, version 10.0
[    67.034] (II) Loading sub module "int10"
[    67.034] (II) LoadModule: "int10"
[    67.034] (II) Loading /usr/lib/xorg/modules/libint10.so
[    67.034] (II) Module int10: vendor="X.Org Foundation"
[    67.034] 	compiled for 1.10.4, module version = 1.0.0
[    67.034] 	ABI class: X.Org Video Driver, version 10.0
[    67.034] (II) VESA(0): initializing int10
[    67.035] (EE) VESA(0): V_BIOS address 0xd00 out of range
[    67.035] (II) UnloadModule: "vesa"
[    67.035] (II) Unloading vesa
[    67.035] (II) UnloadModule: "int10"
[    67.035] (II) Unloading int10
[    67.035] (II) UnloadModule: "vbe"
[    67.035] (II) Unloading vbe
[    67.035] (EE) Screen(s) found, but none have a usable configuration.
[    67.035] 
Fatal server error:
[    67.035] no screens found
[    67.035] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    67.035] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    67.035] 
[    67.042]  ddxSigGiveUp: Closing log
```

---

### Post by oknoproblem on 2011-10-01
Hey MaxxABillion, I have a 8,2 too, that it is the DVD drive with the problem. A work around is to burn a Natty CD, then make a USB drive with the same image.

The problem is no longer there with 11.10

eufrat:
My Ubuntu broke after the latest update; reinstalling solved the problem.

---

### Post by eufrat on 2011-10-01
Still no luck with my macbook 8,2 with 11.10 installed from alternative-amd64 and efi mode couple days ago. Just made dist-upgrade. I'm stuck in screen where is ubuntu and 5 dots (nothing works). With boot parameter nomodeset  it's stuck after "checking battery state" or something and ctrl+alt+f1 works.

I have no idea what to do next. Something says it's related to GPU..

sorry bad english.

Last Xorg.0.log was taken with "nomodeset" boot and same results with latest upgrades

and here is Xorg.0.log with normal boot and latest upgrades
```
[    23.623] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    23.623] X Protocol Version 11, Revision 0
[    23.623] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    23.623] Current Operating System: Linux mah-pook 3.0.0-12-generic #19-Ubuntu SMP Fri Sep 23 21:23:39 UTC 2011 x86_64
[    23.623] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=5929eb72-139f-419e-b0aa-d5a3dc4e658e ro quiet splash vt.handoff=7
[    23.623] Build Date: 29 September 2011  02:45:13AM
[    23.623] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    23.623] Current version of pixman: 0.22.2
[    23.623] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.623] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.623] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  1 15:07:24 2011
[    23.751] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.862] (==) No Layout section.  Using the first Screen section.
[    23.862] (==) No screen section available. Using defaults.
[    23.862] (**) |-->Screen "Default Screen Section" (0)
[    23.862] (**) |   |-->Monitor "<default monitor>"
[    23.862] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.862] (==) Automatically adding devices
[    23.862] (==) Automatically enabling devices
[    23.910] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.910] 	Entry deleted from font path.
[    23.910] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.910] 	Entry deleted from font path.
[    23.910] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.910] 	Entry deleted from font path.
[    23.928] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.928] 	Entry deleted from font path.
[    23.928] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.928] 	Entry deleted from font path.
[    23.969] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    23.970] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.970] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.970] (II) Loader magic: 0x7e0220
[    23.970] (II) Module ABI versions:
[    23.970] 	X.Org ANSI C Emulation: 0.4
[    23.970] 	X.Org Video Driver: 10.0
[    23.970] 	X.Org XInput driver : 12.3
[    23.970] 	X.Org Server Extension : 5.0
[    23.970] (--) PCI:*(0:0:2:0) 8086:0116:106b:00dc rev 9, Mem @ 0xb0000000/4194304, 0xa0000000/268435456, I/O @ 0x00003000/64
[    23.970] (--) PCI: (0:1:0:0) 1002:6760:106b:00e1 rev 0, Mem @ 0x90000000/268435456, 0xb0800000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    23.970] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.970] (II) LoadModule: "extmod"
[    24.251] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.277] (II) Module extmod: vendor="X.Org Foundation"
[    24.277] 	compiled for 1.10.4, module version = 1.0.0
[    24.277] 	Module class: X.Org Server Extension
[    24.277] 	ABI class: X.Org Server Extension, version 5.0
[    24.277] (II) Loading extension MIT-SCREEN-SAVER
[    24.277] (II) Loading extension XFree86-VidModeExtension
[    24.277] (II) Loading extension XFree86-DGA
[    24.277] (II) Loading extension DPMS
[    24.277] (II) Loading extension XVideo
[    24.277] (II) Loading extension XVideo-MotionCompensation
[    24.277] (II) Loading extension X-Resource
[    24.277] (II) LoadModule: "dbe"
[    24.278] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.278] (II) Module dbe: vendor="X.Org Foundation"
[    24.278] 	compiled for 1.10.4, module version = 1.0.0
[    24.278] 	Module class: X.Org Server Extension
[    24.278] 	ABI class: X.Org Server Extension, version 5.0
[    24.278] (II) Loading extension DOUBLE-BUFFER
[    24.278] (II) LoadModule: "glx"
[    24.278] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    24.341] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    24.342] 	compiled for 6.9.0, module version = 1.0.0
[    24.342] (II) Loading extension GLX
[    24.342] (II) LoadModule: "record"
[    24.342] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.343] (II) Module record: vendor="X.Org Foundation"
[    24.343] 	compiled for 1.10.4, module version = 1.13.0
[    24.343] 	Module class: X.Org Server Extension
[    24.343] 	ABI class: X.Org Server Extension, version 5.0
[    24.343] (II) Loading extension RECORD
[    24.343] (II) LoadModule: "dri"
[    24.343] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.358] (II) Module dri: vendor="X.Org Foundation"
[    24.358] 	compiled for 1.10.4, module version = 1.0.0
[    24.358] 	ABI class: X.Org Server Extension, version 5.0
[    24.358] (II) Loading extension XFree86-DRI
[    24.358] (II) LoadModule: "dri2"
[    24.358] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.359] (II) Module dri2: vendor="X.Org Foundation"
[    24.359] 	compiled for 1.10.4, module version = 1.2.0
[    24.359] 	ABI class: X.Org Server Extension, version 5.0
[    24.359] (II) Loading extension DRI2
[    24.359] (==) Matched intel as autoconfigured driver 0
[    24.359] (==) Matched vesa as autoconfigured driver 1
[    24.359] (==) Matched fbdev as autoconfigured driver 2
[    24.359] (==) Assigned the driver to the xf86ConfigLayout
[    24.359] (II) LoadModule: "intel"
[    24.359] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.386] (II) Module intel: vendor="X.Org Foundation"
[    24.386] 	compiled for 1.10.2.902, module version = 2.15.901
[    24.386] 	Module class: X.Org Video Driver
[    24.386] 	ABI class: X.Org Video Driver, version 10.0
[    24.386] (II) LoadModule: "vesa"
[    24.386] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.418] (II) Module vesa: vendor="X.Org Foundation"
[    24.418] 	compiled for 1.10.2, module version = 2.3.0
[    24.418] 	Module class: X.Org Video Driver
[    24.418] 	ABI class: X.Org Video Driver, version 10.0
[    24.418] (II) LoadModule: "fbdev"
[    24.418] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.418] (II) Module fbdev: vendor="X.Org Foundation"
[    24.418] 	compiled for 1.10.0, module version = 0.4.2
[    24.418] 	ABI class: X.Org Video Driver, version 10.0
[    24.418] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    24.419] (II) VESA: driver for VESA chipsets: vesa
[    24.419] (II) FBDEV: driver for framebuffer: fbdev
[    24.419] (++) using VT number 7

[    24.420] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.420] (WW) Falling back to old probe method for vesa
[    24.420] (WW) Falling back to old probe method for fbdev
[    24.420] (II) Loading sub module "fbdevhw"
[    24.420] (II) LoadModule: "fbdevhw"
[    24.420] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.446] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.446] 	compiled for 1.10.4, module version = 0.0.2
[    24.446] 	ABI class: X.Org Video Driver, version 10.0
[    24.446] drmOpenDevice: node name is /dev/dri/card0
[    24.447] drmOpenDevice: open result is 12, (OK)
[    24.447] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.447] drmOpenDevice: node name is /dev/dri/card0
[    24.447] drmOpenDevice: open result is 12, (OK)
[    24.447] drmOpenByBusid: drmOpenMinor returns 12
[    24.447] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.447] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.447] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.447] (==) intel(0): RGB weight 888
[    24.447] (==) intel(0): Default visual is TrueColor
[    24.447] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    24.447] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    24.447] (**) intel(0): Relaxed fencing enabled
[    24.447] (**) intel(0): Wait on SwapBuffers? enabled
[    24.447] (**) intel(0): Triple buffering? enabled
[    24.447] (**) intel(0): Framebuffer tiled
[    24.447] (**) intel(0): Pixmaps tiled
[    24.447] (**) intel(0): 3D buffers tiled
[    24.447] (**) intel(0): SwapBuffers wait enabled
[    24.447] (==) intel(0): video overlay key set to 0x101fe
[    24.447] (II) intel(0): Output VGA1 has no monitor section
[    24.470] (II) intel(0): Output HDMI1 has no monitor section
[    24.516] (II) intel(0): Output DP1 has no monitor section
[    24.516] (II) intel(0): EDID for output VGA1
[    24.539] (II) intel(0): EDID for output HDMI1
[    24.584] (II) intel(0): EDID for output DP1
[    24.584] (II) intel(0): Output VGA1 disconnected
[    24.584] (II) intel(0): Output HDMI1 disconnected
[    24.584] (II) intel(0): Output DP1 disconnected
[    24.584] (WW) intel(0): No outputs definitely connected, trying again...
[    24.584] (II) intel(0): Output VGA1 disconnected
[    24.584] (II) intel(0): Output HDMI1 disconnected
[    24.584] (II) intel(0): Output DP1 disconnected
[    24.584] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    24.584] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.584] (II) intel(0): Kernel page flipping support detected, enabling
[    24.584] (==) intel(0): DPI set to (96, 96)
[    24.584] (II) Loading sub module "fb"
[    24.584] (II) LoadModule: "fb"
[    24.584] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.607] (II) Module fb: vendor="X.Org Foundation"
[    24.607] 	compiled for 1.10.4, module version = 1.0.0
[    24.607] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.607] (II) Loading sub module "dri2"
[    24.607] (II) LoadModule: "dri2"
[    24.607] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.607] (II) Module dri2: vendor="X.Org Foundation"
[    24.607] 	compiled for 1.10.4, module version = 1.2.0
[    24.607] 	ABI class: X.Org Server Extension, version 5.0
[    24.607] (II) UnloadModule: "vesa"
[    24.607] (II) Unloading vesa
[    24.607] (II) UnloadModule: "fbdev"
[    24.607] (II) Unloading fbdev
[    24.607] (II) UnloadModule: "fbdevhw"
[    24.607] (II) Unloading fbdevhw
[    24.607] (==) Depth 24 pixmap format is 32 bpp
[    24.608] (II) intel(0): [DRI2] Setup complete
[    24.608] (II) intel(0): [DRI2]   DRI driver: i965
[    24.608] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    24.684] (II) UXA(0): Driver registered support for the following operations:
[    24.684] (II)         solid
[    24.684] (II)         copy
[    24.684] (II)         composite (RENDER acceleration)
[    24.684] (II)         put_image
[    24.684] (II)         get_image
[    24.684] (==) intel(0): Backing store disabled
[    24.684] (==) intel(0): Silken mouse enabled
[    24.708] (II) intel(0): Initializing HW Cursor
[    24.708] (EE) intel(0): Couldn't create pixmap for fbcon
[    24.708] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.708] (==) intel(0): DPMS enabled
[    24.708] (==) intel(0): Intel XvMC decoder enabled
[    24.708] (II) intel(0): Set up textured video
[    24.708] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    24.708] (II) intel(0): direct rendering: DRI2 Enabled
[    24.708] (==) intel(0): hotplug detection: "enabled"
[    24.708] (--) RandR disabled
[    24.708] (II) Initializing built-in extension Generic Event Extension
[    24.708] (II) Initializing built-in extension SHAPE
[    24.708] (II) Initializing built-in extension MIT-SHM
[    24.708] (II) Initializing built-in extension XInputExtension
[    24.708] (II) Initializing built-in extension XTEST
[    24.708] (II) Initializing built-in extension BIG-REQUESTS
[    24.708] (II) Initializing built-in extension SYNC
[    24.708] (II) Initializing built-in extension XKEYBOARD
[    24.708] (II) Initializing built-in extension XC-MISC
[    24.708] (II) Initializing built-in extension SECURITY
[    24.708] (II) Initializing built-in extension XINERAMA
[    24.708] (II) Initializing built-in extension XFIXES
[    24.708] (II) Initializing built-in extension RENDER
[    24.708] (II) Initializing built-in extension RANDR
[    24.708] (II) Initializing built-in extension COMPOSITE
[    24.708] (II) Initializing built-in extension DAMAGE
[    24.708] (II) Initializing built-in extension GESTURE
[    24.709] (EE) GLX error: Can not get required symbols.
[    24.996] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.015] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    25.015] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.015] (II) LoadModule: "evdev"
[    25.015] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.118] (II) Module evdev: vendor="X.Org Foundation"
[    25.118] 	compiled for 1.10.2, module version = 2.6.0
[    25.118] 	Module class: X.Org XInput Driver
[    25.118] 	ABI class: X.Org XInput driver, version 12.3
[    25.118] (II) Using input driver 'evdev' for 'Power Button'
[    25.118] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.118] (**) Power Button: always reports core events
[    25.118] (**) Power Button: Device: "/dev/input/event3"
[    25.118] (--) Power Button: Found keys
[    25.118] (II) Power Button: Configuring as keyboard
[    25.118] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    25.118] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.118] (**) Option "xkb_rules" "evdev"
[    25.118] (**) Option "xkb_model" "pc105"
[    25.118] (**) Option "xkb_layout" "fi"
[    25.118] (**) Option "xkb_variant" "mac"
[    25.120] (II) XKB: reuse xkmfile /var/lib/xkb/server-A83EB2178712BE1B41BBA098AFF857AE78311E14.xkm
[    25.129] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    25.129] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.129] (II) Using input driver 'evdev' for 'Video Bus'
[    25.129] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.129] (**) Video Bus: always reports core events
[    25.129] (**) Video Bus: Device: "/dev/input/event10"
[    25.129] (--) Video Bus: Found keys
[    25.129] (II) Video Bus: Configuring as keyboard
[    25.129] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event10"
[    25.129] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.129] (**) Option "xkb_rules" "evdev"
[    25.129] (**) Option "xkb_model" "pc105"
[    25.129] (**) Option "xkb_layout" "fi"
[    25.129] (**) Option "xkb_variant" "mac"
[    25.129] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    25.129] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.129] (II) Using input driver 'evdev' for 'Video Bus'
[    25.129] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.129] (**) Video Bus: always reports core events
[    25.129] (**) Video Bus: Device: "/dev/input/event9"
[    25.130] (--) Video Bus: Found keys
[    25.130] (II) Video Bus: Configuring as keyboard
[    25.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input9/event9"
[    25.130] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.130] (**) Option "xkb_rules" "evdev"
[    25.130] (**) Option "xkb_model" "pc105"
[    25.130] (**) Option "xkb_layout" "fi"
[    25.130] (**) Option "xkb_variant" "mac"
[    25.170] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.170] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.170] (II) Using input driver 'evdev' for 'Power Button'
[    25.170] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.170] (**) Power Button: always reports core events
[    25.170] (**) Power Button: Device: "/dev/input/event1"
[    25.170] (--) Power Button: Found keys
[    25.170] (II) Power Button: Configuring as keyboard
[    25.170] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.170] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.170] (**) Option "xkb_rules" "evdev"
[    25.170] (**) Option "xkb_model" "pc105"
[    25.170] (**) Option "xkb_layout" "fi"
[    25.170] (**) Option "xkb_variant" "mac"
[    25.170] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.170] (II) No input driver/identifier specified (ignoring)
[    25.170] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.170] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.170] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.170] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.170] (**) Sleep Button: always reports core events
[    25.170] (**) Sleep Button: Device: "/dev/input/event2"
[    25.170] (--) Sleep Button: Found keys
[    25.170] (II) Sleep Button: Configuring as keyboard
[    25.171] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.171] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.171] (**) Option "xkb_rules" "evdev"
[    25.171] (**) Option "xkb_model" "pc105"
[    25.171] (**) Option "xkb_layout" "fi"
[    25.171] (**) Option "xkb_variant" "mac"
[    25.171] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event11)
[    25.171] (II) No input driver/identifier specified (ignoring)
[    25.173] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event4)
[    25.173] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[    25.173] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    25.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.173] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    25.173] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event4"
[    25.173] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found keys
[    25.173] (II) Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[    25.173] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[    25.173] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
[    25.173] (**) Option "xkb_rules" "evdev"
[    25.173] (**) Option "xkb_model" "pc105"
[    25.173] (**) Option "xkb_layout" "fi"
[    25.173] (**) Option "xkb_variant" "mac"
[    25.174] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event5)
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev pointer catchall"
[    25.174] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    25.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event5"
[    25.174] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found 3 mouse buttons
[    25.174] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found relative axes
[    25.174] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found x and y relative axes
[    25.174] (II) Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as mouse
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: YAxisMapping: buttons 4 and 5
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.174] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input5/event5"
[    25.174] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: MOUSE)
[    25.174] (II) Apple Inc. Apple Internal Keyboard / Trackpad: initialized for relative axes.
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) keeping acceleration scheme 1
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration profile 0
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration factor: 2.000
[    25.174] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration threshold: 4
[    25.174] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/mouse0)
[    25.174] (II) No input driver/identifier specified (ignoring)
[    25.174] (II) config/udev: Adding input device FaceTime HD Camera (Built-in) (/dev/input/event6)
[    25.174] (**) FaceTime HD Camera (Built-in): Applying InputClass "evdev keyboard catchall"
[    25.174] (II) Using input driver 'evdev' for 'FaceTime HD Camera (Built-in)'
[    25.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.174] (**) FaceTime HD Camera (Built-in): always reports core events
[    25.174] (**) FaceTime HD Camera (Built-in): Device: "/dev/input/event6"
[    25.175] (--) FaceTime HD Camera (Built-in): Found keys
[    25.175] (II) FaceTime HD Camera (Built-in): Configuring as keyboard
[    25.175] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input12/event6"
[    25.175] (II) XINPUT: Adding extended input device "FaceTime HD Camera (Built-in)" (type: KEYBOARD)
[    25.175] (**) Option "xkb_rules" "evdev"
[    25.175] (**) Option "xkb_model" "pc105"
[    25.175] (**) Option "xkb_layout" "fi"
[    25.175] (**) Option "xkb_variant" "mac"
[    25.179] (II) config/udev: Adding input device applesmc (/dev/input/event8)
[    25.179] (II) No input driver/identifier specified (ignoring)
[    25.179] (II) config/udev: Adding input device applesmc (/dev/input/js0)
[    25.179] (II) No input driver/identifier specified (ignoring)
[    48.773] (II) Open ACPI successful (/var/run/acpid.socket)
[    48.773] (EE) intel(0): Couldn't create pixmap for fbcon
```

---

### Post by eufrat on 2011-10-03
Is there some difference between macbook pro 8,2 bough with 10.6 installed and macbook pro 8,2 bought with 10.7 installed? Does anybody know?

i'm getting really frustrated about this problem. I want to use ubuntu again. This osx is no't for me.. (i bough't macbook only for music and audio use)

---

### Post by JJJ&amp;J on 2011-10-03
> **eufrat said:**
> Is there some difference between macbook pro 8,2 bough with 10.6 installed and macbook pro 8,2 bought with 10.7 installed? Does anybody know?

i'm getting really frustrated about this problem. I want to use ubuntu again. This osx is no't for me.. (i bough't macbook only for music and audio use)

I think you just need to install the nvidia driver, add a properly edited xorg.conf file so the nvidia driver loads during boot, blacklist the intel driver, maybe a few other things along those lines...

...OR, since I have a 2010 6,2, this method is now outdated and should be disregarded.

---

