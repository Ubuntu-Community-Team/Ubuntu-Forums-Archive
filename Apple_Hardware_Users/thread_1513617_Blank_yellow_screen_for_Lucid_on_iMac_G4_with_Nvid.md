---
title: "Blank yellow screen for Lucid on iMac G4 with Nvidia graphics, but livecd worsk fine?"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by jmite on 2010-06-19
I'm trying to install lucid on a G4 imac with Nvidia graphics. The live-cd boots just fine, and the graphics work fine for the installer, but after it completes and I boot from disk, all I get is a blank screen

Does anyone know of a way to fix this? If I boot with nouveau.blacklis=true, it says that nouveau.blacklist isn't a valid parameter, and then it boots to a command line login.

I imagine this is a common problem, even if someone can give a link to a solution if it exists... what's strangest is that the livecd works just fine. I need to figure out what's different between it and the installed verison...

---

### Post by linuxopjemac on 2010-06-20
As a starter, can you paste me the link to your iMac G4 model? Thanks.

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

---

### Post by jmite on 2010-06-20
[http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html](http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html)
Pretty ancient...

I've disabled kernel modesetting in /etc/modprobe.d/nouveau-kms.conf, so now when I boot it just goes straight to a command line login.

Do I somehow need to re-enable the nv kernel module? I'm also confused as for how to deal with this, Lucid doesn't really have an xorg.conf file, do I need to create one? (I forget, what is it's full path? I haven't used one in so long...)

Thanks!

---

### Post by linuxopjemac on 2010-06-20
Can you give me the output of:

```
cvt 1024 768
cvt 800 600
cvt 640 480
```

---

### Post by jmite on 2010-06-20
I'll have the ouput from those asap, but basically, I think it could be as simple as enabling the -nv driver. I don't know how to do that, though. Lucid uses nouveau by default, but the livecd seemed to use nv. This explains why when I disabled nv I didn't get any video, just a cli.

---

### Post by linuxopjemac on 2010-06-21
Just give me the cvt output. I will make an xorg.conf for you. Nouveau is the way to go.

---

### Post by jmite on 2010-06-21
Here's the output:

```

# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync


# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync





```

---

### Post by jmite on 2010-06-22
When I run "sudo start gdm" I get x11 in low graphics mode, with very garbled colours... don't know if that's progress or not...

---

### Post by linuxopjemac on 2010-06-22
First make sure you have the driver installed:

```
sudo apt-get install xserver-xorg-video-nouveau
```

Try this xorg.conf file and tell me if it works.

just move your old file to a new name:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Make a new file:
```
sudo nano /etc/X11/xorg.conf

```

and just copy and paste the following lines:

