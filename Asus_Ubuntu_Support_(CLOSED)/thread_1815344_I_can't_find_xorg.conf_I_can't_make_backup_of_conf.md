---
title: "I can't find xorg.conf I can't make backup of configuration"
date: 2011-07-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by electrogenius on 2011-07-31
Hi,
I am a noob.
I need to export/save existing Xorg configuration as a xorg.conf file but the problem is i can't find it. 
Here is my /var/log/Xorg.0.log
```

[    75.829] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    75.829] X Protocol Version 11, Revision 0
[    75.829] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    75.829] Current Operating System: Linux electrogenius-EasyNote-TK85 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64
[    75.829] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=2522e9f9-575f-40a3-b52c-82b5bc8caa7f ro quiet splash vt.handoff=7
[    75.829] Build Date: 21 May 2011  11:48:41AM
[    75.829] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    75.829] Current version of pixman: 0.20.2
[    75.829]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    75.829] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    75.829] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 31 11:48:27 2011
[    75.830] (==) **Using system config directory "/usr/share/X11/xorg.conf.d"**
[    75.830] (==) No Layout section.  Using the first Screen section.
[    75.830] (==) No screen section available. Using defaults.
[    75.830] (**) |-->Screen "Default Screen Section" (0)
[    75.830] (**) |   |-->Monitor "<default monitor>"
[    75.830] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    75.830] (==) Automatically adding devices
[    75.830] (==) Automatically enabling devices
[    75.830] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    75.830]     Entry deleted from font path.
[    75.830] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    75.830]     Entry deleted from font path.
[    75.830] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    75.830]     Entry deleted from font path.
[    75.830] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    75.830]     Entry deleted from font path.
[    75.830] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    75.830]     Entry deleted from font path.
[    75.830] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    75.830] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    75.830] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    75.830] (II) Loader magic: 0x7e0280
[    75.830] (II) Module ABI versions:
[    75.830]     X.Org ANSI C Emulation: 0.4
[    75.830]     X.Org Video Driver: 10.0
[    75.830]     X.Org XInput driver : 12.3
[    75.830]     X.Org Server Extension : 5.0
[    75.831] (--) PCI:*(0:0:2:0) 8086:0046:1025:0488 rev 2, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00004050/8
[    75.831] (--) PCI: (0:1:0:0) 10de:0df4:1025:0488 rev 161, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    75.831] (II) Open ACPI successful (/var/run/acpid.socket)
[    75.831] (II) LoadModule: "extmod"
[    75.831] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    75.831] (II) Module extmod: vendor="X.Org Foundation"
[    75.831]     compiled for 1.10.1, module version = 1.0.0
[    75.831]     Module class: X.Org Server Extension
[    75.831]     ABI class: X.Org Server Extension, version 5.0
[    75.832] (II) Loading extension MIT-SCREEN-SAVER
[    75.832] (II) Loading extension XFree86-VidModeExtension
[    75.832] (II) Loading extension XFree86-DGA
[    75.832] (II) Loading extension DPMS
[    75.832] (II) Loading extension XVideo
[    75.832] (II) Loading extension XVideo-MotionCompensation
[    75.832] (II) Loading extension X-Resource
[    75.832] (II) LoadModule: "dbe"
[    75.832] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    75.832] (II) Module dbe: vendor="X.Org Foundation"
[    75.832]     compiled for 1.10.1, module version = 1.0.0
[    75.832]     Module class: X.Org Server Extension
[    75.832]     ABI class: X.Org Server Extension, version 5.0
[    75.832] (II) Loading extension DOUBLE-BUFFER
[    75.832] (II) LoadModule: "glx"
[    75.832] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    75.839] (II) Module glx: vendor="NVIDIA Corporation"
[    75.839]     compiled for 4.0.2, module version = 1.0.0
[    75.839]     Module class: X.Org Server Extension
[    75.839] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    75.839] (II) Loading extension GLX
[    75.839] (II) LoadModule: "record"
[    75.839] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    75.839] (II) Module record: vendor="X.Org Foundation"
[    75.839]     compiled for 1.10.1, module version = 1.13.0
[    75.839]     Module class: X.Org Server Extension
[    75.839]     ABI class: X.Org Server Extension, version 5.0
[    75.839] (II) Loading extension RECORD
[    75.839] (II) LoadModule: "dri"
[    75.840] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    75.840] (II) Module dri: vendor="X.Org Foundation"
[    75.840]     compiled for 1.10.1, module version = 1.0.0
[    75.840]     ABI class: X.Org Server Extension, version 5.0
[    75.840] (II) Loading extension XFree86-DRI
[    75.840] (II) LoadModule: "dri2"
[    75.840] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    75.840] (II) Module dri2: vendor="X.Org Foundation"
[    75.840]     compiled for 1.10.1, module version = 1.2.0
[    75.840]     ABI class: X.Org Server Extension, version 5.0
[    75.840] (II) Loading extension DRI2
[    75.840] (==) Matched intel as autoconfigured driver 0
[    75.840] (==) Matched vesa as autoconfigured driver 1
[    75.840] (==) Matched fbdev as autoconfigured driver 2
[    75.840] (==) Assigned the driver to the xf86ConfigLayout
[    75.840] (II) LoadModule: "intel"
[    75.840] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    75.840] (II) Module intel: vendor="X.Org Foundation"
[    75.840]     compiled for 1.10.1, module version = 2.14.0
[    75.840]     Module class: X.Org Video Driver
[    75.840]     ABI class: X.Org Video Driver, version 10.0
[    75.840] (II) LoadModule: "vesa"
[    75.841] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    75.841] (II) Module vesa: vendor="X.Org Foundation"
[    75.841]     compiled for 1.10.0, module version = 2.3.0
[    75.841]     Module class: X.Org Video Driver
[    75.841]     ABI class: X.Org Video Driver, version 10.0
[    75.841] (II) LoadModule: "fbdev"
[    75.841] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    75.841] (II) Module fbdev: vendor="X.Org Foundation"
[    75.841]     compiled for 1.10.0, module version = 0.4.2
[    75.841]     ABI class: X.Org Video Driver, version 10.0
[    75.841] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    75.841] (II) VESA: driver for VESA chipsets: vesa
[    75.841] (II) FBDEV: driver for framebuffer: fbdev
[    75.841] (--) using VT number 8

[    75.845] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    75.845] (WW) Falling back to old probe method for vesa
[    75.845] (WW) Falling back to old probe method for fbdev
[    75.845] (II) Loading sub module "fbdevhw"
[    75.845] (II) LoadModule: "fbdevhw"
[    75.846] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    75.846] (II) Module fbdevhw: vendor="X.Org Foundation"
[    75.846]     compiled for 1.10.1, module version = 0.0.2
[    75.846]     ABI class: X.Org Video Driver, version 10.0
[    75.846] drmOpenDevice: node name is /dev/dri/card0
[    75.846] drmOpenDevice: open result is 9, (OK)
[    75.846] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    75.846] drmOpenDevice: node name is /dev/dri/card0
[    75.846] drmOpenDevice: open result is 9, (OK)
[    75.846] drmOpenByBusid: drmOpenMinor returns 9
[    75.846] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    75.846] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    75.846] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    75.846] (==) intel(0): RGB weight 888
[    75.846] (==) intel(0): Default visual is TrueColor
[    75.846] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    75.846] (--) intel(0): Chipset: "Arrandale"
[    75.846] (**) intel(0): Relaxed fencing enabled
[    75.846] (**) intel(0): Tiling enabled
[    75.846] (**) intel(0): SwapBuffers wait enabled
[    75.846] (==) intel(0): video overlay key set to 0x101fe
[    75.846] (II) intel(0): Output LVDS1 has no monitor section
[    75.940] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    76.001] (II) intel(0): Output VGA1 has no monitor section
[    76.006] (II) intel(0): Output HDMI1 has no monitor section
[    76.007] (II) intel(0): Output DP1 has no monitor section
[    76.007] (II) intel(0): EDID for output LVDS1
[    76.007] (II) intel(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    76.007] (II) intel(0): Year: 2009  Week: 1
[    76.007] (II) intel(0): EDID Version: 1.3
[    76.007] (II) intel(0): Digital Display Input
[    76.007] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    76.007] (II) intel(0): Gamma: 2.20
[    76.007] (II) intel(0): No DPMS capabilities specified
[    76.007] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    76.007] (II) intel(0): First detailed timing is preferred mode
[    76.007] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    76.007] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    76.007] (II) intel(0): Manufacturer's mask: 0
[    76.007] (II) intel(0): Supported detailed timing:
[    76.007] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    76.007] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
[    76.007] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    76.007] (II) intel(0): Unknown vendor-specific block f
[    76.007] (II) intel(0):  AUO
[    76.007] (II) intel(0):  B156XW02 V2
[    76.007] (II) intel(0): EDID (in hex):
[    76.007] (II) intel(0):     00ffffffffffff0006afec2200000000
[    76.007] (II) intel(0):     01130103802213780ac8959e57549226
[    76.007] (II) intel(0):     0f505400000001010101010101010101
[    76.007] (II) intel(0):     010101010101121b5642500026302018
[    76.007] (II) intel(0):     340058c1100000180000000f00000000
[    76.007] (II) intel(0):     00000000000000000020000000fe0041
[    76.007] (II) intel(0):     554f0a202020202020202020000000fe
[    76.007] (II) intel(0):     004231353658573032205632200a00c0
[    76.007] (II) intel(0): EDID vendor "AUO", prod id 8940
[    76.007] (II) intel(0): Printing DDC gathered Modelines:
[    76.007] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    76.007] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    76.007] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    76.007] (II) intel(0): Printing probed modes for output LVDS1
[    76.007] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    76.007] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    76.007] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    76.007] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    76.007] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    76.007] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    76.007] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    76.069] (II) intel(0): EDID for output VGA1
[    76.069] (II) intel(0): Manufacturer: SAM  Model: 117  Serial#: 1279406391
[    76.069] (II) intel(0): Year: 2006  Week: 4
[    76.069] (II) intel(0): EDID Version: 1.3
[    76.069] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    76.069] (II) intel(0): Sync:  Separate
[    76.069] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 23
[    76.069] (II) intel(0): Gamma: 2.20
[    76.069] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[    76.069] (II) intel(0): Default color space is primary color space
[    76.069] (II) intel(0): First detailed timing is preferred mode
[    76.069] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    76.069] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    76.069] (II) intel(0): Supported established timings:
[    76.069] (II) intel(0): 720x400@70Hz
[    76.069] (II) intel(0): 640x480@60Hz
[    76.069] (II) intel(0): 640x480@67Hz
[    76.069] (II) intel(0): 640x480@72Hz
[    76.069] (II) intel(0): 640x480@75Hz
[    76.069] (II) intel(0): 800x600@56Hz
[    76.069] (II) intel(0): 800x600@60Hz
[    76.069] (II) intel(0): 800x600@72Hz
[    76.069] (II) intel(0): 800x600@75Hz
[    76.069] (II) intel(0): 832x624@75Hz
[    76.069] (II) intel(0): 1024x768@60Hz
[    76.069] (II) intel(0): 1024x768@70Hz
[    76.069] (II) intel(0): 1024x768@75Hz
[    76.069] (II) intel(0): 1152x864@75Hz
[    76.069] (II) intel(0): Manufacturer's mask: 0
[    76.069] (II) intel(0): Supported standard timings:
[    76.069] (II) intel(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[    76.069] (II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[    76.069] (II) intel(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
[    76.069] (II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    76.069] (II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    76.069] (II) intel(0): Supported detailed timing:
[    76.069] (II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
[    76.069] (II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
[    76.069] (II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
[    76.069] (II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 71 kHz, PixClock max 115 MHz
[    76.069] (II) intel(0): Monitor name: SyncMaster
[    76.069] (II) intel(0): Serial No: HMAA136870
[    76.069] (II) intel(0): EDID (in hex):
[    76.069] (II) intel(0):     00ffffffffffff004c2d17013731424c
[    76.069] (II) intel(0):     04100103681f17782eee91a3544c9926
[    76.069] (II) intel(0):     0f5054bfee806159455931598180714f
[    76.069] (II) intel(0):     010101010101ea240060410028303060
[    76.069] (II) intel(0):     130038ea1000001e000000fd0032a01e
[    76.069] (II) intel(0):     470b000a202020202020000000fc0053
[    76.069] (II) intel(0):     796e634d61737465720a2020000000ff
[    76.069] (II) intel(0):     00484d41413133363837300a2020002e
[    76.069] (II) intel(0): Printing probed modes for output VGA1
[    76.069] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    76.069] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    76.069] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    76.069] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    76.069] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    76.069] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    76.069] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    76.069] (II) intel(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    76.069] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    76.069] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    76.069] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    76.069] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    76.069] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    76.069] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    76.069] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    76.069] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    76.069] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    76.069] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    76.074] (II) intel(0): EDID for output HDMI1
[    76.075] (II) intel(0): EDID for output DP1
[    76.075] (II) intel(0): Output LVDS1 connected
[    76.075] (II) intel(0): Output VGA1 connected
[    76.075] (II) intel(0): Output HDMI1 disconnected
[    76.075] (II) intel(0): Output DP1 disconnected
[    76.075] (II) intel(0): Using exact sizes for initial modes
[    76.075] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    76.075] (II) intel(0): Output VGA1 using initial mode 1024x768
[    76.075] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    76.075] (II) intel(0): Kernel page flipping support detected, enabling
[    76.075] (**) intel(0): Display dimensions: (340, 190) mm
[    76.075] (**) intel(0): DPI set to (76, 102)
[    76.075] (II) Loading sub module "fb"
[    76.075] (II) LoadModule: "fb"
[    76.075] (II) Loading /usr/lib/xorg/modules/libfb.so
[    76.076] (II) Module fb: vendor="X.Org Foundation"
[    76.076]     compiled for 1.10.1, module version = 1.0.0
[    76.076]     ABI class: X.Org ANSI C Emulation, version 0.4
[    76.076] (II) UnloadModule: "vesa"
[    76.076] (II) Unloading vesa
[    76.076] (II) UnloadModule: "fbdev"
[    76.076] (II) Unloading fbdev
[    76.076] (II) UnloadModule: "fbdevhw"
[    76.076] (II) Unloading fbdevhw
[    76.076] (==) Depth 24 pixmap format is 32 bpp
[    76.076] (==) intel(0): VideoRam: 262144 KB
[    76.076] (II) intel(0): [DRI2] Setup complete
[    76.076] (II) intel(0): [DRI2]   DRI driver: i965
[    76.076] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    76.082] (II) UXA(0): Driver registered support for the following operations:
[    76.082] (II)         solid
[    76.082] (II)         copy
[    76.082] (II)         composite (RENDER acceleration)
[    76.082] (II)         put_image
[    76.082] (II)         get_image
[    76.082] (==) intel(0): Backing store disabled
[    76.082] (==) intel(0): Silken mouse enabled
[    76.082] (II) intel(0): Initializing HW Cursor
[    76.310] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    76.311] (==) intel(0): DPMS enabled
[    76.311] (==) intel(0): Intel XvMC decoder enabled
[    76.311] (II) intel(0): Set up textured video
[    76.311] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    76.311] (II) intel(0): direct rendering: DRI2 Enabled
[    76.311] (==) intel(0): hotplug detection: "enabled"
[    76.311] (--) RandR disabled
[    76.311] (II) Initializing built-in extension Generic Event Extension
[    76.311] (II) Initializing built-in extension SHAPE
[    76.311] (II) Initializing built-in extension MIT-SHM
[    76.311] (II) Initializing built-in extension XInputExtension
[    76.311] (II) Initializing built-in extension XTEST
[    76.311] (II) Initializing built-in extension BIG-REQUESTS
[    76.311] (II) Initializing built-in extension SYNC
[    76.311] (II) Initializing built-in extension XKEYBOARD
[    76.311] (II) Initializing built-in extension XC-MISC
[    76.311] (II) Initializing built-in extension SECURITY
[    76.311] (II) Initializing built-in extension XINERAMA
[    76.311] (II) Initializing built-in extension XFIXES
[    76.311] (II) Initializing built-in extension RENDER
[    76.311] (II) Initializing built-in extension RANDR
[    76.311] (II) Initializing built-in extension COMPOSITE
[    76.311] (II) Initializing built-in extension DAMAGE
[    76.311] (II) Initializing built-in extension GESTURE
[    76.312] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    76.315] (II) intel(0): Setting screen physical size to 270 x 203
[    76.321] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    76.328] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    76.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    76.328] (II) LoadModule: "evdev"
[    76.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    76.328] (II) Module evdev: vendor="X.Org Foundation"
[    76.328]     compiled for 1.10.0.902, module version = 2.6.0
[    76.328]     Module class: X.Org XInput Driver
[    76.328]     ABI class: X.Org XInput driver, version 12.3
[    76.328] (II) Using input driver 'evdev' for 'Power Button'
[    76.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    76.328] (**) Power Button: always reports core events
[    76.328] (**) Power Button: Device: "/dev/input/event3"
[    76.360] (--) Power Button: Found keys
[    76.360] (II) Power Button: Configuring as keyboard
[    76.360] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    76.360] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    76.360] (**) Option "xkb_rules" "evdev"
[    76.360] (**) Option "xkb_model" "pc105"
[    76.360] (**) Option "xkb_layout" "us"
[    76.361] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    76.361] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    76.361] (II) Using input driver 'evdev' for 'Video Bus'
[    76.361] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    76.361] (**) Video Bus: always reports core events
[    76.361] (**) Video Bus: Device: "/dev/input/event9"
[    76.361] (--) Video Bus: Found keys
[    76.361] (II) Video Bus: Configuring as keyboard
[    76.361] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9/event9"
[    76.361] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    76.361] (**) Option "xkb_rules" "evdev"
[    76.361] (**) Option "xkb_model" "pc105"
[    76.361] (**) Option "xkb_layout" "us"
[    76.361] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    76.361] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    76.361] (II) Using input driver 'evdev' for 'Video Bus'
[    76.361] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    76.361] (**) Video Bus: always reports core events
[    76.361] (**) Video Bus: Device: "/dev/input/event10"
[    76.361] (--) Video Bus: Found keys
[    76.361] (II) Video Bus: Configuring as keyboard
[    76.361] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input10/event10"
[    76.362] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    76.362] (**) Option "xkb_rules" "evdev"
[    76.362] (**) Option "xkb_model" "pc105"
[    76.362] (**) Option "xkb_layout" "us"
[    77.460] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    77.460] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    77.460] (II) Using input driver 'evdev' for 'Power Button'
[    77.460] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.460] (**) Power Button: always reports core events
[    77.460] (**) Power Button: Device: "/dev/input/event0"
[    77.520] (--) Power Button: Found keys
[    77.520] (II) Power Button: Configuring as keyboard
[    77.520] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/PNP0C0C:00/input/input0/event0"
[    77.520] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    77.520] (**) Option "xkb_rules" "evdev"
[    77.520] (**) Option "xkb_model" "pc105"
[    77.520] (**) Option "xkb_layout" "us"
[    77.520] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    77.520] (II) No input driver/identifier specified (ignoring)
[    77.520] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    77.520] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    77.520] (II) Using input driver 'evdev' for 'Sleep Button'
[    77.520] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.520] (**) Sleep Button: always reports core events
[    77.520] (**) Sleep Button: Device: "/dev/input/event2"
[    77.650] (--) Sleep Button: Found keys
[    77.650] (II) Sleep Button: Configuring as keyboard
[    77.650] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/PNP0C0E:00/input/input2/event2"
[    77.650] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    77.650] (**) Option "xkb_rules" "evdev"
[    77.650] (**) Option "xkb_model" "pc105"
[    77.650] (**) Option "xkb_layout" "us"
[    77.653] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[    77.653] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    77.653] (II) Using input driver 'evdev' for '1.3M WebCam'
[    77.653] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.653] (**) 1.3M WebCam: always reports core events
[    77.653] (**) 1.3M WebCam: Device: "/dev/input/event8"
[    77.653] (--) 1.3M WebCam: Found keys
[    77.653] (II) 1.3M WebCam: Configuring as keyboard
[    77.653] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input8/event8"
[    77.653] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    77.653] (**) Option "xkb_rules" "evdev"
[    77.653] (**) Option "xkb_model" "pc105"
[    77.653] (**) Option "xkb_layout" "us"
[    77.654] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event12)
[    77.654] (II) No input driver/identifier specified (ignoring)
[    77.654] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event13)
[    77.654] (II) No input driver/identifier specified (ignoring)
[    77.655] (II) config/udev: Adding input device HID 04b4:0033 (/dev/input/event5)
[    77.655] (**) HID 04b4:0033: Applying InputClass "evdev pointer catchall"
[    77.655] (II) Using input driver 'evdev' for 'HID 04b4:0033'
[    77.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.655] (**) HID 04b4:0033: always reports core events
[    77.655] (**) HID 04b4:0033: Device: "/dev/input/event5"
[    77.655] (--) HID 04b4:0033: Found 9 mouse buttons
[    77.655] (--) HID 04b4:0033: Found scroll wheel(s)
[    77.655] (--) HID 04b4:0033: Found relative axes
[    77.655] (--) HID 04b4:0033: Found x and y relative axes
[    77.655] (II) HID 04b4:0033: Configuring as mouse
[    77.655] (II) HID 04b4:0033: Adding scrollwheel support
[    77.655] (**) HID 04b4:0033: YAxisMapping: buttons 4 and 5
[    77.655] (**) HID 04b4:0033: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    77.655] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0/input/input5/event5"
[    77.655] (II) XINPUT: Adding extended input device "HID 04b4:0033" (type: MOUSE)
[    77.655] (II) HID 04b4:0033: initialized for relative axes.
[    77.655] (**) HID 04b4:0033: (accel) keeping acceleration scheme 1
[    77.655] (**) HID 04b4:0033: (accel) acceleration profile 0
[    77.656] (**) HID 04b4:0033: (accel) acceleration factor: 2.000
[    77.656] (**) HID 04b4:0033: (accel) acceleration threshold: 4
[    77.656] (II) config/udev: Adding input device HID 04b4:0033 (/dev/input/mouse0)
[    77.656] (II) No input driver/identifier specified (ignoring)
[    77.656] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event6)
[    77.656] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    77.656] (II) Using input driver 'evdev' for '  USB Keyboard'
[    77.656] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.656] (**)   USB Keyboard: always reports core events
[    77.656] (**)   USB Keyboard: Device: "/dev/input/event6"
[    77.660] (--)   USB Keyboard: Found keys
[    77.660] (II)   USB Keyboard: Configuring as keyboard
[    77.660] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input6/event6"
[    77.660] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    77.660] (**) Option "xkb_rules" "evdev"
[    77.660] (**) Option "xkb_model" "pc105"
[    77.660] (**) Option "xkb_layout" "us"
[    77.660] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event7)
[    77.660] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    77.660] (II) Using input driver 'evdev' for '  USB Keyboard'
[    77.660] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.660] (**)   USB Keyboard: always reports core events
[    77.660] (**)   USB Keyboard: Device: "/dev/input/event7"
[    77.660] (--)   USB Keyboard: Found keys
[    77.660] (II)   USB Keyboard: Configuring as keyboard
[    77.660] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.1/input/input7/event7"
[    77.660] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    77.660] (**) Option "xkb_rules" "evdev"
[    77.660] (**) Option "xkb_model" "pc105"
[    77.661] (**) Option "xkb_layout" "us"
[    77.663] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    77.663] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    77.663] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    77.663] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.663] (**) AT Translated Set 2 keyboard: always reports core events
[    77.663] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    77.663] (--) AT Translated Set 2 keyboard: Found keys
[    77.663] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    77.663] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    77.663] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    77.663] (**) Option "xkb_rules" "evdev"
[    77.663] (**) Option "xkb_model" "pc105"
[    77.663] (**) Option "xkb_layout" "us"
[    77.664] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event11)
[    77.664] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    77.664] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    77.664] (II) LoadModule: "synaptics"
[    77.664] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    77.664] (II) Module synaptics: vendor="X.Org Foundation"
[    77.664]     compiled for 1.10.1, module version = 1.3.99
[    77.664]     Module class: X.Org XInput Driver
[    77.664]     ABI class: X.Org XInput driver, version 12.3
[    77.664] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    77.664] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    77.664] (**) ETPS/2 Elantech Touchpad: always reports core events
[    77.664] (**) Option "Device" "/dev/input/event11"
[    77.670] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    77.670] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    77.670] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[    77.670] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    77.670] (--) ETPS/2 Elantech Touchpad: invalid pressure range.  defaulting to 0 - 256
[    77.670] (--) ETPS/2 Elantech Touchpad: invalid finger width range.  defaulting to 0 - 16
[    77.680] (--) ETPS/2 Elantech Touchpad: touchpad found
[    77.680] (**) ETPS/2 Elantech Touchpad: always reports core events
[    77.680] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    77.680] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    77.680] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    77.680] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    77.680] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[    77.680] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    77.680] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    77.680] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    77.680] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    77.690] (II) ETPS/2 Elantech Touchpad: failed to open grail, no gesture support
[    77.690] (--) ETPS/2 Elantech Touchpad: touchpad found
[    77.690] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    77.690] (II) No input driver/identifier specified (ignoring)
[    77.898] (II) intel(0): EDID vendor "AUO", prod id 8940
[    77.898] (II) intel(0): Printing DDC gathered Modelines:
[    77.898] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    77.966] (II) intel(0): EDID vendor "AUO", prod id 8940
[    77.966] (II) intel(0): Printing DDC gathered Modelines:
[    77.966] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    78.067] (II) intel(0): EDID vendor "AUO", prod id 8940
[    78.067] (II) intel(0): Printing DDC gathered Modelines:
[    78.067] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    78.136] (II) intel(0): EDID vendor "AUO", prod id 8940
[    78.136] (II) intel(0): Printing DDC gathered Modelines:
[    78.136] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    88.911] (II) intel(0): EDID vendor "AUO", prod id 8940
[    88.911] (II) intel(0): Printing DDC gathered Modelines:
[    88.911] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    88.976] (II) intel(0): EDID vendor "AUO", prod id 8940
[    88.976] (II) intel(0): Printing DDC gathered Modelines:
[    88.976] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    89.698] (II) intel(0): EDID vendor "AUO", prod id 8940
[    89.698] (II) intel(0): Printing DDC gathered Modelines:
[    89.698] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    89.704] (II) intel(0): EDID vendor "AUO", prod id 8940
[    89.704] (II) intel(0): Printing DDC gathered Modelines:
[    89.704] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    89.917] (II) intel(0): EDID vendor "AUO", prod id 8940
[    89.917] (II) intel(0): Printing DDC gathered Modelines:
[    89.917] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    89.926] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    90.104] (II) intel(0): EDID vendor "AUO", prod id 8940
[    90.104] (II) intel(0): Printing DDC gathered Modelines:
[    90.104] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    90.112] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    90.238] (II) intel(0): EDID vendor "AUO", prod id 8940
[    90.238] (II) intel(0): Printing DDC gathered Modelines:
[    90.238] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    90.296] (II) intel(0): EDID vendor "AUO", prod id 8940
[    90.296] (II) intel(0): Printing DDC gathered Modelines:
[    90.296] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    90.315] (II) intel(0): EDID vendor "AUO", prod id 8940
[    90.315] (II) intel(0): Printing DDC gathered Modelines:
[    90.315] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)

```it uses a directory as configuration not a file and there is no xorg.conf file in this directory. but i need it in file format. So how can I get this configuration file.
Sorry for my bad english.
Cheers...

