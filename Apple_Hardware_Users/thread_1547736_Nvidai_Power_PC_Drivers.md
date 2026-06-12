---
title: "Nvidai Power PC Drivers"
date: 2010-08-07
forum: Apple Hardware Users
---

### Post by newbody on 2010-08-07
Hello,

I installed Ubuntu 10.4 for PPC.
But I need the drivers for my Nvidia Geforce Go5200!

Help PLS!

---

### Post by linuxopjemac on 2010-08-07
You could try nouveau, which is an open source project to support nVidia hardware.

---

### Post by newbody on 2010-08-07
> **linuxopjemac said:**
> You could try nouveau, which is an open source project to support nVidia hardware.

Well, I installed it.
And it was installed.

But I want to use Compiz with my iMac G5

---

### Post by linuxopjemac on 2010-08-07
compiz should work with nouveau. You have to have a working xorg.conf file. Show me the output of

```
sudo cat /etc/X11/xorg.conf
```

---

### Post by newbody on 2010-08-08
> **linuxopjemac said:**
> compiz should work with nouveau. You have to have a working xorg.conf file. Show me the output of

```
sudo cat /etc/X11/xorg.conf
```

No such file or directory???

---

### Post by linuxopjemac on 2010-08-08
that is the problem...for compiz to work, you need to have some settings in xorg.conf

I will try to make a working xorg.conf file for you. Can you give me the specs of your G5 (everymac.com) and your monitor please ?

---

### Post by newbody on 2010-08-08
> **linuxopjemac said:**
> that is the problem...for compiz to work, you need to have some settings in xorg.conf

I will try to make a working xorg.conf file for you. Can you give me the specs of your G5 (everymac.com) and your monitor please ?

Oh thank you very much.

