---
title: "Best graphics experience with Radeon AGP-cards (PowerMac G5)"
date: 2016-10-13
forum: Apple Hardware Users
---

### Post by ernsteiswuerfel on 2016-10-13
Perhaps this is really helpful to other PPC-users as the desktop on my PowerMac G5 7,3 was *reeaaally* sluggish and now it's not.
Got this idea after reading various PPC-specific bug reports on the xorg bugtracker, e.g. [Bug 95017]("https://bugs.freedesktop.org/show_bug.cgi?id=95017"), [Bug 94877]("https://bugs.freedesktop.org/show_bug.cgi?id=94877").

I added the following **boot-parameter to /etc/yaboot.conf**:
append="root=... radeon.agpmode=8"

Don't forget to write out your yaboot.conf to disk via **sudo ybin -v** afterwards.

And use the following **xorg.conf in /etc/X11**:
```
Section "Device"
    Identifier "Radeon"
    Driver "radeon"
    #Option "DRI" "2"
    #Option "AccelMethod" "exa"
    Option "NoAccel" "True"
EndSection
```
What these config options do is drive the card at maximum AGP-speed but turn off the radeon hardware specific acceleration methods. The boost of bandwith from 133 MB/s (PCI mode, as in radeon.agpmode=-1) to 2133 MB/s (AGP-x8 mode, as in radeon.agpmode=8) outweighs the loss of specific acceleration a lot, at least on my G5 machine with its "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150).

You have to check first what maximum AGP-speed your card and your AGP-Northbride support. Then adjust the radeon.agpmode=x boot-parameter accordingly. On my G5 it's radeon.agpmode=8, on my PowerBook G4s it would be radeon.agpmode=4. If this wors correctly you will get following messages from your kernel:
```
~$ dmesg | grep -i agp
[    0.000000] Found U3-AGP PCI host bridge.  Firmware bus number: 240->255
[    0.000000] Kernel command line: ro root=UUID=637cdd2f-ef32-412f-9efd-8cf51db84ad3 radeon.agpmode=8 
[    5.896623] Linux agpgart interface v0.103
[    7.746566] agpgart-uninorth 0000:f0:0b.0: Apple U3H chipset
[    7.794476] agpgart-uninorth 0000:f0:0b.0: configuring for size idx: 64
[    7.803914] agpgart-uninorth 0000:f0:0b.0: AGP aperture is 256M @ 0x0
[    8.147292] [drm] AGP mode requested: 8
[    8.147321] agpgart-uninorth 0000:f0:0b.0: putting AGP V3 device into 8x mode
[    8.147332] radeon 0000:f0:10.0: putting AGP V3 device into 8x mode

```
If your hardware does not support the radeon.agpmode you requested it simply should inform you that this mode is not supported and drive the card with it's default vaiue.

If you used some kind of compositor for the desktop you should turn it off first. In Ubuntu MATE this is done via System->Settings->Appearance->MATE-Tweaks->Windows (Marco, no composit).

---

### Post by rican-linux on 2016-10-15
How can you verfiy your speeds? I have your set up on my powerbook g4.

---

### Post by rican-linux on 2016-10-16
I have also tested on my iBook G4 and can verify this work as well.

```

rican-linux@debian-powerpc:~/Desktop$ dmesg |grep -i agp
[    0.000000] Kernel command line: root=UUID=2b8ccffa-b987-473e-9bb6-f8b8ac6c1c27 ro quiet splash radeon.agpmode=4 
[    1.718332] Linux agpgart interface v0.103
[    1.718378] agpgart-uninorth 0000:00:0b.0: Apple UniNorth 2 chipset
[    1.719660] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[    1.719791] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
[   14.363999] [drm] AGP mode requested: 4
[   14.364027] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 4x mode
[   14.364086] radeon 0000:00:10.0: putting AGP V2 device into 4x mode

```

I cannot believe the performace improvement I am seeing! Ususally on this iBook if I use FF the fans kick in if I go to gmail for example. Now it does not happen. In the past if I watched video with no hw accelleration and used the x11 driver the CPU would max and fans would scream. Now videos play smoothly in mpv with x11 driver. Even in lightweight browsers such as midori, surf, luakit I can even watch youtube with 360p or 240p. 

Thanks I am definately going to share
Herminio

---

### Post by rican-linux on 2016-10-16
I have done some more testing with the iBook. There are some videos that will stick kick the fan when playing in mpv. Streaming videos work but my fans kick in right away. I have the same set up on my PowerBook G4 and am seeing better performace there as well.

---

### Post by ernsteiswuerfel on 2016-10-17
@rican-linux:
Glad to hear that this works with your setup too! What graphic cards are in your iBook & Powerbook? I only got Radeon r300-class cards, so I can't make any statements about different hardware. I can only suppose this can improve performance on other rx00-card systems too if the machine has at least AGPx2 and an otherwise hardware acceleration is not.

The only machine where I get *_full* HW-acceleratio_**n** is my **PowerBook 5,8**. There I don't need the "NoAccel"-option in xorg.confg and can drive the card with AGPx4. This does not work on a PB 5,6 or 5,4 which I had. There must be some subtile differences between the 5,8 model and the other ones...

I will continue playing around with some xorg.conf options, e.g. "AccelMethod", "ColorTiling", "ColorTiling2D" look interesting. Let's see what leads to a GPU-lockup and if not to more performance. ;)

---

### Post by rican-linux on 2016-10-17
My iBook has a radeon 9400 (r300)
PowerBook 9600 (r300)

Here is something on my PowerMac G5 7,2 I have full hw acceleration on Ubuntu but not on Debian.

---

### Post by ernsteiswuerfel on 2016-10-17
> **rican-linux said:**
> Here is something on my PowerMac G5 7,2 I have full hw acceleration on Ubuntu but not on Debian.
This is somewhat surprising! What card you got in your G5 and what does your /var/log/Xorg.0.log tell? I was not able to get a full accelerated desktop with my Radeon 9650 yet.

 Maybe it's due to an older xorg stack on Debian? Ubuntu uses latest xorg-1.18.4 and 7.7.x radeon drivers.

---

### Post by rican-linux on 2016-10-17
Here is the card listed in Xorg.0.log

```

[    45.944] (--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)

```

Here is my dmesg

```

rican-linux@Lubuntu-G5:~$ dmesg |grep -e radeon -e drm -e agp
[    5.725462] Linux agpgart interface v0.103
[    7.366602] agpgart-uninorth 0000:f0:0b.0: Apple U3 chipset
[    7.390331] [drm] Initialized drm 1.1.0 20060810
[    7.438792] agpgart-uninorth 0000:f0:0b.0: configuring for size idx: 64
[    7.438943] agpgart-uninorth 0000:f0:0b.0: AGP aperture is 256M @ 0x0
[    7.525634] [drm] radeon kernel modesetting enabled.
[    7.525700] fb: switching to radeondrmfb from OFfb ATY,Simone
[    7.528397] fb: switching to radeondrmfb from OFfb ATY,Simone
[    7.529583] radeon 0000:f0:10.0: enabling device (0006 -> 0007)
[    7.530140] [drm] initializing kernel modesetting (RV350 0x1002:0x4150 0x1002:0x4150 0x00).
[    7.530164] [drm] register mmio base: 0xA0000000
[    7.530166] [drm] register mmio size: 65536
[    7.530210] radeon 0000:f0:10.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
[    7.622759] [drm] Not an x86 BIOS ROM, not using.
[    7.622784] [drm] Using device-tree clock info
[    7.622825] agpgart-uninorth 0000:f0:0b.0: putting AGP V3 device into 8x mode
[    7.622834] radeon 0000:f0:10.0: putting AGP V3 device into 8x mode
[    7.622944] radeon 0000:f0:10.0: GTT: 256M 0x00000000 - 0x0FFFFFFF
[    7.622948] [drm] Generation 2 PCI interface, using max accessible memory
[    7.622972] radeon 0000:f0:10.0: VRAM: 256M 0x00000000B0000000 - 0x00000000BFFFFFFF (64M used)
[    7.623156] [drm] Detected VRAM RAM=256M, BAR=256M
[    7.623159] [drm] RAM width 128bits DDR
[    7.623428] [drm] radeon: 64M of VRAM memory ready
[    7.623431] [drm] radeon: 256M of GTT memory ready.
[    7.623516] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[    7.623698] radeon 0000:f0:10.0: WB disabled
[    7.623705] radeon 0000:f0:10.0: fence driver on ring 0 use gpu addr 0x0000000000000000 and cpu addr 0xd00000000137e000
[    7.623710] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    7.623712] [drm] Driver supports precise vblank timestamp query.
[    7.623760] [drm] radeon: irq initialized.
[    7.623778] [drm] Loading R300 Microcode
[    7.624368] [drm] radeon: ring at 0x0000000000001000
[    7.624400] [drm] ring test succeeded in 0 usecs
[    7.625010] [drm] ib test succeeded in 0 usecs
[    7.628467] [drm] Connector Table: 12 (mac g5 9600)
[    7.628482] [drm] No valid Ext TMDS info found in BIOS
[    7.628489] [drm] No TV DAC info found in BIOS
[    7.628645] [drm] No TMDS info found in BIOS
[    7.628803] [drm] Radeon Display Connectors
[    7.628805] [drm] Connector 0:
[    7.628806] [drm]   DVI-I-1
[    7.628808] [drm]   HPD1
[    7.628810] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    7.628812] [drm]   Encoders:
[    7.628813] [drm]     DFP2: INTERNAL_DVO1
[    7.628815] [drm]     CRT2: INTERNAL_DAC2
[    7.628816] [drm] Connector 1:
[    7.628817] [drm]   DVI-I-2
[    7.628818] [drm]   HPD2
[    7.628820] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    7.628821] [drm]   Encoders:
[    7.628822] [drm]     DFP1: INTERNAL_TMDS1
[    7.628823] [drm]     CRT1: INTERNAL_DAC1
[    7.628825] [drm] Connector 2:
[    7.628826] [drm]   SVIDEO-1
[    7.628827] [drm]   Encoders:
[    7.628828] [drm]     TV1: INTERNAL_DAC2
[    7.716238] [drm] fb mappable at 0xB0040000
[    7.716242] [drm] vram apper at 0xB0000000
[    7.716244] [drm] size 8294400
[    7.716246] [drm] fb depth is 24
[    7.716247] [drm]    pitch is 7680
[    7.811337] radeon 0000:f0:10.0: fb0: radeondrmfb frame buffer device
[    7.823183] [drm] Initialized radeon 2.46.0 20080528 for 0000:f0:10.0 on minor 0
rican-linux@Lubuntu-G5:~$ 

```

Here is my complete Xorg.0.log