---

### Post by el_koraco on 2011-07-31
the xorg configuration is located in /etc/X11/xorg.conf. But that only applies when you install a binary video driver. if you have an Intel card, or are using the open source drivers for ATI or Nvidia, the file will not be created. What exactly is it that you need to do and why?

---

### Post by electrogenius on 2011-07-31
X server does not start after executing nvidia-xconfig. nvidia-xconfig can't find xorg.conf and then it creates one xorg.conf but after reboot just black screen. I check the log and see the error that it cant find the screen.
this is the xorg.conf generated by nvidia-xconfig
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

``````

[    18.074] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.074] X Protocol Version 11, Revision 0
[    18.074] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.074] Current Operating System: Linux electrogenius-EasyNote-TK85 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64
[    18.074] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=2522e9f9-575f-40a3-b52c-82b5bc8caa7f ro quiet splash vt.handoff=7
[    18.074] Build Date: 21 May 2011  11:48:41AM
[    18.074] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    18.074] Current version of pixman: 0.20.2
[    18.074]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.075] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.075] (==) Log file: "/var/log/Xorg.2.log", Time: Sun Jul 31 11:41:28 2011
[    18.075] (==) **Using config file: "/etc/X11/xorg.conf"**
[    18.075] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.075] Data incomplete in file /etc/X11/xorg.conf
    Undefined Screen "Screen3" referenced by ServerLayout "X.org Configured".
[    18.075] (EE) Problem parsing the config file
[    18.075] (EE) Error parsing the config file
[    18.075] 
[B]Fatal server error:
[    18.075] no screens found
[/B][    18.075] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    18.075] Please also check the log file at "/var/log/Xorg.2.log" for additional information.
[    18.075] 
[    18.075]  ddxSigGiveUp: Closing log

```

---

### Post by realzippy on 2011-07-31
Edit.
just noticed:

```
[    75.841] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge

```
So I guess you have an Optimus laptop ?!
What does
```
lspci |grep VGA
```
show?

---

### Post by electrogenius on 2011-07-31
```

lspci |grep VGA

```
 
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

```

---

### Post by realzippy on 2011-07-31
Ok,another Optimus problem.
Suggest to read [this]("http://ubuntuforums.org/showthread.php?p=10304516#post10304516")....

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