I think I have this one:
[http://www.everymac.com/systems/apple/imac/stats/imac_g5_1.8_17.html](http://www.everymac.com/systems/apple/imac/stats/imac_g5_1.8_17.html)

and the size is: 1440x900
(16:10)

---

### Post by linuxopjemac on 2010-08-08
which monitor? link please.

---

### Post by newbody on 2010-08-08
> **linuxopjemac said:**
> which monitor? link please.

It's the Monitor which is integrated in G5 Apple Mac

---

### Post by linuxopjemac on 2010-08-08
I will try to come up with something tomorrow. I was very busy today with my car and now it's time to have dinner.

---

### Post by Finalfantasykid on 2010-08-08
Actually don't you need the gallium driver for nouveau to have 3d acceleration?  Compiz requires 3d capabilities right?

---

### Post by newbody on 2010-08-08
> **linuxopjemac said:**
> I will try to come up with something tomorrow. I was very busy today with my car and now it's time to have dinner.

It's so nice of you!
Enjoy the dinner.
I'll be happy tomorrow

---

### Post by linuxopjemac on 2010-08-09
try this:

```
Section "Device"
	Identifier	"GeForce FX 5200 Ultra"
	BusID		"PCI:0:16:0"
	Driver		"nouveau"
	Option "NoInt10" "true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"GeForce FX 5200 Ultra"
	Monitor		"iMac"
	DefaultDepth    24
	SubSection "Display"
		Depth   24
		Modes   "1440x900" "1152x720" "1024x640" "800x500"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"iMac Configuration"
	Screen 0	"Screen0"		0 0
EndSection
```

make sure you have nouveau
```

sudo apt-get install xserver-xorg-video-nouveau
```

It would be even better if we have the modeline of 1440x900. can you give me the output of:

```
cvt 1440 900
```

NOTE: that 3D acceleration is not supported by 10.04 yet. So it is unlikely that you will get compiz to work now.

---

### Post by linuxopjemac on 2010-08-09
also look at this post:
[http://ubuntuforums.org/archive/index.php/t-1501746.html](http://ubuntuforums.org/archive/index.php/t-1501746.html)

and here:
[http://nouveau.freedesktop.org/wiki/FAQ#Glxgearsworks.21Butyousaidthereisno3D.3F](http://nouveau.freedesktop.org/wiki/FAQ#Glxgearsworks.21Butyousaidthereisno3D.3F)

---

### Post by newbody on 2010-08-09
> **linuxopjemac said:**
> try this:

```
Section "Device"
    Identifier    "GeForce FX 5200 Ultra"
    BusID        "PCI:0:16:0"
    Driver        "nouveau"
    Option "NoInt10" "true"
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"
EndSection


Section "Screen"
    Identifier    "Screen0"
    Device        "GeForce FX 5200 Ultra"
    Monitor        "iMac"
    DefaultDepth    24
    SubSection "Display"
        Depth   24
        Modes   "1440x900" "1152x720" "1024x640" "800x500"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "iMac Configuration"
    Screen 0    "Screen0"        0 0
EndSection
```make sure you have nouveau
```

sudo apt-get install xserver-xorg-video-nouveau
```It would be even better if we have the modeline of 1440x900. can you give me the output of:

```
cvt 1440 900
```NOTE: that 3D acceleration is not supported by 10.04 yet. So it is unlikely that you will get compiz to work now.


Hello:

1. Where should I type in this code? When I'm typing that in in the terminal Im only getting some error messages!

2.cvt 1440 900 :
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

---

### Post by linuxopjemac on 2010-08-09
You have to make the xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

you enter an editor, then paste the following:

```
Section "Device"
    Identifier    "GeForce FX 5200 Ultra"
    BusID        "PCI:0:16:0"
    Driver        "nouveau"
    Option "NoInt10" "true"
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync 
Option "PreferredMode" "1440x900_60.00"
EndSection


Section "Screen"
    Identifier    "Screen0"
    Device        "GeForce FX 5200 Ultra"
    Monitor        "iMac"
    DefaultDepth    24
    SubSection "Display"
        Depth   24
        Modes   "1440x900" "1152x720" "1024x640" "800x500"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "iMac Configuration"
    Screen 0    "Screen0"        0 0
EndSection
```

then CTRL-X and "y" to save the file.

Then reboot and see if it works.

---

### Post by newbody on 2010-08-09
Hei, 

so nice of you.
I followed your instructions and rebooted my pc.
And I got the message:
Ubuntu is running with low graphics.
Error: No devices detected

(I translated it, so it should be another message in english)

So what ca I do?

LG
:KS

---

### Post by linuxopjemac on 2010-08-09
did you install the driver ?

---

### Post by newbody on 2010-08-09
> **linuxopjemac said:**
> did you install the driver ?

Yes

I gave in: 

sudo apt-get install xserver-xorg-video-nouveau

and he said that I already have the newest Version.

---

### Post by newbody on 2010-08-10
> **linuxopjemac said:**
> did you install the driver ?

Today I ran lshw. And here are my Ubuntu Sys Infos:

 width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
       clock: 285MHz
       capabilities: powermac8_1 macrisc4 power_macintosh
     *-firmware
          product: OpenFirmware 4
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-cpu
          description: CPU
          product: PPC970FX, altivec supported
          physical id: 1
          bus info: cpu@0
          version: 3.0 (pvr 003c 0300)
          size: 900MHz
          capacity: 900MHz
          clock: 600MHz
          capabilities: altivec performance-monitor cpufreq
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 512KiB
             clock: 1152MHz (0.9ns)
     *-memory
          description: System memory
          physical id: 2
          size: 1183MiB
     *-pci:0
          description: Host bridge
          product: U3L AGP Bridge
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@0000:f0:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: NV34M [GeForce FX Go5200]
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:f0:10.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list rom
             configuration: driver=nouveau latency=16 maxlatency=1 mingnt=5
             resources: irq:59 memory:91000000-91ffffff memory:a0000000-a7ffffff(prefetchable) memory:90000000-9001ffff(prefetchable)
     *-pci:1
          description: Host bridge
          product: U4 PCIe
          vendor: Apple Computer Inc.
          physical id: 101
          bus info: pci@0001:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Shasta PCI Bridge
             vendor: Apple Computer Inc.
             physical id: 1
             bus info: pci@0001:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:80200000-805fffff
           *-network
                description: Ethernet interface
                product: Shasta (Sun GEM)
                vendor: Apple Computer Inc.
                physical id: f
                bus info: pci@0001:03:0f.0
                logical name: eth0
                version: 00
                serial: 00:0d:93:b6:87:86
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master rom ethernet physical
                configuration: broadcast=yes driver=sungem driverversion=0.98 ip=192.168.2.104 latency=16 maxlatency=64 mingnt=64 multicast=yes
                resources: irq:40 memory:80400000-805fffff memory:80200000-802fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: Shasta PCI Bridge
             vendor: Apple Computer Inc.
             physical id: 2
             bus info: pci@0001:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:80000000-800fffff
           *-generic
                product: Shasta Mac I/O
                vendor: Apple Computer Inc.
                physical id: 7
                bus info: pci@0001:01:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=macio latency=16
                resources: irq:0 memory:80000000-8007ffff
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b
                bus info: pci@0001:01:0b.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1
                resources: irq:70 memory:80082000-80082fff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b.1
                bus info: pci@0001:01:0b.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1
                resources: irq:70 memory:80081000-80081fff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: b.2
                bus info: pci@0001:01:0b.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ehci_hcd latency=16 maxlatency=34 mingnt=16
                resources: irq:70 memory:80080000-800800ff
        *-pci:2
             description: PCI bridge
             product: Shasta PCI Bridge
             vendor: Apple Computer Inc.
             physical id: 3
             bus info: pci@0001:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:80100000-801fffff
           *-ide
                description: IDE interface
                product: K2 SATA
                vendor: Broadcom
                physical id: c
                bus info: pci@0001:02:0c.0
                logical name: scsi0
                logical name: scsi1
                logical name: scsi2
                logical name: scsi3
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: ide bus_master scsi-host
                configuration: driver=sata_svw latency=16
                resources: irq:17 memory:80102000-80103fff
           *-generic
                product: Shasta IDE
                vendor: Apple Computer Inc.
                physical id: d
                bus info: pci@0001:02:0d.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=ide-pmac latency=32
                resources: irq:38 memory:80104000-80107fff
              *-ide
                   description: IDE Channel 0
                   physical id: 0
                   bus info: ide@0
                   logical name: ide0
                   clock: 33MHz
                 *-cdrom
                      product: MATSHITADVD-R UJ-825
                      physical id: 0
                      bus info: ide@0.0
                      logical name: /dev/hda
                      capabilities: packet
           *-firewire
                description: FireWire (IEEE 1394)
                product: Shasta Firewire
                vendor: Apple Computer Inc.
                physical id: e
                bus info: pci@0001:02:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=248 maxlatency=24 mingnt=12
                resources: irq:39 memory:80100000-80100fff
ortega@ortega-desktop:~$ s

---

### Post by linuxopjemac on 2010-08-10
can you give me the output of:

```
sudo cat /var/log/Xorg.0.log
```

Maybe you have to try a lower color bit depth, e.g. 16. The section will look like this then:

```
Section "Screen"
    Identifier    "Screen0"
    Device        "GeForce FX 5200 Ultra"
    Monitor        "iMac"
    DefaultDepth    16
    SubSection "Display"
        Depth   16
        Modes   "1440x900" "1152x720" "1024x640" "800x500"
    EndSubSection
EndSection
```

---

### Post by newbody on 2010-08-11
Here's the output

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-22-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ortega-desktop 2.6.32-24-powerpc64-smp #39-Ubuntu SMP Wed Jul 28 21:17:01 UTC 2010 ppc64
Kernel command line: root=/dev/sda3 ro quiet splash 
Build Date: 16 June 2010  09:45:48AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 11 09:11:00 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:240:16:0) 10de:0329:10de:0010 nVidia Corporation NV34M [GeForce FX Go5200] rev 161, Mem @ 0x91000000/16777216, 0xa0000000/134217728, BIOS @ 0x????????/131072
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.7.3.902, module version = 2.1.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI f0@00:10:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:f0:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:f0:10.0
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:f0:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:f0:10.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV34"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output TV-1 has no monitor section
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): Manufacturer: APP  Model: 9c27  Serial#: 0
(II) NOUVEAU(0): Year: 2002  Week: 0
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing not preferred mode in violation of standard!
(II) NOUVEAU(0): redX: 0.626 redY: 0.347   greenX: 0.308 greenY: 0.588
(II) NOUVEAU(0): blueX: 0.146 blueY: 0.108   whiteX: 0.312 whiteY: 0.328
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 96.2 MHz   Image Size:  367 x 229 mm
(II) NOUVEAU(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 912 v_border: 0
(II) NOUVEAU(0):  LM171W02
(II) NOUVEAU(0):  LM171W02
(II) NOUVEAU(0):  COLOR
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):     00ffffffffffff000610279c00000000
(II) NOUVEAU(0):     000c010380251778287e70a0584e9625
(II) NOUVEAU(0):     1b505400000001010101010101010101
(II) NOUVEAU(0):     0101010101019525a04051840c304020
(II) NOUVEAU(0):     33006fe510000018000000fe004c4d31
(II) NOUVEAU(0):     37315730320000000000000000fe004c
(II) NOUVEAU(0):     4d3137315730320000000000000000fe
(II) NOUVEAU(0):     00434f4c4f52004c4344000000000027
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): Printing probed modes for output DVI-D-1
(II) NOUVEAU(0): Modeline "1440x900"x59.9   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): EDID for output TV-1
(II) NOUVEAU(0): Output DVI-D-1 connected
(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output TV-1 disconnected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output DVI-D-1 using initial mode 1440x900
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1440x900 (pitch 1472)
(**) NOUVEAU(0):  Driver mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1440x900"x59.9   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(**) NOUVEAU(0): Display dimensions: (370, 230) mm
(**) NOUVEAU(0): DPI set to (98, 99)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 64MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(==) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 381 x 238
resize called 1440 900
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Logitech Apple Optical USB Mouse (/dev/input/event1)
(**) Logitech Apple Optical USB Mouse: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Logitech Apple Optical USB Mouse: always reports core events
(**) Logitech Apple Optical USB Mouse: Device: "/dev/input/event1"
(II) Logitech Apple Optical USB Mouse: Found 1 mouse buttons
(II) Logitech Apple Optical USB Mouse: Found relative axes
(II) Logitech Apple Optical USB Mouse: Found x and y relative axes
(II) Logitech Apple Optical USB Mouse: Configuring as mouse
(**) Logitech Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Apple Optical USB Mouse" (type: MOUSE)
(II) Logitech Apple Optical USB Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech Apple Optical USB Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/event2)
(**) Microsoft Microsoft Wireless Optical Mouse® 1.00: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Microsoft Wireless Optical Mouse® 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse® 1.00: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found 9 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found scroll wheel(s)
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found relative axes
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse® 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse® 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse® 1.00" (type: MOUSE)
(II) Microsoft Microsoft Wireless Optical Mouse® 1.00: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(II) XKB: reuse xkmfile /var/lib/xkb/server-1B5353734E7854C1F2B0553E65A16986C9AAC402.xkm
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev keyboard catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event5)
(**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event5"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event6)
(**) Mouseemu virtual mouse: Applying InputClass "evdev keyboard catchall"
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event6"
(II) Mouseemu virtual mouse: Found 14 mouse buttons
(II) Mouseemu virtual mouse: Found scroll wheel(s)
(II) Mouseemu virtual mouse: Found relative axes
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(II) Mouseemu virtual mouse: initialized for relative axes.
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(WW) config/udev: device Mouseemu virtual keyboard already added. Ignoring.
(WW) config/udev: device Mouseemu virtual mouse already added. Ignoring.
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) NOUVEAU(0): EDID vendor "APP", prod id 39975
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
ortega@ortega-desktop:~$