```

rican-linux@Lubuntu-G5:~$ cat /var/log/Xorg.0.log 
[    45.232] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    45.233] X Protocol Version 11, Revision 0
[    45.233] Build Operating System: Linux 4.4.0-31-powerpc64-smp ppc Ubuntu
[    45.233] Current Operating System: Linux Lubuntu-G5 4.8.0-rican #1 SMP Mon Oct 17 02:16:36 MST 2016 ppc64
[    45.233] Kernel command line: root=UUID=1b09e342-f84f-42ad-8997-8964300f6ffc ro quiet splash 
[    45.233] Build Date: 07 September 2016  05:17:08AM
[    45.233] xorg-server 2:1.18.4-1ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.233] Current version of pixman: 0.33.6
[    45.234] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    45.234] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.234] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 17 12:47:21 2016
[    45.307] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.375] (==) No Layout section.  Using the first Screen section.
[    45.375] (==) No screen section available. Using defaults.
[    45.375] (**) |-->Screen "Default Screen Section" (0)
[    45.375] (**) |   |-->Monitor "<default monitor>"
[    45.375] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    45.375] (==) Automatically adding devices
[    45.375] (==) Automatically enabling devices
[    45.375] (==) Automatically adding GPU devices
[    45.375] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    45.376] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/Type1".
[    45.376] 	Entry deleted from font path.
[    45.376] 	(Run 'mkfontdir' on "/usr/share/fonts/X11/Type1").
[    45.376] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.376] 	Entry deleted from font path.
[    45.376] (==) FontPath set to:
	built-ins
[    45.376] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.376] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.388] (II) Loader magic: 0x205a86e8
[    45.388] (II) Module ABI versions:
[    45.388] 	X.Org ANSI C Emulation: 0.4
[    45.388] 	X.Org Video Driver: 20.0
[    45.388] 	X.Org XInput driver : 22.1
[    45.388] 	X.Org Server Extension : 9.0
[    45.390] (++) using VT number 7

[    45.390] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    45.392] (II) xfree86: Adding drm device (/dev/dri/card0)
[    45.395] (--) PCI:*(0:240:16:0) 1002:4150:1002:4150 rev 0, Mem @ 0xb0000000/268435456, 0xa0000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    45.425] (II) LoadModule: "glx"
[    45.572] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.779] (II) Module glx: vendor="X.Org Foundation"
[    45.779] 	compiled for 1.18.4, module version = 1.0.0
[    45.779] 	ABI class: X.Org Server Extension, version 9.0
[    45.779] (==) AIGLX enabled
[    45.779] (==) Matched ati as autoconfigured driver 0
[    45.779] (==) Matched ati as autoconfigured driver 1
[    45.779] (==) Matched modesetting as autoconfigured driver 2
[    45.779] (==) Matched fbdev as autoconfigured driver 3
[    45.780] (==) Assigned the driver to the xf86ConfigLayout
[    45.780] (II) LoadModule: "ati"
[    45.805] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    45.814] (II) Module ati: vendor="X.Org Foundation"
[    45.814] 	compiled for 1.18.4, module version = 7.7.1
[    45.814] 	Module class: X.Org Video Driver
[    45.814] 	ABI class: X.Org Video Driver, version 20.0
[    45.814] (II) LoadModule: "radeon"
[    45.815] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    45.853] (II) Module radeon: vendor="X.Org Foundation"
[    45.853] 	compiled for 1.18.4, module version = 7.7.1
[    45.853] 	Module class: X.Org Video Driver
[    45.853] 	ABI class: X.Org Video Driver, version 20.0
[    45.853] (II) LoadModule: "modesetting"
[    45.854] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    45.861] (II) Module modesetting: vendor="X.Org Foundation"
[    45.861] 	compiled for 1.18.4, module version = 1.18.4
[    45.861] 	Module class: X.Org Video Driver
[    45.861] 	ABI class: X.Org Video Driver, version 20.0
[    45.862] (II) LoadModule: "fbdev"
[    45.862] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.864] (II) Module fbdev: vendor="X.Org Foundation"
[    45.864] 	compiled for 1.18.1, module version = 0.4.4
[    45.864] 	Module class: X.Org Video Driver
[    45.864] 	ABI class: X.Org Video Driver, version 20.0
[    45.864] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    45.882] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    45.882] (II) FBDEV: driver for framebuffer: fbdev
[    45.935] (II) [KMS] Kernel modesetting enabled.
[    45.935] (WW) Falling back to old probe method for modesetting
[    45.935] (WW) Falling back to old probe method for fbdev
[    45.935] (II) Loading sub module "fbdevhw"
[    45.935] (II) LoadModule: "fbdevhw"
[    45.936] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.942] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.942] 	compiled for 1.18.4, module version = 0.0.2
[    45.942] 	ABI class: X.Org Video Driver, version 20.0
[    45.943] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    45.943] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    45.943] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    45.943] (==) RADEON(0): Default visual is TrueColor
[    45.944] (==) RADEON(0): RGB weight 888
[    45.944] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    45.944] (--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
[    45.944] (II) Loading sub module "fb"
[    45.944] (II) LoadModule: "fb"
[    45.944] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.956] (II) Module fb: vendor="X.Org Foundation"
[    45.956] 	compiled for 1.18.4, module version = 1.0.0
[    45.956] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    45.956] (II) Loading sub module "dri2"
[    45.956] (II) LoadModule: "dri2"
[    45.956] (II) Module "dri2" already built-in
[    45.956] (II) Loading sub module "exa"
[    45.956] (II) LoadModule: "exa"
[    45.956] (II) Loading /usr/lib/xorg/modules/libexa.so
[    45.968] (II) Module exa: vendor="X.Org Foundation"
[    45.968] 	compiled for 1.18.4, module version = 2.6.0
[    45.968] 	ABI class: X.Org Video Driver, version 20.0
[    45.968] (II) RADEON(0): KMS Color Tiling: enabled
[    45.968] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    45.968] (II) RADEON(0): KMS Pageflipping: enabled
[    45.968] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    45.998] (II) RADEON(0): Output DVI-0 has no monitor section
[    46.001] (II) RADEON(0): Output DVI-1 has no monitor section
[    46.011] (II) RADEON(0): Output S-video has no monitor section
[    46.042] (II) RADEON(0): EDID for output DVI-0
[    46.042] (II) RADEON(0): Manufacturer: DEL  Model: 4061  Serial#: 1146697804
[    46.042] (II) RADEON(0): Year: 2010  Week: 31
[    46.042] (II) RADEON(0): EDID Version: 1.3
[    46.042] (II) RADEON(0): Digital Display Input
[    46.042] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    46.042] (II) RADEON(0): Gamma: 2.20
[    46.042] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    46.042] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    46.042] (II) RADEON(0): First detailed timing is preferred mode
[    46.042] (II) RADEON(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[    46.042] (II) RADEON(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[    46.042] (II) RADEON(0): Supported established timings:
[    46.042] (II) RADEON(0): 720x400@70Hz
[    46.042] (II) RADEON(0): 640x480@60Hz
[    46.042] (II) RADEON(0): 640x480@75Hz
[    46.042] (II) RADEON(0): 800x600@60Hz
[    46.042] (II) RADEON(0): 800x600@75Hz
[    46.042] (II) RADEON(0): 1024x768@60Hz
[    46.042] (II) RADEON(0): 1024x768@75Hz
[    46.042] (II) RADEON(0): 1280x1024@75Hz
[    46.042] (II) RADEON(0): Manufacturer's mask: 0
[    46.042] (II) RADEON(0): Supported standard timings:
[    46.042] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    46.042] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    46.042] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    46.042] (II) RADEON(0): Supported detailed timing:
[    46.042] (II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    46.043] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    46.043] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    46.043] (II) RADEON(0): Serial No: TYXD9085DY8L
[    46.043] (II) RADEON(0): Monitor name: DELL P2211H
[    46.043] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    46.043] (II) RADEON(0): EDID (in hex):
[    46.043] (II) RADEON(0): 	00ffffffffffff0010ac61404c385944
[    46.043] (II) RADEON(0): 	1f14010380301b78ea9535a159579f27
[    46.043] (II) RADEON(0): 	0e5054a54b00714f8180d1c001010101
[    46.043] (II) RADEON(0): 	010101010101023a801871382d40582c
[    46.043] (II) RADEON(0): 	4500dd0c1100001e000000ff00545958
[    46.043] (II) RADEON(0): 	44393038354459384c0a000000fc0044
[    46.043] (II) RADEON(0): 	454c4c205032323131480a20000000fd
[    46.043] (II) RADEON(0): 	00384c1e5311000a202020202020009f
[    46.043] (II) RADEON(0): Printing probed modes for output DVI-0
[    46.043] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    46.043] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    46.043] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    46.043] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    46.043] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    46.043] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    46.043] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    46.043] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    46.043] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    46.043] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    46.043] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    46.046] (II) RADEON(0): EDID for output DVI-1
[    46.056] (II) RADEON(0): EDID for output S-video
[    46.056] (II) RADEON(0): Output DVI-0 connected
[    46.056] (II) RADEON(0): Output DVI-1 disconnected
[    46.056] (II) RADEON(0): Output S-video disconnected
[    46.056] (II) RADEON(0): Using exact sizes for initial modes
[    46.056] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080 +0+0
[    46.056] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    46.057] (II) RADEON(0): mem size init: gart size :fdff000 vram size: s:4000000 visible:37d7000
[    46.057] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    46.057] (==) RADEON(0): DPI set to (96, 96)
[    46.057] (II) Loading sub module "ramdac"
[    46.057] (II) LoadModule: "ramdac"
[    46.057] (II) Module "ramdac" already built-in
[    46.057] (II) UnloadModule: "modesetting"
[    46.057] (II) Unloading modesetting
[    46.057] (II) UnloadModule: "fbdev"
[    46.057] (II) Unloading fbdev
[    46.057] (II) UnloadSubModule: "fbdevhw"
[    46.057] (II) Unloading fbdevhw
[    46.057] (--) Depth 24 pixmap format is 32 bpp
[    46.059] (II) RADEON(0): [DRI2] Setup complete
[    46.059] (II) RADEON(0): [DRI2]   DRI driver: r300
[    46.059] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    46.059] (II) RADEON(0): Front buffer size: 8160K
[    46.059] (II) RADEON(0): VRAM usage limit set to 44089K
[    46.075] (==) RADEON(0): DRI3 disabled
[    46.075] (==) RADEON(0): Backing store enabled
[    46.075] (II) RADEON(0): Direct rendering enabled
[    46.075] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    46.075] (II) EXA(0): Driver allocated offscreen pixmaps
[    46.075] (II) EXA(0): Driver registered support for the following operations:
[    46.075] (II)         Solid
[    46.075] (II)         Copy
[    46.075] (II)         Composite (RENDER acceleration)
[    46.075] (II)         UploadToScreen
[    46.075] (II)         DownloadFromScreen
[    46.075] (II) RADEON(0): Acceleration enabled
[    46.075] (==) RADEON(0): DPMS enabled
[    46.075] (==) RADEON(0): Silken mouse enabled
[    46.077] (II) RADEON(0): Set up textured video
[    46.077] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    46.077] (II) RADEON(0): [XvMC] Extension initialized.
[    46.077] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    46.087] (--) RandR disabled
[    46.115] (II) SELinux: Disabled on system
[    46.508] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    46.508] (II) AIGLX: enabled GLX_ARB_create_context
[    46.508] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    46.508] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    46.508] (II) AIGLX: enabled GLX_INTEL_swap_event
[    46.508] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    46.508] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    46.508] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    46.508] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    46.508] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    46.510] (II) AIGLX: Loaded and initialized r300
[    46.510] (II) GLX: Initialized DRI2 GL provider for screen 0
[    46.511] (II) RADEON(0): Setting screen physical size to 508 x 285
[    46.782] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event1)
[    46.782] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    46.782] (II) LoadModule: "evdev"
[    46.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.817] (II) Module evdev: vendor="X.Org Foundation"
[    46.817] 	compiled for 1.18.3, module version = 2.10.2
[    46.817] 	Module class: X.Org XInput Driver
[    46.817] 	ABI class: X.Org XInput driver, version 22.1
[    46.817] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    46.817] (**) USB Optical Mouse: always reports core events
[    46.817] (**) evdev: USB Optical Mouse: Device: "/dev/input/event1"
[    46.876] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d81
[    46.876] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    46.876] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    46.876] (--) evdev: USB Optical Mouse: Found relative axes
[    46.876] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    46.876] (II) evdev: USB Optical Mouse: Configuring as mouse
[    46.876] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    46.876] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    46.876] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.876] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.0/usb4/4-1/4-1:1.0/0003:0461:4D81.0001/input/input1/event1"
[    46.876] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 6)
[    46.876] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    46.877] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    46.877] (**) USB Optical Mouse: (accel) acceleration profile 0
[    46.877] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    46.877] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    46.878] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    46.879] (II) No input driver specified, ignoring this device.
[    46.879] (II) This device may have been added with another device file.
[    46.880] (II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event2)
[    46.880] (**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[    46.881] (II) Using input driver 'evdev' for 'Dell Dell Multimedia Pro Keyboard'
[    46.881] (**) Dell Dell Multimedia Pro Keyboard: always reports core events
[    46.881] (**) evdev: Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event2"
[    46.881] (--) evdev: Dell Dell Multimedia Pro Keyboard: Vendor 0x413c Product 0x2011
[    46.881] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found keys
[    46.881] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
[    46.881] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.1/usb5/5-2/5-2.1/5-2.1:1.0/0003:413C:2011.0002/input/input2/event2"
[    46.881] (II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD, id 7)
[    46.881] (**) Option "xkb_rules" "evdev"
[    46.881] (**) Option "xkb_model" "pc105"
[    46.881] (**) Option "xkb_layout" "us"
[    46.883] (II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event3)
[    46.883] (**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[    46.883] (II) Using input driver 'evdev' for 'Dell Dell Multimedia Pro Keyboard'
[    46.884] (**) Dell Dell Multimedia Pro Keyboard: always reports core events
[    46.884] (**) evdev: Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event3"
[    46.884] (--) evdev: Dell Dell Multimedia Pro Keyboard: Vendor 0x413c Product 0x2011
[    46.884] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found absolute axes
[    46.884] (II) evdev: Dell Dell Multimedia Pro Keyboard: Forcing absolute x/y axes to exist.
[    46.884] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found keys
[    46.884] (II) evdev: Dell Dell Multimedia Pro Keyboard: Forcing relative x/y axes to exist.
[    46.884] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as mouse
[    46.884] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
[    46.884] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:04.0/0001:02:0b.1/usb5/5-2/5-2.1/5-2.1:1.1/0003:413C:2011.0003/input/input3/event3"
[    46.884] (II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD, id 8)
[    46.884] (**) Option "xkb_rules" "evdev"
[    46.884] (**) Option "xkb_model" "pc105"
[    46.884] (**) Option "xkb_layout" "us"
[    46.885] (II) evdev: Dell Dell Multimedia Pro Keyboard: initialized for absolute axes.
[    46.885] (**) Dell Dell Multimedia Pro Keyboard: (accel) keeping acceleration scheme 1
[    46.885] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration profile 0
[    46.885] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration factor: 2.000
[    46.885] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration threshold: 4
[    46.891] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    46.891] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    46.891] (II) Using input driver 'evdev' for 'PMU'
[    46.891] (**) PMU: always reports core events
[    46.891] (**) evdev: PMU: Device: "/dev/input/event0"
[    46.892] (--) evdev: PMU: Vendor 0x1 Product 0x1
[    46.892] (--) evdev: PMU: Found keys
[    46.892] (II) evdev: PMU: Configuring as keyboard
[    46.892] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    46.892] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD, id 9)
[    46.892] (**) Option "xkb_rules" "evdev"
[    46.892] (**) Option "xkb_model" "pc105"
[    46.892] (**) Option "xkb_layout" "us"
[   860.060] (II) AIGLX: Suspending AIGLX clients for VT switch
[   887.727] (II) AIGLX: Resuming AIGLX clients after VT switch
[   887.768] (II) RADEON(0): EDID vendor "DEL", prod id 16481
[   887.770] (II) RADEON(0): Using EDID range info for horizontal sync
[   887.770] (II) RADEON(0): Using EDID range info for vertical refresh
[   887.770] (II) RADEON(0): Printing DDC gathered Modelines:
[   887.770] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   887.770] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   887.770] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   887.770] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   887.770] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   887.770] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   887.770] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   887.770] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   887.770] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   887.770] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   887.770] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   887.770] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  2046.200] (II) AIGLX: Suspending AIGLX clients for VT switch
[  3467.225] (II) AIGLX: Resuming AIGLX clients after VT switch
[  3467.268] (II) RADEON(0): EDID vendor "DEL", prod id 16481
[  3467.268] (II) RADEON(0): Using hsync ranges from config file
[  3467.268] (II) RADEON(0): Using vrefresh ranges from config file
[  3467.268] (II) RADEON(0): Printing DDC gathered Modelines:
[  3467.268] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3467.269] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3467.269] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3467.269] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3467.269] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3467.269] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3467.269] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
rican-linux@Lubuntu-G5:~$ 

```

