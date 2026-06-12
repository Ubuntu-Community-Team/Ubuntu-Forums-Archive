---
title: "PowerPC + mach64 xorg driver == FAIL ??"
date: 2009-07-11
forum: Apple Hardware Users
---

### Post by KittyKitty on 2009-07-11
My problem is with getting xorg to work properly on my iMac
I have tried dpkg-reconfigure -phigh xserver-xorg
X -configure
and hand editing files to try to get the monitor to run at an "acceptable" refresh rate and resolution to no avail

the only way i can get my screen to output any Xserver is by using driver "fbdev"

when i use mach64 it'll load up, log into the auto login user, eventually start the vino server which i can connect to and use the computer with limited 3d acceleration, but the built in crt will just go into powersave mode (much like it was outside of the vertical/horizontal frequencies)

i have attached my xorg.conf file that i've been testing and using, and the xorg.log file from such testing
Plz help i'm completely out of ideas that don't involve using it as a boat anchor
```
Linux ubuntu-Imac 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc GNU/Linux
```
```
root@ubuntu-Imac:/etc/X11# lspci
00:00.0 Host bridge: Motorola MPC106 [Grackle] (rev 40)
00:10.0 Class ff00: Apple Computer Inc. Paddington Mac I/O
00:12.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] (rev 3a)
00:14.0 USB Controller: OPTi Inc. 82C861 (rev 10)

root@ubuntu-Imac:/etc/X11# cat ~/xorg.conf.new
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "dri"
        Load  "dbe"
        Load  "extmod"
        Load  "record"
        Load  "glx"
        Load  "dri2"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "probe_sparse"              # [<bool>]
        #Option     "accel"                     # [<bool>]
        #Option     "crt_display"               # [<bool>]
        #Option     "composite_sync"            # [<bool>]
        #Option     "hw_cursor"                 # [<bool>]
        #Option     "force_pci_mode"            # [<bool>]
        #Option     "dma_mode"                  # <str>
        #Option     "agp_mode"                  # <i>
        #Option     "agp_size"                  # <i>
        #Option     "local_textures"            # [<bool>]
        #Option     "buffer_size"               # <i>
        #Option     "mmio_cache"                # [<bool>]
        #Option     "test_mmio_cache"           # [<bool>]
        #Option     "panel_display"             # [<bool>]
        #Option     "reference_clock"           # <freq>
        #Option     "shadow_fb"                 # [<bool>]
        #Option     "sw_cursor"                 # [<bool>]
        #Option     "AccelMethod"               # <str>
        #Option     "RenderAccel"               # [<bool>]
        Identifier  "Card0"
        Driver      "mach64"
        VendorName  "ATI Technologies Inc"
        BoardName   "3D Rage IIC 215IIC [Mach64 GT IIC]"
        BusID       "PCI:0:18:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```
```
root@ubuntu-Imac:/etc/X11# cat /var/log/Xorg.1.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu-Imac 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc
Build Date: 09 April 2009  02:10:13AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@ross.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Jul 11 08:51:36 2009
(++) Using config file: "/root/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x1e80
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0@0:18:0) ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] rev 58, Mem @ 0x81000000/16777216, 0x80881000/4096, I/O @ 0x00000c00/256, BIOS @ 0x????????/131072
(II) No APM support in BIOS or kernel
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
        compiled for 1.5.99.3, module version = 6.8.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) MACH64: Driver for ATI Mach64 chipsets
(II) Primary Device is: PCI 00@00:12:0
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(==) MACH64(0): Depth 24, (--) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 0:18:0 detected.
(II) MACH64(0): BIOS Data:  BIOSSize=0x0000, ROMTable=0x0000.
(II) MACH64(0): BIOS Data:  ClockTable=0x0000, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0000.
(II) MACH64(0): BIOS Data:  I2CType=0x00, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage IIc graphics controller detected.
(--) MACH64(0): Chip type 4756 "GV", version 2, foundry UMC, class 0, revision 0x00.
(--) MACH64(0): PCI bus interface detected.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
        of this adapter, please see http://gatos.sf.net.
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(II) MACH64(0): Storing hardware cursor image at 0x811FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0x81800000.
(!!) MACH64(0): Virtual resolutions will be limited to 2047 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0x80881400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0x80881000.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 2048 kB of SGRAM (1:1) detected (using 2047 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 82.676 MHz;  Refresh rate code 6.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) MACH64(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(WW) MACH64(0): Unable to estimate virtual size
(II) MACH64(0): Maximum clock: 165.00 MHz
(II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "320x240" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "512x384" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "832x624" (hsync out of range)
(II) MACH64(0): Not using default mode "416x312" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "720x450" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x540" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(--) MACH64(0): Virtual size is 800x600 (pitch 800)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) MACH64(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.2.1
        ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(--) MACH64(0): ImpacTV chip ID 0x8A detected.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): Direct rendering is not supported for ATI chips earlier than the ATI 3D Rage Pro.
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0):         800 x 55 rectangle at 0,600
(II) MACH64(0):         32 x 56 rectangle at 0,600
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Setting up tile and stipple cache:
                7 32x55 slots
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(II) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
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
(II) config/hal: Adding input device Alps Electric Apple USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) Alps Electric Apple USB Keyboard: always reports core events
(**) Alps Electric Apple USB Keyboard: Device: "/dev/input/event1"
(II) Alps Electric Apple USB Keyboard: Found keys
(II) Alps Electric Apple USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric Apple USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Alps Electric Apple USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Alps Electric Apple USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Alps Electric Apple USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Mouseemu virtual keyboard
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event4"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Mouseemu virtual keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Mouseemu virtual keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Mouseemu virtual keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Mouseemu virtual mouse
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event5"
(II) Mouseemu virtual mouse: Found 3 mouse buttons
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
(**) Mouseemu virtual mouse: (accel) filter chain progression: 2.00
(**) Mouseemu virtual mouse: (accel) filter stage 0: 20.00 ms
(**) Mouseemu virtual mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
(II) Alps Electric Apple USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Mouseemu virtual keyboard: Close
(II) UnloadModule: "evdev"
(II) Mouseemu virtual mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB-PS/2 Optical Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

### Post by KittyKitty on 2009-08-16
bump ?

I am still trying to address this issue, have not found any further information or help from online sources.

If anyone is familiar or can point me to a website that will show me the futility of my attempts, that would be great.

---

### Post by jhf on 2009-11-24
You need to add
```
        HorizSync 59-61
        VertRefresh 43-117
```to the "Monitor" section of your xorg.conf.

Since this is a very early iMac, you will also need to add
```
        DefaultDepth    16
```just below
```
        Monitor         "Configured Monitor"
```in the "Screen" section, 'cause your iMac doesn't have enough video RAM do to 1024x768 at 32bit color depth.

---