---

### Post by linuxopjemac on 2010-08-11
Maybe it does not like 1440x900

give the output of
```
cvt 1152 720
cvt 1024 640
cvt 800 500
cvt 1024 768
cvt 800 600
cvt 640 480
```

We will now try to make an xorg.conf file, without forcing him to use 1440x900

---

### Post by newbody on 2010-08-11
> **linuxopjemac said:**
> Maybe it does not like 1440x900

give the output of
```
cvt 1152 720
cvt 1024 640
cvt 800 500
cvt 1024 768
cvt 800 600
cvt 640 480
```We will now try to make an xorg.conf file, without forcing him to use 1440x900

Thank you very much.

Here's my output

# 1152x720 59.97 Hz (CVT 0.83MA) hsync: 44.86 kHz; pclk: 66.75 MHz
Modeline "1152x720_60.00"   66.75  1152 1208 1320 1488  720 723 729 748 -hsync +vsync
ortega@ortega-desktop:~$ cvt 1024 640
# 1024x640 59.89 Hz (CVT 0.66MA) hsync: 39.82 kHz; pclk: 52.25 MHz
Modeline "1024x640_60.00"   52.25  1024 1072 1168 1312  640 643 649 665 -hsync +vsync
ortega@ortega-desktop:~$ cvt 800 500
# 800x500 59.50 Hz (CVT 0.40MA) hsync: 31.00 kHz; pclk: 30.75 MHz
Modeline "800x500_60.00"   30.75  800 824 896 992  500 503 509 521 -hsync +vsync
ortega@ortega-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
ortega@ortega-desktop:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

