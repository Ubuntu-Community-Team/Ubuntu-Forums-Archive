---
title: "radeon, radeondrmfb and Radeon HD 4670"
date: 2019-08-20
forum: Apple Hardware Users
---

### Post by edbch on 2019-08-20
Hello all.
Argh, that will be a long post, but I'm putting the initial steps so others can be beneficiated by the hours I had spent on it.
Fresh install of ubuntu 18.04 on a old iMac digged out of the garage. Installation can only be done by using the 'nomodeset' on kernel command line. After Installation, it keep the same behavior, ie, blank screen without the nomodeset kernel parameter, and the fbdev is the only working option. 
Looking at the Xorg log, 

```
...
[   101.096] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
...
    MULLINS, KAVERI, HAWAII
[   101.105] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   101.105] (II) FBDEV: driver for framebuffer: fbdev
[   101.105] (EE) open /dev/dri/card0: No such file or directory
[   101.105] (WW) Falling back to old probe method for modesetting
[   101.105] (EE) open /dev/dri/card0: No such file or directory
[   101.105] (II) Loading sub module "fbdevhw"
[   101.105] (II) LoadModule: "fbdevhw"
[   101.106] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   101.106] (II) Module fbdevhw: vendor="X.Org Foundation"
[   101.106]     compiled for 1.20.4, module version = 0.0.2
[   101.106]     ABI class: X.Org Video Driver, version 24.0
[   101.106] (**) FBDEV(1): claimed PCI slot 1@0:0:0
...
[   101.107] (II) Unloading radeon
...
```

The important line seems to be 

```
[   101.105] (EE) open /dev/dri/card0: No such file or directory
```

That i solved by putting the radeon module in the initrd, to have the early kms magic. Of corse the blank screen occurs sonner now.

Now, without the nomodeset parameter, the xorg log show that the card is being recognized by the radeon module

```
...
    MULLINS, KAVERI, HAWAII
(II) modesetting: Driver for Modesetting Kernel Drivers: kms
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(II) [KMS] Kernel modesetting enabled.
(WW) Falling back to old probe method for modesetting
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.20.4, module version = 0.0.2
(II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon HD 4670" (ChipID = 0x9488)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.20.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/libglamoregl.so
(II) Module glamoregl: vendor="X.Org Foundation"
    compiled for 1.20.4, module version = 1.0.1
(II) RADEON(0): glamor X acceleration enabled on AMD RV730 (DRM 2.50.0 / 5.0.0-25-generic, LLVM 8.0.0)
(II) RADEON(0): glamor detected, initialising EGL layer.
(II) RADEON(0): KMS Color Tiling: enabled
(II) RADEON(0): KMS Color Tiling 2D: enabled
(==) RADEON(0): TearFree property default: auto
(II) RADEON(0): KMS Pageflipping: enabled
(II) RADEON(0): Output DisplayPort-0 has no monitor section
(II) RADEON(0): Output eDP has no monitor section
(II) RADEON(0): Output VGA-0 has no monitor section
(WW) RADEON(0): 3 ZaphodHeads crtcs unavailable. Some outputs will stay off.
(II) RADEON(0): EDID for output DisplayPort-0
(II) RADEON(0): EDID for output eDP
(II) RADEON(0): Manufacturer: APP  Model: 9cdd  Serial#: 0
(II) RADEON(0): Year: 2010  Week: 10
(II) RADEON(0): EDID Version: 1.4
(II) RADEON(0): Digital Display Input
(II) RADEON(0): 8 bits per channel
(II) RADEON(0): Digital interface is DisplayPort
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): Preferred mode is native pixel format and refresh rate
(II) RADEON(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.620
(II) RADEON(0): blueX: 0.146 blueY: 0.050   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 138.5 MHz   Image Size:  475 x 267 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
(II) RADEON(0): Unknown vendor-specific block 2
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610dd9c00000000
(II) RADEON(0):     0a140104a5301b78226fb1a7554c9e25
(II) RADEON(0):     0c505400000001010101010101010101
(II) RADEON(0):     0101010101011a3680a070381f403020
(II) RADEON(0):     3500db0b1100001a0000000201061001
(II) RADEON(0):     0a010000000000000000000000fc0043
(II) RADEON(0):     6f6c6f72204c43440a20202000000000
(II) RADEON(0):     00000000000000000000000000000055
(II) RADEON(0): Printing probed modes for output eDP
(II) RADEON(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.36  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1400x1050"x60.0  121.79  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.10  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x60.0  106.68  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (56.0 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  101.34  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.8 kHz)
(II) RADEON(0): Modeline "1280x854"x60.0   89.34  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.2 kHz)
(II) RADEON(0): Modeline "1280x800"x60.0   83.71  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.65  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.9 kHz)
(II) RADEON(0): Modeline "1152x768"x59.9   71.95  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.53  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x60.0   38.31  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "848x480"x59.9   31.65  848 872 952 1056  480 483 493 500 -hsync +vsync (30.0 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   26.85  720 744 808 896  480 483 493 500 -hsync +vsync (30.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   23.98  640 664 720 800  480 483 487 500 -hsync +vsync (30.0 kHz)
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output DisplayPort-0 disconnected
(II) RADEON(0): Output eDP connected
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output eDP using initial mode 1920x1080 +0+0
(II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:10000000 visible:f4ca000
(==) RADEON(0): DPI set to (96, 96)
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Unloading modesetting
(II) Unloading fbdev
(II) Unloading fbdevhw
(II) Unloading vesa
(II) RADEON(0): [DRI2] Setup complete
(II) RADEON(0): [DRI2]   DRI driver: r600
(II) RADEON(0): [DRI2]   VDPAU driver: r600
(II) RADEON(0): Front buffer size: 8100K
(II) RADEON(0): VRAM usage limit set to 218278K
(II) RADEON(0): SYNC extension fences enabled
(II) RADEON(0): Present extension enabled
(==) RADEON(0): DRI3 enabled
(==) RADEON(0): Backing store enabled
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Use GLAMOR acceleration.
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video (glamor)
(II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
(II) RADEON(0): [XvMC] Extension initialized.
(II) SELinux: Disabled on system
(II) AIGLX: Loaded and initialized r600
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 508 x 285
```