---

### Post by rican-linux on 2016-10-18
So I have also tested this solution on my PowerMac G4 Dual 1.25 Ghz MDD running Debian Stretch. It has Radeon 9000 card (r200). This card always freezes when I try to use hw accleration even when I put the card in pci mode. So this has been great! Also you have compositing using compton with these switches.

```

compton -c -r 16 --backend=xrender --xredner-sync -b

```

Try it and let me know.

---

### Post by ernsteiswuerfel on 2016-10-19
> **rican-linux said:**
> This card always freezes when I try to use hw accleration even when I put the card in pci mode. So this has been great! Also you have compositing using compton with these switches.
```

compton -c -r 16 --backend=xrender --xredner-sync -b

```
Try it and let me know.
Your compton command works and I get the window shadows afterwards. Apart from that no effect.

The point is, with **Option "NoAccel" "True"** in your /etc/xorg.conf you get NO hardware acceleration from the graphics card, because it will be disabled:
```
$ cat /var/log/Xorg.0.log  | grep -i render[    40.154] (WW) RADEON(0): Direct rendering disabled
[    40.236] (EE) AIGLX: reverting to software rendering

```
Means the DRI2-infrastucture is not used to display graphics but the framebuffer. But with DRI2 turned off the Radeon cards no longer freeze when using the intended AGP-x4 or AGP-x8 mode. That's what is causing the "speed boost", because the maximum bandwith for accessing the graphics card is so much faster than plain PCI-mode.

Ideally DRI2 or DRI3 can be used AND the appropriate AGP-mode is autodeteced. Which is normally the case on Radeon cards on x86 PC-boards. And which magically works on your PowerMac G5 7,2 and my PowerBook G4 5,8 but not on other hardware-combiations... Don't know if variations of the Apple U3/U4 northbridge in the different PPC-Macs or specific Radeon cards are to blame but enabling DRI seems a very delicate matter...

---

### Post by rican-linux on 2016-10-20
I am not sure if there is also a software component as well. On my PowerMac if I run Debian the GPU default to PCI mode and turns off hw acceleration. Here is my kernel log so you can see it. There is something that Ubuntu is doing differently that is giving better GPU performance on my PowerMac.