---

### Post by linuxopjemac on 2010-08-11
Try this:

```
Section "Device"
    Identifier    "GeForce FX 5200 Ultra"
    BusID        "PCI:240:16:0"
    Driver        "nouveau"
    Option "NoInt10" "true"
EndSection

Section "Monitor"
    Identifier    "iMac"
    Option        "DPMS"

# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync 

# 1152x720 59.97 Hz (CVT 0.83MA) hsync: 44.86 kHz; pclk: 66.75 MHz
Modeline "1152x720_60.00" 66.75 1152 1208 1320 1488 720 723 729 748 -hsync +vsync

# 1024x640 59.89 Hz (CVT 0.66MA) hsync: 39.82 kHz; pclk: 52.25 MHz
Modeline "1024x640_60.00" 52.25 1024 1072 1168 1312 640 643 649 665 -hsync +vsync

# 800x500 59.50 Hz (CVT 0.40MA) hsync: 31.00 kHz; pclk: 30.75 MHz
Modeline "800x500_60.00" 30.75 800 824 896 992 500 503 509 521 -hsync +vsync

# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync

#Option "PreferredMode" "1440x900_60.00"
EndSection


Section "Screen"
    Identifier    "Configured Screen"
    Device        "GeForce FX 5200 Ultra"
    Monitor        "iMac"
    DefaultDepth    24

    SubSection "Display"
        Depth   24
        Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

SubSection "Display"
        Depth   16
         Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

SubSection "Display"
        Depth   15
         Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

SubSection "Display"
        Depth   8
         Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

SubSection "Display"
        Depth   4
         Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

SubSection "Display"
        Depth   1
         Modes   "1440x900" "1152x720" "1024x640" "800x500" "1024x768" "800x600"
    EndSubSection

EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Configured Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

```

