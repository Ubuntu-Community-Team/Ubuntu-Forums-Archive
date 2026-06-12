---
title: "PPC Imac G5 With Radeon ATI X600"
date: 2011-04-06
forum: Apple Hardware Users
---

### Post by freechelmi on 2011-04-06
Hi , I've read a lot of threads on making Imac PPC Ati cards work right but none of the solution worked for me so I thought I would create a new one.


I have a G5 Imac PPC ( [http://www.everymac.com/systems/apple/imac/stats/imac_g5_2.1_20.html](http://www.everymac.com/systems/apple/imac/stats/imac_g5_2.1_20.html)) with an ATI X600 Cards.

I've installed 10.04 without MacOSX


2D and 3D acceleration are not activated. It's just not usable, too sluggish for me.

I tried to disable KMS through creating a radeon-kms.conf file in the modprobe.d directory as advised, but the result is that I get a black screen and the systems seems dead as not of the tty answer.

I 've heard about a lot of option possible to test , mainly here 

[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)


But it's definitely not clear what option should work without getting a kernel panic as it seems for now.

any hint on what could make this kernel panic ?


here is my xorg log with stock ubuntu installed 

> X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-24-powerpc64-smp ppc Ubuntu
Current Operating System: Linux test-desktop 2.6.32-30-powerpc64-smp #59-Ubuntu SMP Tue Mar 1 23:39:42 UTC 2011 ppc64
Kernel command line: root=/dev/sda3 ro quiet splash 
Build Date: 10 December 2010  06:31:47PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  6 23:02:23 2011
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

(--) PCI:*(0:4:0:0) 1002:3e50:1002:3e50 ATI Technologies Inc RV380 0x3e50 [Radeon X600] rev 0, Mem @ 0x98000000/134217728, 0x90000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
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
(==) Matched ati as autoconfigured driver 0
(==) Matched fbdev as autoconfigured driver 1
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
	
[Removed list of cards]

(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 04@00:00:0
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): TOTO SAYS 0000000090000000
(II) RADEON(0): MMIO registers at 0x0000000090000000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) RADEON(0): VGAAccess option set to FALSE, VGA module load skipped
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X600 (RV380) 3E50 (PCIE)" (ChipID = 0x3e50)
(--) RADEON(0): Linear framebuffer at 0x0000000098000000
(II) RADEON(0): PCIE card detected
(WW) RADEON(0): Failed to read PCI ROM!
(II) RADEON(0): Attempting to read un-POSTed bios
(WW) RADEON(0): Failed to read PCI ROM!
(WW) RADEON(0): Unrecognized BIOS signature, BIOS data will not be used
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card15
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card15
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(WW) RADEON(0): Video BIOS not detected, using default clock settings!
(II) RADEON(0): Probed PLL values: xtal: 27.000000 Mhz, sclk: 499.500000 Mhz, mclk: 351.000000 Mhz
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12500 max=35000; xclk=4664
(==) RADEON(0): Detected iMac G5 iSight.
(II) RADEON(0): If this is not correct, try Option "MacModel" and consider reporting to the
(II) RADEON(0): [email]xorg-driver-ati@lists.x.org[/email] mailing list with the contents of /proc/cpuinfo.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Port0:
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP1: INTERNAL_TMDS1
  DDC reg: 0x68
(II) RADEON(0): Port1:
  XRANDR name: VGA-0
  Connector: VGA
  CRT2: INTERNAL_DAC2
  DDC reg: 0x64
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
finished output detect: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): Panel infos found from DDC detailed: 1680x1050
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1680x1050
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(**) RADEON(0): Display dimensions: (430, 270) mm
(**) RADEON(0): DPI set to (99, 158)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): Cannot access BIOS or it is not valid.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit 98000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable FP1
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x9fff9800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1728,8191)
(II) RADEON(0): Reserved area from (0,1680) to (1728,1682)
(II) RADEON(0): Largest offscreen area available: 1728 x 6509
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9fff9800 0x7fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00b16600
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00b1b700
(II) RADEON(0): Largest offscreen area available: 1728 x 6503
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable FP1
disable TVDAC
disable TV
disable FP1
init memmap
init common
init crtc1
init pll1
freq: 119000000
best_freq: 119000000
best_feedback_div: 238
best_frac_feedback_div: 0
best_ref_div: 27
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9fff9800 0x9fff9800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set FP1
enable FP1
disable TVDAC
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 444 x 277
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0

[Removed : keyboard & mouse]


(II) No input driver/identifier specified (ignoring)
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c51  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): DFP 1.x compatible TMDS
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.296 greenY: 0.612
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.313 whiteY: 0.328
(II) RADEON(0): Supported established timings:
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  433 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LM201W01-STB2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000610519c01010101
(II) RADEON(0): 	000f0103812b1b780acf74a3574b9c25
(II) RADEON(0): 	11505400001001010101010101010101
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600b10e1100001c0000000100061021
(II) RADEON(0): 	11000000000000000a20000000fe004c
(II) RADEON(0): 	4d3230315730312d53544232000000fc
(II) RADEON(0): 	00436f6c6f72204c43440a202020006c
(II) RADEON(0): EDID vendor "APP", prod id 40017
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0

---

### Post by linuxopjemac on 2011-04-07
A similar card was found to be totally unworkable with in the MintPPC forums. There is a bug report but no activity there:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=607767](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=607767)
[http://www.mintppc.org/forums/viewtopic.php?f=10&t=69](http://www.mintppc.org/forums/viewtopic.php?f=10&t=69)

ymmv, you can try to change some settings as per:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
[http://linux.die.net/man/4/radeon](http://linux.die.net/man/4/radeon)
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

I wish I could be more helpful. It's trial and error with these cards.

**You may also want to install firmware-linux and firmware-linux-nonfree.**

---

### Post by freechelmi on 2011-04-07
Hi linuxopjemac and thanks for your answer, quick & sharp as usual.

I think also there is really something special with this card.

---

### Post by freechelmi on 2011-06-08
Hi I didn't get further on the this problem. 

Maybe someone can confirme that the problem is easier to solve on 11.04 PPC ?

---

