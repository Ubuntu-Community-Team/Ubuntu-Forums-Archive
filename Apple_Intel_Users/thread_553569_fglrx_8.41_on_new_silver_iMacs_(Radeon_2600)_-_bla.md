---
title: "fglrx 8.41 on new silver iMacs (Radeon 2600) - black screen"
date: 2007-09-17
forum: Apple Intel Users
---

### Post by woodburn8 on 2007-09-17
Just wondering if anyone got the new fglrx 8.41 driver to work with any of Apple's new devices using Radeon 2600's?  I'm on a 24 inch iMac and all I get is a black screen after installing the driver and reconfiguring xorg.

Why fglrx?  The free drivers included with ubuntu don't seem to recognize/support the 2600 yet..?

---

### Post by cyberdork33 on 2007-09-18
> **woodburn8 said:**
> Just wondering if anyone got the new fglrx 8.41 driver to work with any of Apple's new devices using Radeon 2600's?  I'm on a 24 inch iMac and all I get is a black screen after installing the driver and reconfiguring xorg.

When does it go to a black screen? Can you get to a terminal? what does your xorg log say? (/var/log/Xorg.0.log).

> Why fglrx?  The free drivers included with ubuntu don't seem to recognize/support the 2600 yet..?
If you want 3D acceleration, then you need the binary drivers. I don't even know if there is proper 2D support yet.

---

### Post by woodburn8 on 2007-09-19
> When does it go to a black screen? Can you get to a terminal? what does your xorg log say? (/var/log/Xorg.0.log).
It goes blank/black right after the spash screen finishes loading, and can't do anything except hold down the power button for a few seconds.

Before I paste a few hundred lines of logs here, let me do a little more digging myself first.
I installed ubuntu with the alternate cd.. which I think might have a possibly conflicting older version of "fglrx" compiled into the kernel already??  Might need to try recompiling with it removed... when I find more time.

In the meantime, if anyone else gets it working, please do post.
Thanks

---

### Post by cyberdork33 on 2007-09-19
> **woodburn8 said:**
> It goes blank/black right after the spash screen finishes loading, and can't do anything except hold down the power button for a few seconds.

Before I paste a few hundred lines of logs here, let me do a little more digging myself first.
I installed ubuntu with the alternate cd.. which I think might have a possibly conflicting older version of "fglrx" compiled into the kernel already??  Might need to try recompiling with it removed... when I find more time.

In the meantime, if anyone else gets it working, please do post.
Thanks

ah yes, you need to blacklist the older module to prevent it from loading... See this tutorial:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually)

---

### Post by woodburn8 on 2007-09-21
Ah, thanks for that - somehow did not come across that while googling.
I'll give it a try this weekend.

---

### Post by cyberdork33 on 2007-09-21
> **woodburn8 said:**
> Ah, thanks for that - somehow did not come across that while googling.
I'll give it a try this weekend.
Please be sure to let us know if it works!

---

### Post by woodburn8 on 2007-09-30
Well, unfortunately didn't have enough luck

----------
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2600 XT" (Chipset = 0x9583)
(--) fglrx(0): (PciSubVendor = 0x106b, PciSubDevice = 0x0083)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0x40000000
(--) fglrx(0): MMIO registers at 0x50620000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.56
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M76
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"     <-----------------------------------------
(WW) fglrx(0): Failed to open DRM connection     <-----------------------------------------
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: APP  Model: 9c6b  Serial#: 16843009
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.649 redY: 0.338   greenX: 0.289 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.2 MHz   Image Size:  433 x 270 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0):  M201EW02 VB
(II) fglrx(0): Monitor name: Color LCD
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0006106b9c01010101
(II) fglrx(0): 	00100103802b1b780a6085a6564a9c25
(II) fglrx(0): 	12505400000001010101010101010101
(II) fglrx(0): 	010101010101932e90a0601a1e403020
(II) fglrx(0): 	3600b10e110000180000000100061030
(II) fglrx(0): 	11080000000000000a20000000fe004d
(II) fglrx(0): 	32303145573032205642200a000000fc
(II) fglrx(0): 	00436f6c6f72204c43440a2020200000
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.23  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.23  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"  119.23  1280 1728 1760 1840  720 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.23  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.23  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.23  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.23  720 1728 1760 1840  480 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.23  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"  119.23  640 1728 1760 1840  432 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.23  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.23  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.23  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.23  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.23  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync
(--) fglrx(0): Display dimensions: (430, 270) mm
(--) fglrx(0): DPI set to (99, 98)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.23  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.23  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"  119.23  1280 1728 1760 1840  720 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.23  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.23  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.23  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.23  720 1728 1760 1840  480 1053 1059 1080 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.23  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"  119.23  640 1728 1760 1840  432 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.23  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.23  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.23  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.23  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.23  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50620000 - 0x5062ffff (0x10000) MX[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x50200000 - 0x50203fff (0x4000) MX[B]
	[7] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
	[8] -1	0	0x50300000 - 0x50303fff (0x4000) MX[B]
	[9] -1	0	0x50400000 - 0x50400fff (0x1000) MX[B]
	[10] -1	0	0x50705000 - 0x507050ff (0x100) MX[B]
	[11] -1	0	0x50704800 - 0x50704bff (0x400) MX[B]
	[12] -1	0	0x50700000 - 0x50703fff (0x4000) MX[B]
	[13] -1	0	0x50704c00 - 0x50704fff (0x400) MX[B]
	[14] -1	0	0x50600000 - 0x5061ffff (0x20000) MX[B](B)
	[15] -1	0	0x50620000 - 0x5062ffff (0x10000) MX[B](B)
	[16] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[25] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[26] -1	0	0x00004020 - 0x0000402f (0x10) IX[B]
	[27] -1	0	0x00004110 - 0x00004113 (0x4) IX[B]
	[28] -1	0	0x000040f0 - 0x000040f7 (0x8) IX[B]
	[29] -1	0	0x00004114 - 0x00004117 (0x4) IX[B]
	[30] -1	0	0x000040f8 - 0x000040ff (0x8) IX[B]
	[31] -1	0	0x000040e0 - 0x000040ef (0x10) IX[B]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[37] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[38] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[39] -1	0	0x000040a0 - 0x000040bf (0x20) IX[B]
	[40] -1	0	0x000040c0 - 0x000040df (0x20) IX[B]
	[41] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.     <-----------------------------------------
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0x40000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 7141

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxScreenInit+0x505) [0xb79b5725]
3: /usr/X11R6/bin/X(AddScreen+0x1ee) [0x8073dce]
4: /usr/X11R6/bin/X(InitOutput+0x21e) [0x80a540e]
5: /usr/X11R6/bin/X(main+0x27b) [0x807456b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7df2ebc]
7: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