```

root@Debian-G5:/home/rican-linux# journalctl |grep -e kernel
Sep 19 11:29:54 Debian-G5 kernel: Allocated 131072 bytes for 32 pacas at c00000000ffe0000
Sep 19 11:29:54 Debian-G5 kernel: DART table allocated at: c00000007f000000
Sep 19 11:29:54 Debian-G5 kernel: Using PowerMac machine description
Sep 19 11:29:54 Debian-G5 kernel: Page orders: linear mapping = 24, virtual = 12, io = 12, vmemmap = 24
Sep 19 11:29:54 Debian-G5 kernel: cma: Reserved 208 MiB at 0x000000016f000000
Sep 19 11:29:54 Debian-G5 kernel: Found initrd at 0xc000000001b00000:0xc000000002d35000
Sep 19 11:29:54 Debian-G5 kernel: Found U3 memory controller & host bridge @ 0xf8000000 revision: 0xb3
Sep 19 11:29:54 Debian-G5 kernel: Mapped at 0xd000080080000000
Sep 19 11:29:54 Debian-G5 kernel: Found a K2 mac-io controller, rev: 32, mapped at 0xd000080080050000
Sep 19 11:29:54 Debian-G5 kernel: PowerMac motherboard: PowerMac G5
Sep 19 11:29:54 Debian-G5 kernel: DART IOMMU initialized for U3 type chipset
Sep 19 11:29:54 Debian-G5 kernel: bootconsole [udbg0] enabled
Sep 19 11:29:54 Debian-G5 kernel: CPU maps initialized for 1 thread per core
Sep 19 11:29:54 Debian-G5 kernel:  (thread shift is 0)
Sep 19 11:29:54 Debian-G5 kernel: Freed 65536 bytes for unused pacas
Sep 19 11:29:54 Debian-G5 kernel: Starting Linux ppc64 #1 SMP Debian 4.6.4-1 (2016-07-18)
Sep 19 11:29:54 Debian-G5 kernel: -----------------------------------------------------
Sep 19 11:29:54 Debian-G5 kernel: ppc64_pft_size    = 0x0
Sep 19 11:29:54 Debian-G5 kernel: phys_mem_size     = 0x100000000
Sep 19 11:29:54 Debian-G5 kernel: cpu_features      = 0x0804806318100448
Sep 19 11:29:54 Debian-G5 kernel:   possible        = 0x3fffffff18500649
Sep 19 11:29:54 Debian-G5 kernel:   always          = 0x0000000018100040
Sep 19 11:29:54 Debian-G5 kernel: cpu_user_features = 0xdc080000 0x00000000
Sep 19 11:29:54 Debian-G5 kernel: mmu_features      = 0x0c000001
Sep 19 11:29:54 Debian-G5 kernel: firmware_features = 0x0000000000000000
Sep 19 11:29:54 Debian-G5 kernel: htab_address      = 0xc00000017c000000
Sep 19 11:29:54 Debian-G5 kernel: htab_hash_mask    = 0x7ffff
Sep 19 11:29:54 Debian-G5 kernel: -----------------------------------------------------
Sep 19 11:29:54 Debian-G5 kernel: Linux version 4.6.0-1-powerpc64 (debian-kernel@lists.debian.org) (gcc version 5.4.0 20160609 (Debian 5.4.0-6) ) #1 SMP Debian 4.6.4-1 (2016-07-18)
Sep 19 11:29:54 Debian-G5 kernel: Top of RAM: 0x180000000, Total RAM: 0x100000000
Sep 19 11:29:54 Debian-G5 kernel: Memory hole size: 2048MB
Sep 19 11:29:54 Debian-G5 kernel: numa: Initmem setup node 0 [mem 0x00000000-0x17fffffff]
Sep 19 11:29:54 Debian-G5 kernel: numa:   NODE_DATA [mem 0x16efc6100-0x16efcffff]
Sep 19 11:29:54 Debian-G5 kernel: Found U3-AGP PCI host bridge.  Firmware bus number: 240->255
Sep 19 11:29:54 Debian-G5 kernel: PCI host bridge /pci@0,f0000000  ranges:
Sep 19 11:29:54 Debian-G5 kernel:  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
Sep 19 11:29:54 Debian-G5 kernel:   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
Sep 19 11:29:54 Debian-G5 kernel:  MEM 0x00000000a0000000..0x00000000bfffffff -> 0x00000000a0000000 
Sep 19 11:29:54 Debian-G5 kernel: Can't get bus-range for /ht@0,f2000000, assume bus 0
Sep 19 11:29:54 Debian-G5 kernel: Found U3-HT PCI host bridge.  Firmware bus number: 0->239
Sep 19 11:29:54 Debian-G5 kernel: PCI host bridge /ht@0,f2000000 (primary) ranges:
Sep 19 11:29:54 Debian-G5 kernel: via-pmu: Server Mode is disabled
Sep 19 11:29:54 Debian-G5 kernel: PMU driver v2 initialized for Core99, firmware: 0c
Sep 19 11:29:54 Debian-G5 kernel: nvram: Checking bank 0...
Sep 19 11:29:54 Debian-G5 kernel: nvram: gen0=893, gen1=894
Sep 19 11:29:54 Debian-G5 kernel: nvram: Active bank is: 1
Sep 19 11:29:54 Debian-G5 kernel: nvram: OF partition at 0x410
Sep 19 11:29:54 Debian-G5 kernel: nvram: XP partition at 0x1020
Sep 19 11:29:54 Debian-G5 kernel: nvram: NR partition at 0x1120
Sep 19 11:29:54 Debian-G5 kernel: Top of RAM: 0x180000000, Total RAM: 0x100000000
Sep 19 11:29:54 Debian-G5 kernel: Memory hole size: 2048MB
Sep 19 11:29:54 Debian-G5 kernel: Zone ranges:
Sep 19 11:29:54 Debian-G5 kernel:   DMA      [mem 0x0000000000000000-0x000000017fffffff]
Sep 19 11:29:54 Debian-G5 kernel:   DMA32    empty
Sep 19 11:29:54 Debian-G5 kernel:   Normal   empty
Sep 19 11:29:54 Debian-G5 kernel: Movable zone start for each node
Sep 19 11:29:54 Debian-G5 kernel: Early memory node ranges
Sep 19 11:29:54 Debian-G5 kernel:   node   0: [mem 0x0000000000000000-0x000000007fffffff]
Sep 19 11:29:54 Debian-G5 kernel:   node   0: [mem 0x0000000100000000-0x000000017fffffff]
Sep 19 11:29:54 Debian-G5 kernel: Initmem setup node 0 [mem 0x0000000000000000-0x000000017fffffff]
Sep 19 11:29:54 Debian-G5 kernel: On node 0 totalpages: 65536
Sep 19 11:29:54 Debian-G5 kernel:   DMA zone: 64 pages used for memmap
Sep 19 11:29:54 Debian-G5 kernel:   DMA zone: 0 pages reserved
Sep 19 11:29:54 Debian-G5 kernel:   DMA zone: 65536 pages, LIFO batch:1
Sep 19 11:29:54 Debian-G5 kernel: percpu: Embedded 3 pages/cpu @c00000016ee00000 s133912 r0 d62696 u524288
Sep 19 11:29:54 Debian-G5 kernel: pcpu-alloc: s133912 r0 d62696 u524288 alloc=1*1048576
Sep 19 11:29:54 Debian-G5 kernel: pcpu-alloc: [0] 0 1 
Sep 19 11:29:54 Debian-G5 kernel: Built 1 zonelists in Node order, mobility grouping on.  Total pages: 65472
Sep 19 11:29:54 Debian-G5 kernel: Policy zone: DMA
Sep 19 11:29:54 Debian-G5 kernel: Kernel command line: root=UUID=aeca9a67-31d7-4c4b-a0f8-4db328b33305  
Sep 19 11:29:54 Debian-G5 kernel: PID hash table entries: 4096 (order: -1, 32768 bytes)
Sep 19 11:29:54 Debian-G5 kernel: Sorting __ex_table...
Sep 19 11:29:54 Debian-G5 kernel: Memory: 3847232K/4194304K available (8320K kernel code, 1920K rwdata, 1920K rodata, 1024K init, 2068K bss, 134080K reserved, 212992K cma-reserved)
Sep 19 11:29:54 Debian-G5 kernel: Hierarchical RCU implementation.
Sep 19 11:29:54 Debian-G5 kernel:         Build-time adjustment of leaf fanout to 64.
Sep 19 11:29:54 Debian-G5 kernel:         RCU restricting CPUs from NR_CPUS=32 to nr_cpu_ids=2.
Sep 19 11:29:54 Debian-G5 kernel: RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=2
Sep 19 11:29:54 Debian-G5 kernel: NR_IRQS:512 nr_irqs:512 16
Sep 19 11:29:54 Debian-G5 kernel: mpic: Resetting
Sep 19 11:29:54 Debian-G5 kernel: mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 2 CPUs
Sep 19 11:29:54 Debian-G5 kernel: mpic: ISU size: 120, shift: 7, mask: 7f
Sep 19 11:29:54 Debian-G5 kernel: mpic: Initializing for 120 sources
Sep 19 11:29:54 Debian-G5 kernel: mpic: Resetting
Sep 19 11:29:54 Debian-G5 kernel: mpic: Setting up MPIC " MPIC 2   " version 1.2 at f8040000, max 2 CPUs
Sep 19 11:29:54 Debian-G5 kernel: mpic: ISU size: 120, shift: 7, mask: 7f
Sep 19 11:29:54 Debian-G5 kernel: mpic: Initializing for 120 sources
Sep 19 11:29:54 Debian-G5 kernel: /u3@0,f8000000/mpic@f8040000: hooking up to IRQ 56
Sep 19 11:29:54 Debian-G5 kernel: time_init: decrementer frequency = 33.333333 MHz
Sep 19 11:29:54 Debian-G5 kernel: time_init: processor frequency   = 2000.000000 MHz
Sep 19 11:29:54 Debian-G5 kernel: clocksource: timebase: mask: 0xffffffffffffffff max_cycles: 0x7b00c4bad, max_idle_ns: 440795202744 ns
Sep 19 11:29:54 Debian-G5 kernel: clocksource: timebase mult[1e000005] shift[24] registered
Sep 19 11:29:54 Debian-G5 kernel: clockevent: decrementer mult[8888887] shift[32] cpu[0]
Sep 19 11:29:54 Debian-G5 kernel: Console: colour dummy device 80x25
Sep 19 11:29:54 Debian-G5 kernel: console [tty0] enabled
Sep 19 11:29:54 Debian-G5 kernel: bootconsole [udbg0] disabled
Sep 19 11:29:54 Debian-G5 kernel: pid_max: default: 32768 minimum: 301
Sep 19 11:29:54 Debian-G5 kernel: Security Framework initialized
Sep 19 11:29:54 Debian-G5 kernel: Yama: disabled by default; enable with sysctl kernel.yama.*
Sep 19 11:29:54 Debian-G5 kernel: AppArmor: AppArmor disabled by boot time parameter
Sep 19 11:29:54 Debian-G5 kernel: Dentry cache hash table entries: 524288 (order: 6, 4194304 bytes)
Sep 19 11:29:54 Debian-G5 kernel: Inode-cache hash table entries: 262144 (order: 5, 2097152 bytes)
Sep 19 11:29:54 Debian-G5 kernel: Mount-cache hash table entries: 8192 (order: 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: Mountpoint-cache hash table entries: 8192 (order: 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: Disabling memory control group subsystem
Sep 19 11:29:54 Debian-G5 kernel: ftrace: allocating 22126 entries in 9 pages
Sep 19 11:29:54 Debian-G5 kernel: PowerMac SMP probe found 2 cpus
Sep 19 11:29:54 Debian-G5 kernel: KeyWest i2c @0xf8001003 irq 42 /u3@0,f8000000/i2c@f8001000
Sep 19 11:29:54 Debian-G5 kernel:  channel 0 bus <multibus>
Sep 19 11:29:54 Debian-G5 kernel:  channel 1 bus <multibus>
Sep 19 11:29:54 Debian-G5 kernel: KeyWest i2c @0x80018000 irq 26 /ht@0,f2000000/pci@3/mac-io@7/i2c@18000
Sep 19 11:29:54 Debian-G5 kernel:  channel 0 bus <multibus>
Sep 19 11:29:54 Debian-G5 kernel: PMU i2c /ht@0,f2000000/pci@3/mac-io@7/via-pmu@16000/pmu-i2c
Sep 19 11:29:54 Debian-G5 kernel:  channel 1 bus <multibus>
Sep 19 11:29:54 Debian-G5 kernel:  channel 2 bus <multibus>
Sep 19 11:29:54 Debian-G5 kernel: Processor timebase sync using Cypress i2c clock
Sep 19 11:29:54 Debian-G5 kernel: mpic: requesting IPIs...
Sep 19 11:29:54 Debian-G5 kernel: PPC970/FX/MP performance monitor hardware support registered
Sep 19 11:29:54 Debian-G5 kernel: Brought up 2 CPUs
Sep 19 11:29:54 Debian-G5 kernel: devtmpfs: initialized
Sep 19 11:29:54 Debian-G5 kernel: EEH: devices created
Sep 19 11:29:54 Debian-G5 kernel: clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Sep 19 11:29:54 Debian-G5 kernel: NET: Registered protocol family 16
Sep 19 11:29:54 Debian-G5 kernel: eeh_init: Platform EEH operation not found
Sep 19 11:29:54 Debian-G5 kernel: IBM eBus Device Driver
Sep 19 11:29:54 Debian-G5 kernel: cpuidle: using governor ladder
Sep 19 11:29:54 Debian-G5 kernel: cpuidle: using governor menu
Sep 19 11:29:54 Debian-G5 kernel: PCI: Probing PCI hardware
Sep 19 11:29:54 Debian-G5 kernel: PCI host bridge to bus 0000:f0
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: root bus resource [io  0x10000-0x80ffff] (bus address [0x0000-0x7fffff])
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: root bus resource [mem 0xf1000000-0xf1ffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: root bus resource [mem 0xa0000000-0xbfffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: root bus resource [bus f0-ff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: busn_res: [bus f0-ff] end is updated to ff
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:0b.0: [106b:004b] type 00 class 0x060000
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: [1002:4150] type 00 class 0x030000
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: reg 0x14: [io  0x10400-0x104ff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: reg 0x18: [mem 0xa0000000-0xa000ffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: reg 0x30: [mem 0xa0020000-0xa003ffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0000:f0:10.0: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: IOMMU table initialized, virtual merging enabled
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: busn_res: [bus f0-ff] end is updated to f0
Sep 19 11:29:54 Debian-G5 kernel: PCI host bridge to bus 0001:00
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: root bus resource [io  0x820000-0xc1ffff] (bus address [0x0000-0x3fffff])
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: root bus resource [mem 0xfa000000-0xffffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: root bus resource [mem 0x80000000-0x9fffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: root bus resource [mem 0xc0000000-0xefffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: root bus resource [bus 00-ef]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: busn_res: [bus 00-ef] end is updated to ff
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:00.0: [106b:004a] type 00 class 0x060000
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:01.0: [1022:7450] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0: [1022:7450] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0: [106b:0045] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0: [106b:0046] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0: [106b:0047] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0: [106b:0048] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0: [106b:0049] type 01 class 0x060400
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:01.0: PCI bridge to [bus 06]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: [8086:1229] type 00 class 0x020000
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: reg 0x10: [mem 0x90000000-0x90000fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: reg 0x14: [io  0x820000-0x82003f]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: reg 0x18: [mem 0x90200000-0x902fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: reg 0x30: [mem 0x90100000-0x901fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0: PCI bridge to [bus 07]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0:   bridge window [io  0x820000-0x820fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0:   bridge window [mem 0x90000000-0x902fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:07.0: [106b:0041] type 00 class 0xff0000
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:07.0: reg 0x10: [mem 0x80000000-0x8007ffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:08.0: [106b:0040] type 00 class 0x0c0310
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:08.0: reg 0x10: [mem 0x80081000-0x80081fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:09.0: [106b:0040] type 00 class 0x0c0310
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:09.0: reg 0x10: [mem 0x80080000-0x80080fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0: PCI bridge to [bus 01]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0:   bridge window [mem 0x80000000-0x800fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0:   bridge window [mem 0x00000000-0x000fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.0: [1033:0035] type 00 class 0x0c0310
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.0: reg 0x10: [mem 0x80102000-0x80102fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.0: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.1: [1033:0035] type 00 class 0x0c0310
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.1: reg 0x10: [mem 0x80101000-0x80101fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.1: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.2: [1033:00e0] type 00 class 0x0c0320
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.2: reg 0x10: [mem 0x80100000-0x801000ff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.2: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.2: PME# supported from D0 D1 D2 D3hot D3cold
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0: PCI bridge to [bus 02]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0:   bridge window [mem 0x80100000-0x801fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0:   bridge window [mem 0x00000000-0x000fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0d.0: [106b:0043] type 00 class 0xff0000
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0d.0: reg 0x10: [mem 0x80204000-0x80207fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0e.0: [106b:0042] type 00 class 0x0c0010
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0e.0: reg 0x10: [mem 0x80200000-0x80200fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0e.0: supports D1 D2
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:03:0e.0: PME# supported from D0 D1 D2 D3hot
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0: PCI bridge to [bus 03]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0:   bridge window [mem 0x80200000-0x802fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0:   bridge window [mem 0x00000000-0x000fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:04:0f.0: [106b:004c] type 00 class 0x020000
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:04:0f.0: reg 0x10: [mem 0x80400000-0x805fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:04:0f.0: reg 0x30: [mem 0x80300000-0x803fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0: PCI bridge to [bus 04]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0:   bridge window [mem 0x80300000-0x805fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0:   bridge window [mem 0x00000000-0x000fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: [1166:0240] type 00 class 0x01018f
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x10: [io  0x820000-0x820007]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x14: [io  0x820000-0x820003]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x18: [io  0x820000-0x820007]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x1c: [io  0x820000-0x820003]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x20: [io  0x820000-0x82000f]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:05:0c.0: reg 0x24: [mem 0x80600000-0x80601fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0: PCI bridge to [bus 05]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0:   bridge window [mem 0x80600000-0x806fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0:   bridge window [mem 0x00000000-0x000fffff pref]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: busn_res: [bus 00-ff] end is updated to 07
Sep 19 11:29:54 Debian-G5 kernel: PCI 0000:f0 Cannot reserve Legacy IO [io  0x10000-0x10fff]
Sep 19 11:29:54 Debian-G5 kernel: PCI 0001:00 Cannot reserve Legacy IO [io  0x820000-0x820fff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: resource 4 [io  0x10000-0x80ffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: resource 5 [mem 0xf1000000-0xf1ffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0000:f0: resource 6 [mem 0xa0000000-0xbfffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:01.0: PCI bridge to [bus 06]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:07:04.0: BAR 1: assigned [io  0x820000-0x82003f]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0: PCI bridge to [bus 07]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0:   bridge window [io  0x820000-0x820fff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0:   bridge window [mem 0x90000000-0x902fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0: PCI bridge to [bus 01]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:03.0:   bridge window [mem 0x80000000-0x800fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0: PCI bridge to [bus 02]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:04.0:   bridge window [mem 0x80100000-0x801fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0: PCI bridge to [bus 03]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:05.0:   bridge window [mem 0x80200000-0x802fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0: PCI bridge to [bus 04]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:06.0:   bridge window [mem 0x80300000-0x805fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0: PCI bridge to [bus 05]
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:07.0:   bridge window [mem 0x80600000-0x806fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: resource 4 [io  0x820000-0xc1ffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: resource 5 [mem 0xfa000000-0xffffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: resource 6 [mem 0x80000000-0x9fffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:00: resource 7 [mem 0xc0000000-0xefffffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:07: resource 0 [io  0x820000-0x820fff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:07: resource 1 [mem 0x90000000-0x902fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:01: resource 1 [mem 0x80000000-0x800fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:02: resource 1 [mem 0x80100000-0x801fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:03: resource 1 [mem 0x80200000-0x802fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:04: resource 1 [mem 0x80300000-0x805fffff]
Sep 19 11:29:54 Debian-G5 kernel: pci_bus 0001:05: resource 1 [mem 0x80600000-0x806fffff]
Sep 19 11:29:54 Debian-G5 kernel: PCI: Probing PCI hardware done
Sep 19 11:29:54 Debian-G5 kernel: HugeTLB registered 16 MB page size, pre-allocated 0 pages
Sep 19 11:29:54 Debian-G5 kernel: vgaarb: device added: PCI:0000:f0:10.0,decodes=io+mem,owns=mem,locks=none
Sep 19 11:29:54 Debian-G5 kernel: vgaarb: loaded
Sep 19 11:29:54 Debian-G5 kernel: vgaarb: bridge control possible 0000:f0:10.0
Sep 19 11:29:54 Debian-G5 kernel: SCSI subsystem initialized
Sep 19 11:29:54 Debian-G5 kernel: libata version 3.00 loaded.
Sep 19 11:29:54 Debian-G5 kernel: clocksource: Switched to clocksource timebase
Sep 19 11:29:54 Debian-G5 kernel: VFS: Disk quotas dquot_6.6.0
Sep 19 11:29:54 Debian-G5 kernel: VFS: Dquot-cache hash table entries: 8192 (order 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: NET: Registered protocol family 2
Sep 19 11:29:54 Debian-G5 kernel: TCP established hash table entries: 32768 (order: 2, 262144 bytes)
Sep 19 11:29:54 Debian-G5 kernel: TCP bind hash table entries: 32768 (order: 3, 524288 bytes)
Sep 19 11:29:54 Debian-G5 kernel: TCP: Hash tables configured (established 32768 bind 32768)
Sep 19 11:29:54 Debian-G5 kernel: UDP hash table entries: 2048 (order: 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: UDP-Lite hash table entries: 2048 (order: 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: NET: Registered protocol family 1
Sep 19 11:29:54 Debian-G5 kernel: PCI: CLS mismatch (32 != 64), using 128 bytes
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:01.0: MSI quirk detected; subordinate MSI disabled
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:01.0: AMD8131 rev 12 detected; disabling PCI-X MMRBC
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0: MSI quirk detected; subordinate MSI disabled
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:00:02.0: AMD8131 rev 12 detected; disabling PCI-X MMRBC
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:08.0: enabling device (0000 -> 0002)
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:01:09.0: enabling device (0000 -> 0002)
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.0: enabling device (0000 -> 0002)
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.1: enabling device (0000 -> 0002)
Sep 19 11:29:54 Debian-G5 kernel: pci 0001:02:0b.2: enabling device (0004 -> 0006)
Sep 19 11:29:54 Debian-G5 kernel: Unpacking initramfs...
Sep 19 11:29:54 Debian-G5 kernel: Freeing initrd memory: 18624K (c000000001b00000 - c000000002d30000)
Sep 19 11:29:54 Debian-G5 kernel: Hypercall H_BEST_ENERGY not supported
Sep 19 11:29:54 Debian-G5 kernel: futex hash table entries: 512 (order: 0, 65536 bytes)
Sep 19 11:29:54 Debian-G5 kernel: audit: initializing netlink subsys (disabled)
Sep 19 11:29:54 Debian-G5 kernel: audit: type=2000 audit(1474309786.143:1): initialized
Sep 19 11:29:54 Debian-G5 kernel: Initialise system trusted keyring
Sep 19 11:29:54 Debian-G5 kernel: workingset: timestamp_bits=36 max_order=16 bucket_order=0
Sep 19 11:29:54 Debian-G5 kernel: zbud: loaded
Sep 19 11:29:54 Debian-G5 kernel: Key type asymmetric registered
Sep 19 11:29:54 Debian-G5 kernel: Asymmetric key parser 'x509' registered
Sep 19 11:29:54 Debian-G5 kernel: Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Sep 19 11:29:54 Debian-G5 kernel: io scheduler noop registered
Sep 19 11:29:54 Debian-G5 kernel: io scheduler deadline registered
Sep 19 11:29:54 Debian-G5 kernel: io scheduler cfq registered (default)
Sep 19 11:29:54 Debian-G5 kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 19 11:29:54 Debian-G5 kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 19 11:29:54 Debian-G5 kernel: Using unsupported 1920x1080 ATY,Simone_A at b8008000, depth=8, pitch=2048
Sep 19 11:29:54 Debian-G5 kernel: Console: switching to colour frame buffer device 240x67
Sep 19 11:29:54 Debian-G5 kernel: fb0: Open Firmware frame buffer device on /pci@0,f0000000/ATY,SimoneParent@10/ATY,Simone_A@0
Sep 19 11:29:54 Debian-G5 kernel: Using unsupported 640x480 ATY,Simone_B at b2008000, depth=8, pitch=768
Sep 19 11:29:54 Debian-G5 kernel: checking generic (b8008000 21c000) vs hw (b2008000 5a000)
Sep 19 11:29:54 Debian-G5 kernel: fb1: Open Firmware frame buffer device on /pci@0,f0000000/ATY,SimoneParent@10/ATY,Simone_B@1
Sep 19 11:29:54 Debian-G5 kernel: Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
Sep 19 11:29:54 Debian-G5 kernel: pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Sep 19 11:29:54 Debian-G5 kernel: Linux agpgart interface v0.103
Sep 19 11:29:54 Debian-G5 kernel: agpgart-uninorth 0000:f0:0b.0: Apple U3 chipset
Sep 19 11:29:54 Debian-G5 kernel: agpgart-uninorth 0000:f0:0b.0: configuring for size idx: 64
Sep 19 11:29:54 Debian-G5 kernel: agpgart-uninorth 0000:f0:0b.0: AGP aperture is 256M @ 0x0
Sep 19 11:29:54 Debian-G5 kernel: MacIO PCI driver attached to K2 chipset
Sep 19 11:29:54 Debian-G5 kernel: 0.00013020:ch-a: ttyPZ0 at MMIO 0x80013020 (irq = 22, base_baud = 230400) is a Z85c30 ESCC - Serial port
Sep 19 11:29:54 Debian-G5 kernel: 0.00013000:ch-b: ttyPZ1 at MMIO 0x80013000 (irq = 23, base_baud = 230400) is a Z85c30 ESCC - Serial port
Sep 19 11:29:54 Debian-G5 kernel: pata-pci-macio 0001:03:0d.0: enabling device (0014 -> 0016)
Sep 19 11:29:54 Debian-G5 kernel: pata-pci-macio 0001:03:0d.0: Activating pata-macio chipset K2 ATA-6, Apple bus ID 3
Sep 19 11:29:54 Debian-G5 kernel: scsi host0: pata_macio
Sep 19 11:29:54 Debian-G5 kernel: ata1: PATA max UDMA/100 irq 39
Sep 19 11:29:54 Debian-G5 kernel: mousedev: PS/2 mouse device common for all mice
Sep 19 11:29:54 Debian-G5 kernel: rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
Sep 19 11:29:54 Debian-G5 kernel: PowerMac i2c bus pmu 2 registered
Sep 19 11:29:54 Debian-G5 kernel: PowerMac i2c bus pmu 1 registered
Sep 19 11:29:54 Debian-G5 kernel: PowerMac i2c bus mac-io 0 registered
Sep 19 11:29:54 Debian-G5 kernel: i2c i2c-2: No i2c address for /ht@0,f2000000/pci@3/mac-io@7/i2c@18000/i2c-modem
Sep 19 11:29:54 Debian-G5 kernel: PowerMac i2c bus u3 1 registered
Sep 19 11:29:54 Debian-G5 kernel: i2c i2c-3: i2c-powermac: modalias failure on /u3@0,f8000000/i2c@f8001000/cereal@1c0
Sep 19 11:29:54 Debian-G5 kernel: PowerMac i2c bus u3 0 registered
Sep 19 11:29:54 Debian-G5 kernel: Registering G5 CPU frequency driver
Sep 19 11:29:54 Debian-G5 kernel: Frequency method: i2c/pfunc, Voltage method: i2c/pfunc
Sep 19 11:29:54 Debian-G5 kernel: Low: 1304 Mhz, High: 2000 Mhz, Cur: 2000 MHz
Sep 19 11:29:54 Debian-G5 kernel: ledtrig-cpu: registered to indicate activity on CPUs
Sep 19 11:29:54 Debian-G5 kernel: NET: Registered protocol family 10
Sep 19 11:29:54 Debian-G5 kernel: mip6: Mobile IPv6
Sep 19 11:29:54 Debian-G5 kernel: NET: Registered protocol family 17
Sep 19 11:29:54 Debian-G5 kernel: mpls_gso: MPLS GSO support
Sep 19 11:29:54 Debian-G5 kernel: PM: Registered nosave memory: [mem 0x7f000000-0x7fffffff]
Sep 19 11:29:54 Debian-G5 kernel: registered taskstats version 1
Sep 19 11:29:54 Debian-G5 kernel: Loading compiled-in X.509 certificates
Sep 19 11:29:54 Debian-G5 kernel: alg: No test for pkcs1pad(rsa,sha256) (pkcs1pad(rsa-generic,sha256))
Sep 19 11:29:54 Debian-G5 kernel: Loaded X.509 cert 'Debian Project: Ben Hutchings: 008a018dca80932630'
Sep 19 11:29:54 Debian-G5 kernel: zswap: loaded using pool lzo/zbud
Sep 19 11:29:54 Debian-G5 kernel: input: PMU as /devices/virtual/input/input0
Sep 19 11:29:54 Debian-G5 kernel: rtc-generic rtc-generic: setting system clock to 2016-09-19 18:29:47 UTC (1474309787)
Sep 19 11:29:54 Debian-G5 kernel: PM: Hibernation image not present or could not be loaded.
Sep 19 11:29:54 Debian-G5 kernel: ata1.00: ATAPI: HL-DT-ST RW/DVD GCC-4480B, 1.03, max UDMA/33
Sep 19 11:29:54 Debian-G5 kernel: ata1.00: configured for UDMA/33
Sep 19 11:29:54 Debian-G5 kernel: blk_queue_max_segment_size: set to minimum 65536
Sep 19 11:29:54 Debian-G5 kernel: scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4480B 1.03 PQ: 0 ANSI: 5
Sep 19 11:29:54 Debian-G5 kernel: ata1.00: K2/Shasta alignment limits applied
Sep 19 11:29:54 Debian-G5 kernel: Freeing unused kernel memory: 1024K (c000000000a10000 - c000000000b10000)
Sep 19 11:29:54 Debian-G5 kernel: This architecture does not have kernel memory protection.
Sep 19 11:29:54 Debian-G5 kernel: random: systemd-udevd urandom read with 10 bits of entropy available
Sep 19 11:29:54 Debian-G5 kernel: mii: module verification failed: signature and/or required key missing - tainting kernel
Sep 19 11:29:54 Debian-G5 kernel: e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Sep 19 11:29:54 Debian-G5 kernel: e100: Copyright(c) 1999-2006 Intel Corporation
Sep 19 11:29:54 Debian-G5 kernel: usbcore: registered new interface driver usbfs
Sep 19 11:29:54 Debian-G5 kernel: usbcore: registered new interface driver hub
Sep 19 11:29:54 Debian-G5 kernel: usbcore: registered new device driver usb
Sep 19 11:29:54 Debian-G5 kernel: ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 19 11:29:54 Debian-G5 kernel: ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 19 11:29:54 Debian-G5 kernel: ehci-pci: EHCI PCI platform driver
Sep 19 11:29:54 Debian-G5 kernel: ehci-pci 0001:02:0b.2: EHCI Host Controller
Sep 19 11:29:54 Debian-G5 kernel: ehci-pci 0001:02:0b.2: new USB bus registered, assigned bus number 1
Sep 19 11:29:54 Debian-G5 kernel: ehci-pci 0001:02:0b.2: irq 63, io mem 0x80100000
Sep 19 11:29:54 Debian-G5 kernel: ehci-pci 0001:02:0b.2: USB 2.0 started, EHCI 1.00
Sep 19 11:29:54 Debian-G5 kernel: usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Sep 19 11:29:54 Debian-G5 kernel: usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 19 11:29:54 Debian-G5 kernel: usb usb1: Product: EHCI Host Controller
Sep 19 11:29:54 Debian-G5 kernel: usb usb1: Manufacturer: Linux 4.6.0-1-powerpc64 ehci_hcd
Sep 19 11:29:54 Debian-G5 kernel: usb usb1: SerialNumber: 0001:02:0b.2
Sep 19 11:29:54 Debian-G5 kernel: sr 0:0:0:0: [sr0] scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Sep 19 11:29:54 Debian-G5 kernel: cdrom: Uniform CD-ROM driver Revision: 3.20
Sep 19 11:29:54 Debian-G5 kernel: sr 0:0:0:0: Attached scsi CD-ROM sr0
Sep 19 11:29:54 Debian-G5 kernel: hub 1-0:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 1-0:1.0: 5 ports detected
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci: OHCI PCI platform driver
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:08.0: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:08.0: new USB bus registered, assigned bus number 2
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:08.0: irq 27, io mem 0x80081000
Sep 19 11:29:54 Debian-G5 kernel: sungem.c:v1.0 David S. Miller <davem@redhat.com>
Sep 19 11:29:54 Debian-G5 kernel: gem 0001:04:0f.0 eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:bb:30:6c
Sep 19 11:29:54 Debian-G5 kernel: firewire_ohci 0001:03:0e.0: enabling device (0000 -> 0002)
Sep 19 11:29:54 Debian-G5 kernel: sata_svw 0001:05:0c.0: version 2.3
Sep 19 11:29:54 Debian-G5 kernel: scsi host1: sata_svw
Sep 19 11:29:54 Debian-G5 kernel: scsi host2: sata_svw
Sep 19 11:29:54 Debian-G5 kernel: firewire_ohci 0001:03:0e.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
Sep 19 11:29:54 Debian-G5 kernel: scsi host3: sata_svw
Sep 19 11:29:54 Debian-G5 kernel: usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Sep 19 11:29:54 Debian-G5 kernel: usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 19 11:29:54 Debian-G5 kernel: usb usb2: Product: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: usb usb2: Manufacturer: Linux 4.6.0-1-powerpc64 ohci_hcd
Sep 19 11:29:54 Debian-G5 kernel: usb usb2: SerialNumber: 0001:01:08.0
Sep 19 11:29:54 Debian-G5 kernel: scsi host4: sata_svw
Sep 19 11:29:54 Debian-G5 kernel: ata2: SATA max UDMA/133 mmio m8192@0x80600000 port 0x80600000 irq 16
Sep 19 11:29:54 Debian-G5 kernel: ata3: SATA max UDMA/133 mmio m8192@0x80600000 port 0x80600100 irq 16
Sep 19 11:29:54 Debian-G5 kernel: ata4: SATA max UDMA/133 mmio m8192@0x80600000 port 0x80600200 irq 16
Sep 19 11:29:54 Debian-G5 kernel: ata5: SATA max UDMA/133 mmio m8192@0x80600000 port 0x80600300 irq 16
Sep 19 11:29:54 Debian-G5 kernel: hub 2-0:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 2-0:1.0: 2 ports detected
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:09.0: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:09.0: new USB bus registered, assigned bus number 3
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:01:09.0: irq 28, io mem 0x80080000
Sep 19 11:29:54 Debian-G5 kernel: usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Sep 19 11:29:54 Debian-G5 kernel: usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 19 11:29:54 Debian-G5 kernel: usb usb3: Product: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: usb usb3: Manufacturer: Linux 4.6.0-1-powerpc64 ohci_hcd
Sep 19 11:29:54 Debian-G5 kernel: usb usb3: SerialNumber: 0001:01:09.0
Sep 19 11:29:54 Debian-G5 kernel: hub 3-0:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 3-0:1.0: 2 ports detected
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.0: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.0: new USB bus registered, assigned bus number 4
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.0: irq 63, io mem 0x80102000
Sep 19 11:29:54 Debian-G5 kernel: usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Sep 19 11:29:54 Debian-G5 kernel: usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 19 11:29:54 Debian-G5 kernel: usb usb4: Product: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: usb usb4: Manufacturer: Linux 4.6.0-1-powerpc64 ohci_hcd
Sep 19 11:29:54 Debian-G5 kernel: usb usb4: SerialNumber: 0001:02:0b.0
Sep 19 11:29:54 Debian-G5 kernel: hub 4-0:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 4-0:1.0: 3 ports detected
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.1: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.1: new USB bus registered, assigned bus number 5
Sep 19 11:29:54 Debian-G5 kernel: ohci-pci 0001:02:0b.1: irq 63, io mem 0x80101000
Sep 19 11:29:54 Debian-G5 kernel: gem 0001:04:0f.0 enP1p4s15f0: renamed from eth0
Sep 19 11:29:54 Debian-G5 kernel: ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep 19 11:29:54 Debian-G5 kernel: usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Sep 19 11:29:54 Debian-G5 kernel: usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 19 11:29:54 Debian-G5 kernel: usb usb5: Product: OHCI PCI host controller
Sep 19 11:29:54 Debian-G5 kernel: usb usb5: Manufacturer: Linux 4.6.0-1-powerpc64 ohci_hcd
Sep 19 11:29:54 Debian-G5 kernel: usb usb5: SerialNumber: 0001:02:0b.1
Sep 19 11:29:54 Debian-G5 kernel: hub 5-0:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 5-0:1.0: 2 ports detected
Sep 19 11:29:54 Debian-G5 kernel: ata2.00: ATA-6: ST3160023AS, 3.05, max UDMA/133
Sep 19 11:29:54 Debian-G5 kernel: ata2.00: 312581808 sectors, multi 16: LBA48 
Sep 19 11:29:54 Debian-G5 kernel: ata2.00: configured for UDMA/133
Sep 19 11:29:54 Debian-G5 kernel: scsi 1:0:0:0: Direct-Access     ATA      ST3160023AS      3.05 PQ: 0 ANSI: 5
Sep 19 11:29:54 Debian-G5 kernel: e100 0001:07:04.0: enabling device (0004 -> 0007)
Sep 19 11:29:54 Debian-G5 kernel: firewire_core 0001:03:0e.0: created device fw0: GUID 000a95fffebb306c, S800
Sep 19 11:29:54 Debian-G5 kernel: e100 0001:07:04.0 eth0: addr 0x90000000, irq 54, MAC addr 00:0e:0c:07:b3:47
Sep 19 11:29:54 Debian-G5 kernel: e100 0001:07:04.0 enP1p7s4: renamed from eth0
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2: new full-speed USB device number 2 using ohci-pci
Sep 19 11:29:54 Debian-G5 kernel: ata3: SATA link down (SStatus 4 SControl 300)
Sep 19 11:29:54 Debian-G5 kernel: usb 4-1: new low-speed USB device number 2 using ohci-pci
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2: New USB device found, idVendor=413c, idProduct=1005
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2: Product: Dell Multimedia Pro Keyboard Hub
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2: Manufacturer: Dell
Sep 19 11:29:54 Debian-G5 kernel: hub 5-2:1.0: USB hub found
Sep 19 11:29:54 Debian-G5 kernel: hub 5-2:1.0: 3 ports detected
Sep 19 11:29:54 Debian-G5 kernel: usb 4-1: New USB device found, idVendor=0461, idProduct=4d81
Sep 19 11:29:54 Debian-G5 kernel: usb 4-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Sep 19 11:29:54 Debian-G5 kernel: usb 4-1: Product: USB Optical Mouse
Sep 19 11:29:54 Debian-G5 kernel: hidraw: raw HID events driver (C) Jiri Kosina
Sep 19 11:29:54 Debian-G5 kernel: ata4: SATA link down (SStatus 4 SControl 300)
Sep 19 11:29:54 Debian-G5 kernel: usbcore: registered new interface driver usbhid
Sep 19 11:29:54 Debian-G5 kernel: usbhid: USB HID core driver
Sep 19 11:29:54 Debian-G5 kernel: input: USB Optical Mouse as /devices/pci0001:00/0001:00:04.0/0001:02:0b.0/usb4/4-1/4-1:1.0/0003:0461:4D81.0001/input/input1
Sep 19 11:29:54 Debian-G5 kernel: hid-generic 0003:0461:4D81.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0001:02:0b.0-1/input0
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2.1: new low-speed USB device number 3 using ohci-pci
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2.1: New USB device found, idVendor=413c, idProduct=2011
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2.1: Product: Dell Multimedia Pro Keyboard
Sep 19 11:29:54 Debian-G5 kernel: usb 5-2.1: Manufacturer: Dell
Sep 19 11:29:54 Debian-G5 kernel: input: Dell Dell Multimedia Pro Keyboard as /devices/pci0001:00/0001:00:04.0/0001:02:0b.1/usb5/5-2/5-2.1/5-2.1:1.0/0003:413C:2011.0002/input/input2
Sep 19 11:29:54 Debian-G5 kernel: hid-generic 0003:413C:2011.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell Multimedia Pro Keyboard] on usb-0001:02:0b.1-2.1/input0
Sep 19 11:29:54 Debian-G5 kernel: ata5: SATA link down (SStatus 4 SControl 300)
Sep 19 11:29:54 Debian-G5 kernel: input: Dell Dell Multimedia Pro Keyboard as /devices/pci0001:00/0001:00:04.0/0001:02:0b.1/usb5/5-2/5-2.1/5-2.1:1.1/0003:413C:2011.0003/input/input3
Sep 19 11:29:54 Debian-G5 kernel: sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Sep 19 11:29:54 Debian-G5 kernel: sd 1:0:0:0: [sda] Write Protect is off
Sep 19 11:29:54 Debian-G5 kernel: sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 19 11:29:54 Debian-G5 kernel: sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 11:29:54 Debian-G5 kernel:  sda: [mac] sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10
Sep 19 11:29:54 Debian-G5 kernel: sd 1:0:0:0: [sda] Attached SCSI disk
Sep 19 11:29:54 Debian-G5 kernel: hid-generic 0003:413C:2011.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell Multimedia Pro Keyboard] on usb-0001:02:0b.1-2.1/input1
Sep 19 11:29:54 Debian-G5 kernel: PM: Starting manual resume from disk
Sep 19 11:29:54 Debian-G5 kernel: PM: Hibernation image partition 8:3 present
Sep 19 11:29:54 Debian-G5 kernel: PM: Looking for hibernation image.
Sep 19 11:29:54 Debian-G5 kernel: PM: Image not found (code -22)
Sep 19 11:29:54 Debian-G5 kernel: PM: Hibernation image not present or could not be loaded.
Sep 19 11:29:54 Debian-G5 kernel: EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Sep 19 11:29:54 Debian-G5 kernel: random: nonblocking pool is initialized
Sep 19 11:29:54 Debian-G5 kernel: ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 19 11:29:54 Debian-G5 systemd[1]: Starting Create list of required static device nodes for the current kernel...
Sep 19 11:29:54 Debian-G5 kernel: lp: driver loaded but no devices found
Sep 19 11:29:54 Debian-G5 kernel: EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Sep 19 11:29:54 Debian-G5 systemd[1]: Started Create list of required static device nodes for the current kernel.
Sep 19 11:29:55 Debian-G5 kernel: i2c /dev entries driver
Sep 19 11:29:55 Debian-G5 kernel: [drm] Initialized drm 1.1.0 20060810
Sep 19 11:29:56 Debian-G5 kernel: sr 0:0:0:0: Attached scsi generic sg0 type 5
Sep 19 11:29:56 Debian-G5 kernel: sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 19 11:29:56 Debian-G5 kernel: windfarm: Initializing for desktop G5 with 2 chips
Sep 19 11:29:56 Debian-G5 kernel: windfarm: CPUs control loops started.
Sep 19 11:29:56 Debian-G5 kernel: wf_pm72: Backside control loop started.
Sep 19 11:29:56 Debian-G5 kernel: wf_pm72: Drive bay control loop started.
Sep 19 11:29:56 Debian-G5 kernel: snd-powermac no longer handles any machines with a layout-id property in the device-tree, use snd-aoa.
Sep 19 11:29:56 Debian-G5 kernel: Attempt to iounmap early bolted mapping at 0x          (null)
Sep 19 11:29:56 Debian-G5 kernel: Attempt to iounmap early bolted mapping at 0x          (null)
Sep 19 11:29:56 Debian-G5 kernel: Attempt to iounmap early bolted mapping at 0x          (null)
Sep 19 11:29:56 Debian-G5 kernel: Attempt to iounmap early bolted mapping at 0x          (null)
Sep 19 11:29:56 Debian-G5 kernel: Attempt to iounmap early bolted mapping at 0x          (null)
Sep 19 11:29:56 Debian-G5 kernel: snd-aoa-codec-tas: tas found, addr 0x35 on /ht@0,f2000000/pci@3/mac-io@7/i2c@18000/deq@6a
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon kernel modesetting enabled.
Sep 19 11:29:57 Debian-G5 kernel: checking generic (b8008000 21c000) vs hw (b0000000 10000000)
Sep 19 11:29:57 Debian-G5 kernel: fb: switching to radeondrmfb from OFfb ATY,Simone
Sep 19 11:29:57 Debian-G5 kernel: Console: switching to colour dummy device 80x25
Sep 19 11:29:57 Debian-G5 kernel: checking generic (b2008000 5a000) vs hw (b0000000 10000000)
Sep 19 11:29:57 Debian-G5 kernel: fb: switching to radeondrmfb from OFfb ATY,Simone
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: enabling device (0006 -> 0007)
Sep 19 11:29:57 Debian-G5 kernel: [drm] initializing kernel modesetting (RV350 0x1002:0x4150 0x1002:0x4150 0x00).
Sep 19 11:29:57 Debian-G5 kernel: [drm] register mmio base: 0xA0000000
Sep 19 11:29:57 Debian-G5 kernel: [drm] register mmio size: 65536
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
Sep 19 11:29:57 Debian-G5 kernel: [drm] Not an x86 BIOS ROM, not using.
Sep 19 11:29:57 Debian-G5 kernel: [drm] Using device-tree clock info
Sep 19 11:29:57 Debian-G5 kernel: agpgart-uninorth 0000:f0:0b.0: putting AGP V3 device into 8x mode
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: putting AGP V3 device into 8x mode
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: GTT: 256M 0x00000000 - 0x0FFFFFFF
Sep 19 11:29:57 Debian-G5 kernel: [drm] Generation 2 PCI interface, using max accessible memory
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: VRAM: 256M 0x00000000B0000000 - 0x00000000BFFFFFFF (64M used)
Sep 19 11:29:57 Debian-G5 kernel: [drm] Detected VRAM RAM=256M, BAR=256M
Sep 19 11:29:57 Debian-G5 kernel: [drm] RAM width 128bits DDR
Sep 19 11:29:57 Debian-G5 kernel: [TTM] Zone  kernel: Available graphics memory: 2040416 kiB
Sep 19 11:29:57 Debian-G5 kernel: [TTM] Initializing pool allocator
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: 64M of VRAM memory ready
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: 256M of GTT memory ready.
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: WB disabled
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: fence driver on ring 0 use gpu addr 0x0000000000000000 and cpu addr 0xd000000003fe0000
Sep 19 11:29:57 Debian-G5 kernel: [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Sep 19 11:29:57 Debian-G5 kernel: [drm] Driver supports precise vblank timestamp query.
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: irq initialized.
Sep 19 11:29:57 Debian-G5 kernel: [drm] Loading R300 Microcode
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: firmware: direct-loading firmware radeon/R300_cp.bin
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: ring at 0x0000000000010000
Sep 19 11:29:57 Debian-G5 kernel: [drm:.r100_ring_test [radeon]] *ERROR* radeon: ring test failed (scratch(0x15E4)=0xCAFEDEAD)
Sep 19 11:29:57 Debian-G5 kernel: [drm:.r100_cp_init [radeon]] *ERROR* radeon: cp isn't working (-22).
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: failed initializing CP (-22).
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: Disabling GPU acceleration
Sep 19 11:29:57 Debian-G5 kernel: [drm:.r100_cp_fini [radeon]] *ERROR* Wait for CP idle timeout, shutting down CP.
Sep 19 11:29:57 Debian-G5 kernel: Failed to wait GUI idle while programming pipes. Bad things might happen.
Sep 19 11:29:57 Debian-G5 kernel: [drm] radeon: cp finalized
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: (r300_asic_reset:425) RBBM_STATUS=0x80010140
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: (r300_asic_reset:444) RBBM_STATUS=0x80010140
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: (r300_asic_reset:456) RBBM_STATUS=0x00000140
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: GPU reset succeed
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: cp finalized
Sep 19 11:29:58 Debian-G5 kernel: [TTM] Finalizing pool allocator
Sep 19 11:29:58 Debian-G5 kernel: [TTM] Zone  kernel: Used memory at exit: 0 kiB
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: ttm finalized
Sep 19 11:29:58 Debian-G5 kernel: [drm] Forcing AGP to PCI mode
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
Sep 19 11:29:58 Debian-G5 kernel: [drm] Not an x86 BIOS ROM, not using.
Sep 19 11:29:58 Debian-G5 kernel: [drm] Using device-tree clock info
Sep 19 11:29:58 Debian-G5 kernel: [drm] Generation 2 PCI interface, using max accessible memory
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: VRAM: 256M 0x00000000B0000000 - 0x00000000BFFFFFFF (64M used)
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: GTT: 512M 0x0000000090000000 - 0x00000000AFFFFFFF
Sep 19 11:29:58 Debian-G5 kernel: [drm] Detected VRAM RAM=256M, BAR=256M
Sep 19 11:29:58 Debian-G5 kernel: [drm] RAM width 128bits DDR
Sep 19 11:29:58 Debian-G5 kernel: [TTM] Zone  kernel: Available graphics memory: 2040416 kiB
Sep 19 11:29:58 Debian-G5 kernel: [TTM] Initializing pool allocator
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: 64M of VRAM memory ready
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: 512M of GTT memory ready.
Sep 19 11:29:58 Debian-G5 kernel: [drm] GART: num cpu pages 8192, num gpu pages 131072
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Sep 19 11:29:58 Debian-G5 kernel: [drm] PCI GART of 512M enabled (table at 0x0000000063000000).
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: WB enabled
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: fence driver on ring 0 use gpu addr 0x0000000090000000 and cpu addr 0xc000000146510000
Sep 19 11:29:58 Debian-G5 kernel: [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Sep 19 11:29:58 Debian-G5 kernel: [drm] Driver supports precise vblank timestamp query.
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: irq initialized.
Sep 19 11:29:58 Debian-G5 kernel: [drm] radeon: ring at 0x0000000090010000
Sep 19 11:29:59 Debian-G5 kernel: [drm:.r100_ring_test [radeon]] *ERROR* radeon: ring test failed (scratch(0x15E4)=0xCAFEDEAD)
Sep 19 11:29:59 Debian-G5 kernel: [drm:.r100_cp_init [radeon]] *ERROR* radeon: cp isn't working (-22).
Sep 19 11:29:59 Debian-G5 kernel: radeon 0000:f0:10.0: failed initializing CP (-22).
Sep 19 11:29:59 Debian-G5 kernel: radeon 0000:f0:10.0: Disabling GPU acceleration
Sep 19 11:29:59 Debian-G5 kernel: [drm:.r100_cp_fini [radeon]] *ERROR* Wait for CP idle timeout, shutting down CP.
Sep 19 11:29:59 Debian-G5 kernel: [drm] radeon: cp finalized
Sep 19 11:29:59 Debian-G5 kernel: [drm] Connector Table: 12 (mac g5 9600)
Sep 19 11:29:59 Debian-G5 kernel: [drm] No valid Ext TMDS info found in BIOS
Sep 19 11:29:59 Debian-G5 kernel: [drm] No TV DAC info found in BIOS
Sep 19 11:29:59 Debian-G5 kernel: [drm] No TMDS info found in BIOS
Sep 19 11:29:59 Debian-G5 kernel: [drm] Radeon Display Connectors
Sep 19 11:29:59 Debian-G5 kernel: [drm] Connector 0:
Sep 19 11:29:59 Debian-G5 kernel: [drm]   DVI-I-1
Sep 19 11:29:59 Debian-G5 kernel: [drm]   HPD1
Sep 19 11:29:59 Debian-G5 kernel: [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Sep 19 11:29:59 Debian-G5 kernel: [drm]   Encoders:
Sep 19 11:29:59 Debian-G5 kernel: [drm]     DFP2: INTERNAL_DVO1
Sep 19 11:29:59 Debian-G5 kernel: [drm]     CRT2: INTERNAL_DAC2
Sep 19 11:29:59 Debian-G5 kernel: [drm] Connector 1:
Sep 19 11:29:59 Debian-G5 kernel: [drm]   DVI-I-2
Sep 19 11:29:59 Debian-G5 kernel: [drm]   HPD2
Sep 19 11:29:59 Debian-G5 kernel: [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Sep 19 11:29:59 Debian-G5 kernel: [drm]   Encoders:
Sep 19 11:29:59 Debian-G5 kernel: [drm]     DFP1: INTERNAL_TMDS1
Sep 19 11:29:59 Debian-G5 kernel: [drm]     CRT1: INTERNAL_DAC1
Sep 19 11:29:59 Debian-G5 kernel: [drm] Connector 2:
Sep 19 11:29:59 Debian-G5 kernel: [drm]   SVIDEO-1
Sep 19 11:29:59 Debian-G5 kernel: [drm]   Encoders:
Sep 19 11:29:59 Debian-G5 kernel: [drm]     TV1: INTERNAL_DAC2
Sep 19 11:29:59 Debian-G5 kernel: Unable to find swap-space signature
Sep 19 11:29:59 Debian-G5 kernel: [drm] fb mappable at 0xB0040000
Sep 19 11:29:59 Debian-G5 kernel: [drm] vram apper at 0xB0000000
Sep 19 11:29:59 Debian-G5 kernel: [drm] size 8323072
Sep 19 11:29:59 Debian-G5 kernel: [drm] fb depth is 24
Sep 19 11:29:59 Debian-G5 kernel: [drm]    pitch is 7680
Sep 19 11:29:59 Debian-G5 kernel: Console: switching to colour frame buffer device 240x67
Sep 19 11:29:59 Debian-G5 kernel: radeon 0000:f0:10.0: fb0: radeondrmfb frame buffer device
Sep 19 11:29:59 Debian-G5 kernel: [drm] Initialized radeon 2.43.0 20080528 for 0000:f0:10.0 on minor 0
Sep 19 11:29:59 Debian-G5 kernel: EXT4-fs (sda4): mounting ext2 file system using the ext4 subsystem
Sep 19 11:29:59 Debian-G5 kernel: EXT4-fs (sda4): mounted filesystem without journal. Opts: (null)
Sep 19 11:30:00 Debian-G5 systemd[1]: Starting LSB: Load kernel modules needed to enable cpufreq scaling...
Sep 19 11:30:03 Debian-G5 loadcpufreq[418]: Loading cpufreq kernel modules...done (none).
Sep 19 11:30:03 Debian-G5 systemd[1]: Started LSB: Load kernel modules needed to enable cpufreq scaling.
Sep 19 11:30:03 Debian-G5 systemd[1]: Starting LSB: set CPUFreq kernel parameters...
Sep 19 11:30:03 Debian-G5 systemd[1]: Started LSB: set CPUFreq kernel parameters.
Sep 19 11:30:05 Debian-G5 NetworkManager[444]: <info>  [1474309805.7808] manager[0x10a17038]: monitoring kernel firmware directory '/lib/firmware'.
Sep 19 11:30:07 Debian-G5 systemd[1]: Startup finished in 5.947s (kernel) + 15.070s (userspace) = 21.017s.
Sep 19 11:30:07 Debian-G5 kernel: IPv6: ADDRCONF(NETDEV_UP): enP1p4s15f0: link is not ready
Sep 19 11:30:07 Debian-G5 kernel: sungem_phy: PHY ID: 2062e0, addr: 1
Sep 19 11:30:07 Debian-G5 kernel: gem 0001:04:0f.0 enP1p4s15f0: Found BCM5421-K2 PHY
Sep 19 11:30:07 Debian-G5 kernel: IPv6: ADDRCONF(NETDEV_UP): enP1p4s15f0: link is not ready
Sep 19 11:30:07 Debian-G5 kernel: IPv6: ADDRCONF(NETDEV_UP): enP1p7s4: link is not ready
Sep 19 11:30:07 Debian-G5 kernel: e100 0001:07:04.0: firmware: direct-loading firmware e100/d101m_ucode.bin
Sep 19 11:30:07 Debian-G5 kernel: IPv6: ADDRCONF(NETDEV_UP): enP1p7s4: link is not ready
Sep 19 11:30:10 Debian-G5 kernel: gem 0001:04:0f.0 enP1p4s15f0: Link is up at 1000 Mbps, full-duplex
Sep 19 11:30:10 Debian-G5 kernel: gem 0001:04:0f.0 enP1p4s15f0: Pause is disabled
Sep 19 11:30:10 Debian-G5 kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enP1p4s15f0: link becomes ready
Sep 19 11:30:46 Debian-G5 kernel: mate-power-mana[806]: unhandled signal 11 at ff25ff00 nip 1ea04100 lr 1ed57930 code 30002
Sep 19 11:31:55 Debian-G5 kernel: mate-terminal[931]: unhandled signal 11 at ff55fe50 nip 1ef64100 lr 1f387930 code 30002
Sep 19 11:35:30 Debian-G5 kernel: mate-terminal[971]: unhandled signal 11 at ff10fe10 nip 1ef54100 lr 1f377930 code 30002
root@Debian-G5:/home/rican-linux# 

```