```
Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nouveau"
Option "NoInt10" "true"
Option "FlatPanel" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60.00"

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
           SubSection        "Display"
             Depth            16
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If it does not work, post me the output of:

```
sudo cat /var/log/Xorg.0.log
```

---

### Post by jmite on 2010-06-22
Same green screen. Here's Xorg.0.log
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-22-powerpc64-smp ppc Ubuntu
Current Operating System: Linux tyne-desktop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro  video=ofonly 
Build Date: 09 June 2010  11:07:27AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 24 01:45:47 2010
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
(--) using VT number 7

(--) PCI:*(0:0:16:0) 10de:0110:0000:0000 nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 178, Mem @ 0x91000000/16777216, 0x98000000/134217728, BIOS @ 0x????????/65536
(II) Open APM successful
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
(WW) Warning, couldn't open module nouveau
(II) UnloadModule: "nouveau"
(EE) Failed to load module "nouveau" (module does not exist, 0)
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
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 MX (Mac),  Quadro NVS,
	 Quadro4 500 GoGL,  GeForce4 410 Go 16M,  GeForce4 MX 440 with AGP8X,
	 GeForce4 MX 440SE with AGP8X,  GeForce4 MX 420 with AGP8X,
	 GeForce4 MX 4000,  GeForce4 448 Go,  GeForce4 488 Go,
	 Quadro4 580 XGL,  GeForce4 MX with AGP8X (Mac),  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  GeForce FX 5200 (Mac),
	 Quadro NVS 55/280 PCI,  Quadro FX 500/600 PCI,
	 GeForce FX Go53xx Series,  GeForce FX Go5100,
	 GeForce FX 5900 Ultra,  GeForce FX 5900,  GeForce FX 590T,
	 GeForce FX 5950 Ultra,  GeForce FX 5900ZT,  Quadro FX 3000,
	 Quadro FX 700,  GeForce FX 5700 Ultra,  GeForce FX 5700,
	 GeForce FX 5700LE,  GeForce FX 5700VE,  GeForce FX Go5700,
	 GeForce FX Go5700,  Quadro FX Go1000,  Quadro FX 1100,
	 GeForce 7650 GS,  GeForce 7600 GT,  GeForce 7600 GS,
	 GeForce 7300 GT,  GeForce 7600 LE,  GeForce 7300 GT,
	 GeForce Go 7700,  GeForce Go 7600,  GeForce Go 7600 GT},
	 Quadro NVS 300M,  GeForce Go 7900 SE,  Quadro FX 550M,
	 Quadro FX 560,  GeForce 6150SE,  GeForce 6100 nForce 405,
	 GeForce 6100 nForce 400,  GeForce 6100 nForce 420,
	 GeForce 8600 GTS,  GeForce 8600 GT,  GeForce 8600 GT,
	 GeForce 8600 GS,  GeForce 8400 GS,  GeForce 9500M GS,
	 GeForce 8600M GT,  GeForce 9650M GS,  GeForce 8700M GT,
	 Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,  Quadro FX 1600M,
	 Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,  GeForce 8500 GT,
	 GeForce 8400 GS,  GeForce 8300 GS,  GeForce 8400 GS,
	 GeForce 8600M GS,  GeForce 8400M GT,  GeForce 8400M GS,
	 GeForce 8400M G,  Quadro NVS 140M,  Quadro NVS 130M,
	 Quadro NVS 135M,  GeForce 9400 GT,  Quadro FX 360M,
	 GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:10:0
(--) NV: Found NVIDIA  GeForce2 MX/MX 400 at 00@00:10:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(--) NV(0): Chipset: " GeForce2 MX/MX 400"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0x98000000
(--) NV(0): MMIO registers at 0x91000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: APP  Model: 9c22  Serial#: 0
(II) NV(0): Year: 2002  Week: 0
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing not preferred mode in violation of standard!
(II) NV(0): redX: 0.626 redY: 0.347   greenX: 0.308 greenY: 0.588
(II) NV(0): blueX: 0.146 blueY: 0.118   whiteX: 0.312 whiteY: 0.328
(II) NV(0): Supported established timings:
(II) NV(0): 1024x768@60Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0):  LM150X04
(II) NV(0):  LM150X04
(II) NV(0): Monitor name: Color LCD
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff000610229c00000000
(II) NV(0): 	000c0103801e1778287e50a0584e9625
(II) NV(0): 	1e505400080001010101010101010101
(II) NV(0): 	01010101010164190040410026301888
(II) NV(0): 	360030e410000018000000fe004c4d31
(II) NV(0): 	35305830340000000a20000000fe004c
(II) NV(0): 	4d3135305830340000000a20000000fc
(II) NV(0): 	00436f6c6f72204c43440a2020200040
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 1 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 1
(--) NV(0): Panel size is 1024 x 768
(II) NV(0): NOTE: This driver cannot reconfigure the BIOS-programmed size.
(II) NV(0): These dimensions will be used as the panel size for mode validation.
(II) NV(0): EDID vendor "APP", prod id 39970
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using hsync range of 47.30-48.36 kHz
(II) NV(0): <default monitor>: Using vrefresh range of 59.87-60.00 Hz
(II) NV(0): Estimated virtual size for aspect ratio 1.3043 is 1024x768
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Driver mode "1024x768": 56.0 MHz, 47.3 kHz, 59.9 Hz
(II) NV(0): Modeline "1024x768"x59.9   56.00  1024 1072 1104 1184  768 771 775 790 +hsync -vsync (47.3 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): Display dimensions: (300, 230) mm
(**) NV(0): DPI set to (86, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(==) NV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event2)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event2"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-61EE7089AE8A96287C2B829E837E808A04504E84.xkm
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Mosart Wireless Mouse (/dev/input/event4)
(**) Mosart Wireless Mouse: Applying InputClass "evdev pointer catchall"
(**) Mosart Wireless Mouse: always reports core events
(**) Mosart Wireless Mouse: Device: "/dev/input/event4"
(II) Mosart Wireless Mouse: Found 9 mouse buttons
(II) Mosart Wireless Mouse: Found scroll wheel(s)
(II) Mosart Wireless Mouse: Found relative axes
(II) Mosart Wireless Mouse: Found x and y relative axes
(II) Mosart Wireless Mouse: Configuring as mouse
(**) Mosart Wireless Mouse: YAxisMapping: buttons 4 and 5
(**) Mosart Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mosart Wireless Mouse" (type: MOUSE)
(II) Mosart Wireless Mouse: initialized for relative axes.
(II) config/udev: Adding input device Mosart Wireless Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
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
(II) config/udev: Adding input device PMU (/dev/input/event1)
(**) PMU: Applying InputClass "evdev keyboard catchall"
(**) PMU: always reports core events
(**) PMU: Device: "/dev/input/event1"
(II) PMU: Found keys
(II) PMU: Configuring as keyboard
(II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Mosart Wireless Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) PMU: Close
(II) UnloadModule: "evdev"
(WW) NV(0): xf86UnMapVidMem: cannot find region for [0x4b055000,0x10000]
 ddxSigGiveUp: Closing log


```