----------

Google turns up a few things for "atiddxDriScreenInit", but wasn't able to solve it right away.

---

### Post by cyberdork33 on 2007-09-30
Yea can't help with that. xorg is crashing. You might get more info if you file a bug report and attach that log file.

---

### Post by clayboy on 2007-10-07
i can help you set up the card i also have the same system so just pm me or aim me clayboidaplyboi

---

### Post by cyberdork33 on 2007-10-08
> **clayboy said:**
> i can help you set up the card i also have the same system so just pm me or aim me clayboidaplyboi
Please put instructions in the forum so that anyone can get help.

---

### Post by Carl Petersen on 2007-10-10
To prevent the old fglrx driver from loading you need to do two things:

Add "fglrx" to the "DISABLE_MODULES" line in the file /etc/defaults/linux-restricted-modules-common

Comment out the line in /etc/modprobe.d/lrm-video which reads "install fglrx...".

Finally have fglrx + xgl + compiz working here.

---

### Post by cyberdork33 on 2007-10-11
> **Carl Petersen said:**
> To prevent the old fglrx driver from loading you need to do two things:

Add "fglrx" to the "DISABLE_MODULES" line in the file /etc/defaults/linux-restricted-modules-common

Comment out the line in /etc/modprobe.d/lrm-video which reads "install fglrx...".

Finally have fglrx + xgl + compiz working here.
I have not seen anyone edit that second file. That may be the key. Is this on Gutsy?

---

### Post by Carl Petersen on 2007-10-11
> **cyberdork33 said:**
> I have not seen anyone edit that second file. That may be the key. Is this on Gutsy?
Yes, Gutsy with all the updates. The first report I saw of it was in BUG #150038. It may have been reported elsewhere.

---

### Post by cyberdork33 on 2007-10-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **Carl Petersen said:**
> Yes, Gutsy with all the updates. The first report I saw of it was in BUG #150038. It may have been reported elsewhere.

I found a bug report that is for this issue... I don't know if there are others. Can you add a comment that this issue affects you as well? This will hopefully help get this fixed.

---

### Post by Carl Petersen on 2007-10-11
> **cyberdork33 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 

I found a bug report that is for this issue... I don't know if there are others. Can you add a comment that this issue affects you as well? This will hopefully help get this fixed.
Done.

We should also try and get the info added to the fglrx install howto.

---

### Post by cyberdork33 on 2007-10-11
> **Carl Petersen said:**
> Done.

We should also try and get the info added to the fglrx install howto.

Actually, there currently is not much compiled information for the new iMacs. There are a couple of threads where people have outlined their 'install process' but nothing that is very in-depth. Could start a wiki page too if there is not one already.

Dirk hasn't been around in a while, and he is the one that edit the sticky post. Might have to get a hold of a moderator.

Are you having this problem as well?
[http://ubuntuforums.org/showthread.php?p=3515549](http://ubuntuforums.org/showthread.php?p=3515549)

---

### Post by Carl Petersen on 2007-10-11
Yea, the low sound volume seems to be a generic problem. I've yet to try the patch but I did look it over and I'm sure it will help. I'll install it tonight and report back if that cures the sound issue.

---

### Post by FunkyM on 2007-10-14
I am using openSUSE but as usual these forums provide a lot of good information. Installed the distro on the new iMac 24" Alu (iMac7,1) model with the usual Apple related issues such as bootloader and partition setup.

Overall I got sound (needs the patch on these forums for v2 models), graphics using fglrx 8.41(openSUSE 10.3 ATI repository) with everything working (3D, 1960x1200, XVideo), full iSight support, USB, Bluetooth, Ethernet (sky2), DVD-Burner and whatever else is in there.

Cons; XGL is failing to work and effectivly Compiz... There is no way to turn down the brightness of the display which is ULTRA-bright but I think it will be a solution by poking some register on the ATI card like current MBP backlight code does (fglrx_xgamma does not do the trick). The WLAN device is a Broadcom 4328 which is new and unsupported by bcm43xx thus you must use ndiswrapper.

---

### Post by cyberdork33 on 2007-10-15
> **FunkyM said:**
> The WLAN device is a Broadcom 4328 which is new and unsupported by bcm43xx thus you must use ndiswrapper.
Same device as in older Intel iMacs, but you are correct about bcm43xx.

---

