---
title: "Graphical issue"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Xenthan on 2007-08-15
I've been attempting to get my Broadcom driver updated to support the injection needed for aircrack, and to do so I followed the guide at [http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=af9d544f292b33a16c2182a51ea95fbf&topic=2045.0]("http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=af9d544f292b33a16c2182a51ea95fbf&topic=2045.0")

I got all the way up to the command "sudo make modules_install" and then ctrl alt deleted out to the login screen.  Now, when I attempt to log in to that account, I am greeted to nothing but the default background.  Mouse is there, no icons, no windows, can't right click.  In essence I can just test my USB mouse.  Any ideas what would cause this issue?  I'm on the root account at the moment and it's obviously working fine, so I'm a tad confused as to what I could have screwed up.

---

### Post by wieman01 on 2007-08-15
Could you post the contents for this file please?
> cat [COLOR="Red"]/var/log/Xorg.0.log[/COLOR]

---

### Post by Xenthan on 2007-08-15
(II) Primary Device is: PCI 01:05:0
(II) ATI:  Candidate "Device" section "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)".
(--) Chipset ATI Radeon XPRESS 200M 5955 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd0308800 - 0xd03088ff (0x100) MX[B]
        [5] -1  0       0xd0308c00 - 0xd0308cff (0x100) MX[B]
        [6] -1  0       0xd0309000 - 0xd03090ff (0x100) MX[B]
        [7] -1  0       0xd0306000 - 0xd0307fff (0x2000) MX[B]
        [8] -1  0       0xd0300000 - 0xd0303fff (0x4000) MX[B]
        [9] -1  0       0xd0308000 - 0xd03087ff (0x800) MX[B]
        [10] -1 0       0xd0304000 - 0xd0305fff (0x2000) MX[B]
        [11] -1 0       0xd0200000 - 0xd0203fff (0x4000) MX[B]
        [12] -1 0       0xd0003800 - 0xd00038ff (0x100) MX[B]
        [13] -1 0       0xd0003400 - 0xd00034ff (0x100) MX[B]
        [14] -1 0       0xd0003000 - 0xd00033ff (0x400) MX[B]
        [15] -1 0       0xd0002000 - 0xd0002fff (0x1000) MX[B]
        [16] -1 0       0xd0001000 - 0xd0001fff (0x1000) MX[B]
        [17] -1 0       0xd0000000 - 0xd0000fff (0x1000) MX[B]
        [18] -1 0       0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
        [19] -1 0       0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [23] -1 0       0x00008410 - 0x0000841f (0x10) IX[B]
        [24] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [25] -1 0       0x00000170 - 0x00000177 (0x8) IX[B]
        [26] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [28] -1 0       0x00008400 - 0x0000840f (0x10) IX[B]
        [29] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 4.2.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd0308800 - 0xd03088ff (0x100) MX[B]
        [5] -1  0       0xd0308c00 - 0xd0308cff (0x100) MX[B]
        [6] -1  0       0xd0309000 - 0xd03090ff (0x100) MX[B]
        [7] -1  0       0xd0306000 - 0xd0307fff (0x2000) MX[B]
        [8] -1  0       0xd0300000 - 0xd0303fff (0x4000) MX[B]
        [9] -1  0       0xd0308000 - 0xd03087ff (0x800) MX[B]
        [10] -1 0       0xd0304000 - 0xd0305fff (0x2000) MX[B]
        [11] -1 0       0xd0200000 - 0xd0203fff (0x4000) MX[B]
        [12] -1 0       0xd0003800 - 0xd00038ff (0x100) MX[B]
        [13] -1 0       0xd0003400 - 0xd00034ff (0x100) MX[B]
        [14] -1 0       0xd0003000 - 0xd00033ff (0x400) MX[B]
        [15] -1 0       0xd0002000 - 0xd0002fff (0x1000) MX[B]
        [16] -1 0       0xd0001000 - 0xd0001fff (0x1000) MX[B]
        [17] -1 0       0xd0000000 - 0xd0000fff (0x1000) MX[B]
        [18] -1 0       0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
        [19] -1 0       0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [26] -1 0       0x00008410 - 0x0000841f (0x10) IX[B]
        [27] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [28] -1 0       0x00000170 - 0x00000177 (0x8) IX[B]
        [29] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x00008400 - 0x0000840f (0x10) IX[B]
        [32] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
        [33] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [34] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xd0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5955 (PCIE)" (ChipID = 0x5955)