Now, is strange to me that it finds 2 monitors, being just one connected and, even finding 2, no image is showed on the screen.  The "Xorg -config" output show 2 monitors and 2 gpu cards, card0 at "PCI:1:0:0" and card1 at "PCI:1:0:1". It doesn't have 2 gpu cards. The second card is the audio card:


```
# lspci | grep "^01:"
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730/M96-XT [Mobility Radeon HD 4670]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
```


Another thing I dont understand is this Xorg log line: 

```
(II) RADEON(0): Setting screen physical size to 508 x 285
``` 

Could the xorg selecting the wrong card/monitor as output? dmesg shows that the radeon module is finding different outputs

```
#dmesg | egrep 'drm|radeon'
[    1.859628] [drm] radeon kernel modesetting enabled.
[    1.860925] fb0: switching to radeondrmfb from EFI VGA
[    1.862536] [drm] initializing kernel modesetting (RV730 0x1002:0x9488 0x106B:0x00B6 0x00).
[    2.154446] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[    2.154450] radeon 0000:01:00.0: GTT: 1024M 0x0000000010000000 - 0x000000004FFFFFFF
[    2.154457] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.154459] [drm] RAM width 128bits DDR
[    2.154534] [drm] radeon: 256M of VRAM memory ready
[    2.154536] [drm] radeon: 1024M of GTT memory ready.
[    2.154544] [drm] Loading RV730 Microcode
[    2.154603] [drm] External GPIO thermal controller with fan control
[    2.157819] [drm] radeon: dpm initialized
[    2.157889] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    2.158729] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    2.168019] [drm] PCIE GART of 1024M enabled (table at 0x000000000014C000).
[    2.168067] radeon 0000:01:00.0: WB enabled
[    2.168071] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0x(____ptrval____)
[    2.168074] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000010000c0c and cpu addr 0x(____ptrval____)
[    2.168285] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0x(____ptrval____)
[    2.168290] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.168292] [drm] Driver supports precise vblank timestamp query.
[    2.168294] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    2.168342] radeon 0000:01:00.0: radeon: using MSI.
[    2.168365] [drm] radeon: irq initialized.
[    2.214592] [drm] ring test on 0 succeeded in 1 usecs
[    2.214602] [drm] ring test on 3 succeeded in 2 usecs
[    2.389266] [drm] ring test on 5 succeeded in 1 usecs
[    2.389271] [drm] UVD initialized successfully.
[    2.389379] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.389398] [drm] ib test on ring 3 succeeded in 0 usecs
[    3.046089] [drm] ib test on ring 5 succeeded
[    3.054023] [drm] radeon atom DIG backlight initialized
[    3.054034] [drm] Radeon Display Connectors
[    3.054038] [drm] Connector 0:
[    3.054042] [drm]   DP-1
[    3.054046] [drm]   HPD1
[    3.054051] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    3.054057] [drm]   Encoders:
[    3.054061] [drm]     DFP1: INTERNAL_UNIPHY
[    3.054065] [drm] Connector 1:
[    3.054068] [drm]   eDP-1
[    3.054071] [drm]   HPD2
[    3.054076] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    3.054081] [drm]   Encoders:
[    3.054085] [drm]     LCD1: INTERNAL_UNIPHY
[    3.054089] [drm] Connector 2:
[    3.054092] [drm]   VGA-1
[    3.054096] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    3.054102] [drm]   Encoders:
[    3.054106] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    3.136779] [drm] fb mappable at 0xC034D000
[    3.136784] [drm] vram apper at 0xC0000000
[    3.136786] [drm] size 8294400
[    3.136787] [drm] fb depth is 24
[    3.136789] [drm]    pitch is 7680
[    3.136990] fbcon: radeondrmfb (fb0) is primary device
[    3.182447] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    3.202093] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
```