---

### Post by ernsteiswuerfel on 2016-10-20
From your dmesg I gather that the Debian-Kernel wants to run the card in AGP 8x mode as default, which fails and then it switches the card to PCI mode. It seems to do that every time you get a GPU reset.
```
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: putting AGP V3 device into 8x mode
[...]
Sep 19 11:29:57 Debian-G5 kernel: [drm:.r100_ring_test [radeon]] *ERROR* radeon: ring test failed (scratch(0x15E4)=0xCAFEDEAD)
Sep 19 11:29:57 Debian-G5 kernel: [drm:.r100_cp_init [radeon]] *ERROR* radeon: cp isn't working (-22).
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: failed initializing CP (-22).
Sep 19 11:29:57 Debian-G5 kernel: radeon 0000:f0:10.0: Disabling GPU acceleration
[...]
Sep 19 11:29:58 Debian-G5 kernel: radeon 0000:f0:10.0: GPU reset succeed
[...]
Sep 19 11:29:58 Debian-G5 kernel: [drm] Forcing AGP to PCI mode
```
IMHO Ubuntu does not do that. Also this one is a 4.4.x kernel, Ubuntu 16.10 runs 4.8.x. On Ubuntu's 4.4.x kernel (Xenial) me too had more problems with the G5. I never tried if the "NoAccel-xorg.conf" leads to a stable system with 4.4.x series as I see no point in using 4.4.x any longer.

If xorg actually gets some kind of hardware acceleration or uses software rendering you see in your xorg.log, e.g. **cat /var/log/Xorg.0.log | grep -i aiglx**.

---

