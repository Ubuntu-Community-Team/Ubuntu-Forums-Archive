---
title: "Backtrack5: How to fix error &quot;black screen&quot; when startx"
date: 2011-08-12
forum: Any Other OS
---

### Post by tracert on 2011-08-12
Pls help me fix this error. Thanks!
Error:
> giving up
xinit: No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno3): Server error.

VGA card/driver: ATI Radeon HD 3600/ati-driver-installer-11-6-x86.x86_64.run

=======================
**This is /var/log/Xorg.0.log**
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux bt 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38 root=UUID=05e75af6-daf8-4382-aa6f-c30b0390a4d5 ro radeon.modeset=0
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 12 10:38:52 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 1002:95c4:17aa:210e ATI Technologies Inc Mobility Radeon HD 3400 Series rev 0, Mem @ 0xd0000000/268435456, 0xcfff0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
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
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 6.9.0, module version = 1.0.0
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.86.5
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.86.5
(II) ATI Proprietary Linux Driver Version Identifier:8.86.5
(II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
(II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:44
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x95C4) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x8ec8b58
(II) fglrx(0): === [xdl_x750_atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 10, (OK)
ukiOpenByBusid: ukiOpenMinor returns 10
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): ATI 2D Acceleration Architecture enabled
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3400 Series" (Chipset = 0x95c4)
(--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x210e)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xcfff0000
(--) fglrx(0): I/O port at 0x00002000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.88
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M82
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(II) fglrx(0): Interrupt handler installed at IRQ 49.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: LVDS
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LEN  Model: 4031  Serial#: 0
(II) fglrx(0): Year: 2007  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.569 redY: 0.332   greenX: 0.312 greenY: 0.544
(II) fglrx(0): blueX: 0.149 blueY: 0.132   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 69.5 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1332  h_sync_end 1396 h_blank_end 1416 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 806 v_blanking: 818 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 57.7 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1332  h_sync_end 1396 h_blank_end 1384 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 806 v_blanking: 834 v_border: 0
(II) fglrx(0): Unknown vendor-specific block f
(II) fglrx(0):  LTN141W1-L05
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff0030ae314000000000
(II) fglrx(0):     00110103801e1378eacd7591554f8b26
(II) fglrx(0):     21505400000001010101010101010101
(II) fglrx(0):     010101010101261b0088502012303440
(II) fglrx(0):     33002fbe100000198b16006850202230
(II) fglrx(0):     344033002fbe100000190000000f0081
(II) fglrx(0):     0a32810a281201004ca35731000000fe
(II) fglrx(0):     004c544e31343157312d4c30350a00d7
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): EDID for output LVDS
(II) fglrx(0): Manufacturer: LEN  Model: 4031  Serial#: 0
(II) fglrx(0): Year: 2007  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.569 redY: 0.332   greenX: 0.312 greenY: 0.544
(II) fglrx(0): blueX: 0.149 blueY: 0.132   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 69.5 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1332  h_sync_end 1396 h_blank_end 1416 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 806 v_blanking: 818 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 57.7 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1332  h_sync_end 1396 h_blank_end 1384 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 806 v_blanking: 834 v_border: 0
(II) fglrx(0): Unknown vendor-specific block f
(II) fglrx(0):  LTN141W1-L05
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff0030ae314000000000
(II) fglrx(0):     00110103801e1378eacd7591554f8b26
(II) fglrx(0):     21505400000001010101010101010101
(II) fglrx(0):     010101010101261b0088502012303440
(II) fglrx(0):     33002fbe100000198b16006850202230
(II) fglrx(0):     344033002fbe100000190000000f0081
(II) fglrx(0):     0a32810a281201004ca35731000000fe
(II) fglrx(0):     004c544e31343157312d4c30350a00d7
(II) fglrx(0): EDID vendor "LEN", prod id 16433
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1280x800"x0.0   69.50  1280 1332 1396 1416  800 803 806 818 -hsync -vsync (49.1 kHz)
(II) fglrx(0): Printing probed modes for output LVDS
(II) fglrx(0): Modeline "1280x800"x60.0   69.50  1280 1332 1396 1416  800 803 806 818 +hsync +vsync (49.1 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x600"x60.0   53.95  1024 1056 1160 1424  600 600 602 627 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x480"x60.0   51.07  800 832 960 1056  480 625 631 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x800"x50.0   57.71  1280 1332 1396 1384  800 803 806 834 +hsync +vsync (41.7 kHz)
(II) fglrx(0): Modeline "1280x768"x50.0   65.17  1280 1336 1464 1648  768 769 772 791 +hsync -vsync (39.5 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync -vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x50.0   51.89  1024 1064 1168 1312  768 769 772 791 +hsync -vsync (39.6 kHz)
(II) fglrx(0): Modeline "1024x600"x50.0   39.55  1024 1048 1152 1280  600 601 604 618 +hsync -vsync (30.9 kHz)
(II) fglrx(0): Modeline "800x600"x50.0   31.14  800 824 904 1008  600 601 604 618 +hsync -vsync (30.9 kHz)
(II) fglrx(0): Modeline "800x480"x50.0   24.15  800 808 888 976  480 481 484 495 +hsync -vsync (24.7 kHz)
(II) fglrx(0): Modeline "720x480"x50.0   21.78  720 728 800 880  480 481 484 495 +hsync -vsync (24.8 kHz)
(II) fglrx(0): Modeline "640x480"x50.0   19.40  640 648 712 784  480 481 484 495 +hsync -vsync (24.7 kHz)
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output LVDS using initial mode 1280x800
(II) fglrx(0): Display dimensions: (300, 190) mm
(II) fglrx(0): DPI set to (108, 106)
(II) fglrx(0): Adapter ATI Mobility Radeon HD 3400 Series has 2 configurable heads and 1 displays connected.
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 15, (OK)
ukiOpenByBusid: ukiOpenMinor returns 15
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb723c000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.86.5
(II) fglrx(0):     Date: May 24 2011
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(0): DRI initialization successfull
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x010a8000
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 528
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 2.0.0
(II) Loading extension AMDXVOPL
(II) Loading extension AMDXVBA
(II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
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
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event4)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Integrated Camera (/dev/input/event5)
(**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
(**) Integrated Camera: always reports core events
(**) Integrated Camera: Device: "/dev/input/event5"
(II) Integrated Camera: Found keys
(II) Integrated Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5598
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4670
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
(II) SynPS/2 Synaptics TouchPad: buttons: left right
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event13)
(**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event13"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found relative axes
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event7)
(**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event7"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) fglrx(0): EDID vendor "LEN", prod id 16433
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1280x800"x0.0   69.50  1280 1332 1396 1416  800 803 806 818 -hsync -vsync (49.1 kHz)
(II) fglrx(0): EDID vendor "LEN", prod id 16433
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1280x800"x0.0   69.50  1280 1332 1396 1416  800 803 806 818 -hsync -vsync (49.1 kHz)
(II) fglrx(0): EDID vendor "LEN", prod id 16433
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1280x800"x0.0   69.50  1280 1332 1396 1416  800 803 806 818 -hsync -vsync (49.1 kHz)
(II) fglrx(0): EDID vendor "LEN", prod id 16433
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1280x800"x0.0   69.50  1280 1332 1396 1416  800 803 806 818 -hsync -vsync (49.1 kHz)
```
**This is my /etc/X11/xorg.conf**
> root@bt:~# cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


**This is my /etc/default/grub**
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