(--) RADEON(0): Linear framebuffer at 0xd4000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Direct rendering broken on XPRESS 200 and 200M
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=65536K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(WW) RADEON(0): Unknown DDCType 5 found
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-4, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 266240 kB
(II) RADEON(0): VESA VBE OEM: ATI MOBILITY RADEON Xpress 200G Series
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: MS48
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read successfully
(II) RADEON(0): DDC Type: 4, Detected Type: 2
(WW) RADEON(0): No valid DDCType is given for DDC2, try vbe probing ...
(II) RADEON(0): DDC Type: 0, Detected Type: 0
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: CMO  Model: 1526  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 9
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.604 redY: 0.340   greenX: 0.306 greenY: 0.521
(II) RADEON(0): blueX: 0.150 blueY: 0.119   whiteX: 0.314 whiteY: 0.321
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) RADEON(0):  N154I2-L02
(II) RADEON(0):  CMO
(II) RADEON(0):  N154I2-L02
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff000daf261500000000
(II) RADEON(0):         09100103802115780ac6a99a574e8526
(II) RADEON(0):         1e505200000001010101010101010101
(II) RADEON(0):         010101010101bc1b00a0502017303020
(II) RADEON(0):         36004bcf10000018000000fe004e3135
(II) RADEON(0):         3449322d4c30320a2020000000fe0043
(II) RADEON(0):         4d4f0a202020202020202020000000fe
(II) RADEON(0):         004e31353449322d4c30320a20200088
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- CRT2_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=47936130030656; xclk=20000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: CMO                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Valid Mode from Detailed timing table: 1280x800
(II) RADEON(0): Total of 1 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 1
(II) RADEON(0): Valid mode using on-chip RMX: 1280x800
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1280x800 (pitch 1280)
(**) RADEON(0): *Mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x800"   71.00  1280 1328 1360 1440  800 803 809 823
(**) RADEON(0):  Default mode "640x350": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x350"   71.00  640 1328 1360 1440  350 803 809 823
(**) RADEON(0):  Default mode "640x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x400"   71.00  640 1328 1360 1440  400 803 809 823
(**) RADEON(0):  Default mode "720x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "720x400"   71.00  720 1328 1360 1440  400 803 809 823
(**) RADEON(0):  Default mode "640x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   71.00  640 1328 1360 1440  480 803 809 823
(**) RADEON(0):  Default mode "800x600": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "800x600"   71.00  800 1328 1360 1440  600 803 809 823
(**) RADEON(0):  Default mode "1024x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1024x768"   71.00  1024 1328 1360 1440  768 803 809 823
(**) RADEON(0):  Default mode "832x624": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "832x624"   71.00  832 1328 1360 1440  624 803 809 823
(**) RADEON(0):  Default mode "1280x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x768"   71.00  1280 1328 1360 1440  768 803 809 823
(**) RADEON(0):  Default mode "1152x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1152x768"   71.00  1152 1328 1360 1440  768 803 809 823
(--) RADEON(0): Display dimensions: (330, 210) mm
(--) RADEON(0): DPI set to (98, 96)
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
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
        of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd0100000 - 0xd010ffff (0x10000) MX[B]
        [1] 0   0       0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xd0308800 - 0xd03088ff (0x100) MX[B]
        [7] -1  0       0xd0308c00 - 0xd0308cff (0x100) MX[B]
        [8] -1  0       0xd0309000 - 0xd03090ff (0x100) MX[B]
        [9] -1  0       0xd0306000 - 0xd0307fff (0x2000) MX[B]
        [10] -1 0       0xd0300000 - 0xd0303fff (0x4000) MX[B]
        [11] -1 0       0xd0308000 - 0xd03087ff (0x800) MX[B]
        [12] -1 0       0xd0304000 - 0xd0305fff (0x2000) MX[B]
        [13] -1 0       0xd0200000 - 0xd0203fff (0x4000) MX[B]
        [14] -1 0       0xd0003800 - 0xd00038ff (0x100) MX[B]
        [15] -1 0       0xd0003400 - 0xd00034ff (0x100) MX[B]
        [16] -1 0       0xd0003000 - 0xd00033ff (0x400) MX[B]
        [17] -1 0       0xd0002000 - 0xd0002fff (0x1000) MX[B]
        [18] -1 0       0xd0001000 - 0xd0001fff (0x1000) MX[B]
        [19] -1 0       0xd0000000 - 0xd0000fff (0x1000) MX[B]
        [20] -1 0       0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
        [21] -1 0       0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
        [22] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [23] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [24] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [25] 0  0       0x00009000 - 0x000090ff (0x100) IX[B]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [28] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [29] -1 0       0x00008410 - 0x0000841f (0x10) IX[B]
        [30] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [31] -1 0       0x00000170 - 0x00000177 (0x8) IX[B]
        [32] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [33] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [34] -1 0       0x00008400 - 0x0000840f (0x10) IX[B]
        [35] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d4000000 0
(**) RADEON(0): Map: 0xd4000000, 0x04000000
(==) RADEON(0): Write-combining range (0xd4000000,0x4000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x7df888)
(**) RADEON(0): Read: 0x00180006 0x00020077 0x00000000
(**) RADEON(0): Read: rd=6, fd=119, pd=2
(**) RADEON(0): RADEONSaveMode returns 0x7df888
(II) RADEON(0): Dynamic Clock Scaling Disabled
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x800       71.00  1280 1328 1360 1440   800  803  809  823 (24,32)
1280x800       71.00  1280 1328 1360 1440   800  803  809  823 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x7e0238
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x7e0238)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20004c4c to 20187c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,800) to (1280,802)
(II) RADEON(0): Largest offscreen area available: 1280 x 7389
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 802)
(II) RADEON(0): Largest offscreen area available: 1280 x 7385
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
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
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
ProcXCloseDevice to close or not ?
xenthan@Craplab:~$

---