---

### Post by newbody on 2010-08-11
Hello,

your code had succes!!!! I didn't get any error messages!
BUT, I coudn't activate my desktop effects :(

---

### Post by svtguy88 on 2010-08-12
Desktop effects require DRI, which currently is not supported by nouveau.  The development version (when combined with a newer kernel and xserver) of nouveau has DRI/3d accel support, but not the one that comes from the ubuntu repo's.

---

### Post by newbody on 2010-08-13
> **pkmgarf said:**
> Desktop effects require DRI, which currently is not supported by nouveau.  The development version (when combined with a newer kernel and xserver) of nouveau has DRI/3d accel support, but not the one that comes from the ubuntu repo's.

Thank you!
So what should I do if I want to use desktop effects?

---

### Post by linuxopjemac on 2010-08-13
wait for a next release of Nouveau...

---

### Post by newbody on 2010-08-13
> **linuxopjemac said:**
> wait for a next release of nouveau...

:(

but thannnkkkk you!!!!!!!

---

### Post by linuxopjemac on 2010-08-13
No problem, your xorg.conf file will be useful for others:

[http://mac.linux.be/content/g5-imac-18-ghz-17-inch-xorgconf](http://mac.linux.be/content/g5-imac-18-ghz-17-inch-xorgconf)

by the way:
[http://nouveau.freedesktop.org/wiki/FeatureMatrix](http://nouveau.freedesktop.org/wiki/FeatureMatrix)

Your card falls under NV30, so you see a bit how 3D support is in nouveau now.

---

### Post by dpny on 2010-11-25
Is it possible to use a different nvidia driver, or to downgrade to an earlier X as a hacky way of fixing this until the nouveau team finishes?

---

### Post by linuxopjemac on 2010-11-26
use the "nv" driver

---

### Post by newbody on 2010-11-26
Hi,

how can I use NV??

---

### Post by dpny on 2010-11-26
> **linuxopjemac said:**
> use the "nv" driver

Looking at the man page for nv, it appears it is only a 2D driver, so no accelerated 3D. Am I correct?

---

### Post by linuxopjemac on 2010-11-27
correct, but it works as opposed to nouveau.

---

### Post by dpny on 2010-11-27
> **linuxopjemac said:**
> correct, but it works as opposed to nouveau.

Thanks.

---