The screen is blank way before gdm3 kicks in, so I'm thinking the problem is the seletion, or correct detection of the output, perhaps by the framebuffer on boot.

Could someone please help me to debug the problem? Thanks.

---

### Post by QIII on 2019-08-20
Moved to Apple Hardware Users as a more appropriate sub-forum.

---

### Post by edbch on 2019-08-21
Just a upgrade on the effort. 

The problem of two card being detected by X goes away by removing the amdgpu xrorg module, leaving just radeon.

While still using early kms enabled with radeon, I found that all Display Connectors were being listed as disabled.

```
# for p in /sys/class/drm/*/enabled; do con=${p%/enabled}; echo -n "${con#*/card?-}: "; cat $p; done
DP-1: disabled
eDP-1: disabled
VGA-1: disabled
```

I tried different combinations of kernel parameters to force them to activate, including all at the same time.

```
"video=DP-1:e video=VGA-1:e video=eDP-1:e"

```

They are listed as enabled and connected even when they are all enabled at the same time. But no image ever appeared on the screen. As soon as the radeon module is loaded the screen goes blank.

Interestingly, disabling early kms, ie, removing the radeon module from initrd, and disabling module loading on boot time with radeon.modeset = 0 , disabling gdm3, and loading radeon module manually after boot is complete, one of the connectors is now listed as enabled and connected without the need to force anything kernel command line.

```
# cat /sys/class/drm/card0-eDP-1/{dpms,enabled,modes,status}
On
enabled
1920x1080
1680x1050
1400x1050
1280x1024
1440x900
1280x960
1280x854
1280x800
1280x720
1152x768
1024x768
800x600
848x480
720x480
640x480
connected

```

Again, no image is displayed. 

I tried deactivate the framebuffer with the kernel parameter nofb, but radeondrmfb is always activated. Is possible to load radeon without framebuffer?

I dont know how to narrow down the problem. Xorg is loaded as if everything is ok, I cant see nothing in the X logs. dmesg says the radeon is loaded, and some radeon internal test are a success. /sys/class/drm says that the card is recognizes and configured, even the screen resolution modes are recognized.

---

### Post by este.el.paz on 2019-09-28
@edbch:

Couple short questions, what iMac are you installing into?  If it's a "PPC" unit then it won't truly run 18.04, 16.04 is the last iteration for PPC.  On my Powermac 3,1 ??  that I ran briefly today running U-mate 16.04 it shows me that "18.04 is available, run do-release-upgrade" . . . but if you run that install there won't be the PPC packages and it will be broken somewhere part way through . . . .  If it's an old iMac you can search the forum for threads on "How to install to an iMac 800" and look around for "abtabt" posts, he has a lot of experience running ubuntu on an iMac 800.

Other question, if this is an intel iMac did you boot from the "efi disk" image??  If you don't boot from that one then the install will be running for a PC . . . .  A friend of mine was having problems installing into an iMac intel C2D and I saw he also had two video cards, but I think he may have gotten it to go through.

Good luck on it.  Otherwise I can't offer too much insight, as on my same Powermac I upgraded the video card from radeon to radeon, but the system doesn't give me video past the splash and a TTY . . . so somewhere in there is a problem . . . computer is just too old to be really useful these days . . . .

---