There's a chance that I've just messed things up, so I'm going to do a fresh install and try your xorg.conf file, but if the problem is clear from the log file, feel free to let me know...

Thanks!

---

### Post by jmite on 2010-06-22
no luck after a fresh install. booting normally gives a blank yellow screen. Booting with nouveau.blacklist=true gives a command login, and when I do sudo start gdm from the command line, I get low graphics mode with a prompt that, when I try to reconfigure x, doesn't do anything (ie clicking okay just brings up the window I clicked okay for...).
Xorg didn't even generate a log file.

There was no xorg.conf file to begin with. does that mean anything?

---

### Post by linuxopjemac on 2010-06-23
do you have nouveau installed ?

---

### Post by jmite on 2010-06-23
turns out I didn't, but even after a "sudo apt-get install xserver-xorg-video-nouveau" X11 still leaves no log file. There's something called Xorg.failsafe.log, probably from when I start gdm with nouveau.blacklist=true...

---

### Post by jmite on 2010-06-23
if u have ideas, let me know, but I think I'm just gonna stick with karmic... is there any way to just install and tell it to use the exact settings as the livecd? liek I said, this computer cn run ubuntu lucid, I just don't know what's different between the livecd and the install

---

### Post by linuxopjemac on 2010-06-23
boot with KMS disabled but you should not blacklist nouveau, otherwise you can't use the nouveau driver.

just boot with:
```
nomodeset
```

later you can add it to yaboot if you like to do it automatically at boot.

You should use the xorg.conf file with nouveau as driver.

---

### Post by linuxopjemac on 2010-06-23
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
[https://wiki.ubuntu.com/X/KernelModeSetting/](https://wiki.ubuntu.com/X/KernelModeSetting/)

---

### Post by Vlado P. on 2010-08-17
The problem with Ubuntu 10.04 on PowerPC is that it does NOT yet include the kernel module required for the nouveau driver! (see [Ubuntu Devel list](https://lists.ubuntu.com/archives/ubuntu-devel/2010-March/030537.html))

So to quickly get started with Ubuntu 10.04, you'd probably make sure to use the old "nv" driver instead. Here is a shortened version of my xorg.conf, which should at least point you in the right direction:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce4 MX"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Device"
        Identifier      "NVIDIA GeForce4 MX"
        Driver          "nv"
        Option          "FlatPanel"     "1"
        Option          "FPDither"      "1"
EndSection

```
Another option of course is to compile your own kernel (version 2.6.33) including the nouveau module (as described in the message mentioned before).

Since Ubuntu 10.10 is already "frozen" you might also run that instead. I've intensively been using it for two days now, and it seems stable enough. Currently the graphical installer seems broken, though. So go for the "alternate" installer, if you want to be on the safe side.

I really like the new possibilities nouveau offers over nv, like transparent terminals. To be completely satisfied with nouveau I had to fix two more problems, though: nouveau [detected a TV](https://bugs.freedesktop.org/show_bug.cgi?id=29455) on my iMac, which is not there, and I had ["chipped" fonts](https://bugs.freedesktop.org/show_bug.cgi?id=21124), which could be fixed by changing a setting in KDE (System Settings/ Application Appearance/ fonts/ sub-pixel rendering).

---

### Post by linuxopjemac on 2010-08-17
This is interesting information, that explains why I see all the nouveau related problems in Lucid Lynx.

---

