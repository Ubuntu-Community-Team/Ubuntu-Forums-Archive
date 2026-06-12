---
title: "TF2 Caused Persistant Video Artifacts"
date: 2012-12-08
forum: Any Other OS
---

### Post by EnigmaticCoder on 2012-12-08
I installed Team Fortress 2, and ever since playing it, I get video artifacts that persist even after rebooting. I'm pretty confident the graphics card is not broken.

[http://i.imgur.com/BPUHT.jpg](http://i.imgur.com/BPUHT.jpg)

Also note that I get similar artifacts when enabling hardware acceleration in flash. They go away when disabled.

I have a feeling it may be related to xorg. Relevant log below:

```

[    33.920] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    33.921] X Protocol Version 11, Revision 0
[    33.921] Build Operating System: Linux 3.6.3-1-ARCH x86_64 
[    33.921] Current Operating System: Linux b1tviolin 3.6.9-1-ARCH #1 SMP PREEMPT Tue Dec 4 08:04:10 CET 2012 x86_64
[    33.921] Kernel command line: BOOT_IMAGE=/vmlinuz-linux root=/dev/mapper/root ro init=/bin/systemd cryptdevice=/dev/sda3:root
[    33.922] Build Date: 08 November 2012  07:09:29PM
[    33.922]  
[    33.925] Current version of pixman: 0.28.0
[    33.930] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    33.930] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.943] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  8 16:25:21 2012
[    34.021] (==) Using config file: "/etc/X11/xorg.conf"
[    34.024] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    34.187] (==) ServerLayout "Layout0"
[    34.187] (**) |-->Screen "Screen0" (0)
[    34.187] (**) |   |-->Monitor "Monitor0"
[    34.187] (**) |   |-->Device "Device0"
[    34.187] (**) |-->Input Device "Keyboard0"
[    34.187] (**) |-->Input Device "Mouse0"
[    34.187] (==) Automatically adding devices
[    34.188] (==) Automatically enabling devices
[    34.188] (==) Automatically adding GPU devices
[    34.426] (WW) The directory "/usr/share/fonts/OTF/" does not exist.
[    34.426] 	Entry deleted from font path.
[    34.453] (WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/100dpi/".
[    34.453] 	Entry deleted from font path.
[    34.453] 	(Run 'mkfontdir' on "/usr/share/fonts/100dpi/").
[    34.564] (==) FontPath set to:
	/usr/share/fonts/misc/,
	/usr/share/fonts/TTF/,
	/usr/share/fonts/Type1/,
	/usr/share/fonts/75dpi/
[    34.564] (==) ModulePath set to "/usr/lib/xorg/modules"
[    34.564] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    34.564] (WW) Disabling Keyboard0
[    34.564] (WW) Disabling Mouse0
[    34.564] (II) Loader magic: 0x7fcc40
[    34.564] (II) Module ABI versions:
[    34.564] 	X.Org ANSI C Emulation: 0.4
[    34.564] 	X.Org Video Driver: 13.1
[    34.564] 	X.Org XInput driver : 18.0
[    34.564] 	X.Org Server Extension : 7.0
[    34.568] (--) PCI:*(0:2:0:0) 10de:0a65:1043:8354 rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xee000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/524288
[    34.568] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    34.586] Initializing built-in extension Generic Event Extension
[    34.589] Initializing built-in extension SHAPE
[    34.591] Initializing built-in extension MIT-SHM
[    34.594] Initializing built-in extension XInputExtension
[    34.597] Initializing built-in extension XTEST
[    34.600] Initializing built-in extension BIG-REQUESTS
[    34.602] Initializing built-in extension SYNC
[    34.605] Initializing built-in extension XKEYBOARD
[    34.607] Initializing built-in extension XC-MISC
[    34.610] Initializing built-in extension SECURITY
[    34.613] Initializing built-in extension XINERAMA
[    34.615] Initializing built-in extension XFIXES
[    34.618] Initializing built-in extension RENDER
[    34.620] Initializing built-in extension RANDR
[    34.622] Initializing built-in extension COMPOSITE
[    34.624] Initializing built-in extension DAMAGE
[    34.626] Initializing built-in extension MIT-SCREEN-SAVER
[    34.628] Initializing built-in extension DOUBLE-BUFFER
[    34.630] Initializing built-in extension RECORD
[    34.632] Initializing built-in extension DPMS
[    34.634] Initializing built-in extension X-Resource
[    34.635] Initializing built-in extension XVideo
[    34.637] Initializing built-in extension XVideo-MotionCompensation
[    34.638] Initializing built-in extension XFree86-VidModeExtension
[    34.640] Initializing built-in extension XFree86-DGA
[    34.641] Initializing built-in extension XFree86-DRI
[    34.642] Initializing built-in extension DRI2
[    34.642] (II) LoadModule: "glx"
[    34.765] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    38.378] (II) Module glx: vendor="NVIDIA Corporation"
[    38.378] 	compiled for 4.0.2, module version = 1.0.0
[    38.378] 	Module class: X.Org Server Extension
[    38.378] (II) NVIDIA GLX Module  310.19  Thu Nov  8 01:12:43 PST 2012
[    38.379] Loading extension GLX
[    38.379] (II) LoadModule: "nvidia"
[    38.380] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    39.001] (II) Module nvidia: vendor="NVIDIA Corporation"
[    39.001] 	compiled for 4.0.2, module version = 1.0.0
[    39.001] 	Module class: X.Org Video Driver
[    39.099] (II) NVIDIA dlloader X Driver  310.19  Thu Nov  8 00:53:33 PST 2012
[    39.099] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    39.137] (++) using VT number 1

[    39.155] (II) Loading sub module "wfb"
[    39.155] (II) LoadModule: "wfb"
[    39.156] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    39.298] (II) Module wfb: vendor="X.Org Foundation"
[    39.298] 	compiled for 1.13.0, module version = 1.0.0
[    39.298] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    39.298] (II) Loading sub module "ramdac"
[    39.299] (II) LoadModule: "ramdac"
[    39.299] (II) Module "ramdac" already built-in
[    39.346] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    39.346] (==) NVIDIA(0): RGB weight 888
[    39.346] (==) NVIDIA(0): Default visual is TrueColor
[    39.346] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.358] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
[    39.358] (**) NVIDIA(0): Enabling 2D acceleration
[    40.085] (II) NVIDIA(GPU-0): Display (COMPAQ CV535 (CRT-0)) does not support NVIDIA 3D
[    40.085] (II) NVIDIA(GPU-0):     Vision stereo.
[    40.100] (II) NVIDIA(GPU-0): Display (ViewSonic A75f (CRT-1)) does not support NVIDIA 3D
[    40.100] (II) NVIDIA(GPU-0):     Vision stereo.
[    40.102] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:2:0:0 (GPU-0)
[    40.102] (--) NVIDIA(0): Memory: 1048576 kBytes
[    40.102] (--) NVIDIA(0): VideoBIOS: 70.18.5f.00.06
[    40.102] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    40.104] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:2:0:0
[    40.104] (--) NVIDIA(0):     COMPAQ CV535 (CRT-0) (connected)
[    40.104] (--) NVIDIA(0):     ViewSonic A75f (CRT-1) (connected)
[    40.104] (--) NVIDIA(0):     DFP-0
[    40.104] (--) NVIDIA(0):     DFP-1
[    40.104] (--) NVIDIA(0): COMPAQ CV535 (CRT-0): 400.0 MHz maximum pixel clock
[    40.104] (--) NVIDIA(0): ViewSonic A75f (CRT-1): 400.0 MHz maximum pixel clock
[    40.104] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    40.104] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    40.104] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    40.104] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    40.104] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    40.104] (**) NVIDIA(0):     device COMPAQ CV535 (CRT-0) (Using EDID frequencies has
[    40.104] (**) NVIDIA(0):     been enabled on all display devices.)
[    40.117] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    40.117] (**) NVIDIA(0):     device ViewSonic A75f (CRT-1) (Using EDID frequencies has
[    40.117] (**) NVIDIA(0):     been enabled on all display devices.)
[    40.136] (II) NVIDIA(0): Validated MetaModes:
[    40.136] (II) NVIDIA(0):     "nvidia-auto-select,nvidia-auto-select"
[    40.136] (II) NVIDIA(0): Virtual screen size determined to be 2048 x 768
[    40.171] (--) NVIDIA(0): DPI set to (92, 92); computed from "UseEdidDpi" X config
[    40.171] (--) NVIDIA(0):     option
[    40.171] (--) Depth 24 pixmap format is 32 bpp
[    40.172] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    40.198] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    40.198] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    40.198] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    40.198] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    40.198] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    40.198] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    40.198] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    40.198] (II) NVIDIA(0):     Config Options in the README.
[    40.199] (II) NVIDIA(0): Setting mode "nvidia-auto-select,nvidia-auto-select"
[    40.354] Loading extension NV-GLX
[    40.628] (==) NVIDIA(0): Disabling shared memory pixmaps
[    40.628] (==) NVIDIA(0): Backing store disabled
[    40.628] (==) NVIDIA(0): Silken mouse enabled
[    40.668] (**) NVIDIA(0): DPMS enabled
[    40.668] Loading extension NV-CONTROL
[    40.669] Loading extension XINERAMA
[    40.669] (WW) NVIDIA(0): Option "TwinView" is not used
[    40.669] (II) Loading sub module "dri2"
[    40.669] (II) LoadModule: "dri2"
[    40.669] (II) Module "dri2" already built-in
[    40.669] (II) NVIDIA(0): [DRI2] Setup complete
[    40.669] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    40.670] (--) RandR disabled
[    40.756] (II) Initializing extension GLX
[    43.180] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    43.180] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.180] (II) LoadModule: "evdev"
[    43.180] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.329] (II) Module evdev: vendor="X.Org Foundation"
[    43.330] 	compiled for 1.13.0, module version = 2.7.3
[    43.330] 	Module class: X.Org XInput Driver
[    43.330] 	ABI class: X.Org XInput driver, version 18.0
[    43.330] (II) Using input driver 'evdev' for 'Power Button'
[    43.330] (**) Power Button: always reports core events
[    43.330] (**) evdev: Power Button: Device: "/dev/input/event3"
[    43.330] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.330] (--) evdev: Power Button: Found keys
[    43.330] (II) evdev: Power Button: Configuring as keyboard
[    43.330] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    43.330] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    43.330] (**) Option "xkb_rules" "evdev"
[    43.330] (**) Option "xkb_model" "evdev"
[    43.330] (**) Option "xkb_layout" "us"
[    43.417] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    43.417] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.417] (II) Using input driver 'evdev' for 'Power Button'
[    43.418] (**) Power Button: always reports core events
[    43.418] (**) evdev: Power Button: Device: "/dev/input/event2"
[    43.418] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.418] (--) evdev: Power Button: Found keys
[    43.418] (II) evdev: Power Button: Configuring as keyboard
[    43.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    43.418] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    43.418] (**) Option "xkb_rules" "evdev"
[    43.418] (**) Option "xkb_model" "evdev"
[    43.418] (**) Option "xkb_layout" "us"
[    43.419] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    43.419] (II) No input driver specified, ignoring this device.
[    43.420] (II) This device may have been added with another device file.
[    43.420] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    43.420] (II) No input driver specified, ignoring this device.
[    43.420] (II) This device may have been added with another device file.
[    43.421] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[    43.421] (II) No input driver specified, ignoring this device.
[    43.421] (II) This device may have been added with another device file.
[    43.422] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    43.422] (II) No input driver specified, ignoring this device.
[    43.422] (II) This device may have been added with another device file.
[    43.422] (II) config/udev: Adding input device Microsoft Natural® Ergonomic Keyboard 4000 (/dev/input/event0)
[    43.422] (**) Microsoft Natural® Ergonomic Keyboard 4000: Applying InputClass "evdev keyboard catchall"
[    43.423] (II) Using input driver 'evdev' for 'Microsoft Natural® Ergonomic Keyboard 4000'
[    43.423] (**) Microsoft Natural® Ergonomic Keyboard 4000: always reports core events
[    43.423] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Device: "/dev/input/event0"
[    43.423] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Vendor 0x45e Product 0xdb
[    43.423] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found keys
[    43.423] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as keyboard
[    43.423] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input0/event0"
[    43.423] (II) XINPUT: Adding extended input device "Microsoft Natural® Ergonomic Keyboard 4000" (type: KEYBOARD, id 8)
[    43.423] (**) Option "xkb_rules" "evdev"
[    43.423] (**) Option "xkb_model" "evdev"
[    43.423] (**) Option "xkb_layout" "us"
[    43.425] (II) config/udev: Adding input device Microsoft Natural® Ergonomic Keyboard 4000 (/dev/input/event1)
[    43.425] (**) Microsoft Natural® Ergonomic Keyboard 4000: Applying InputClass "evdev keyboard catchall"
[    43.425] (II) Using input driver 'evdev' for 'Microsoft Natural® Ergonomic Keyboard 4000'
[    43.425] (**) Microsoft Natural® Ergonomic Keyboard 4000: always reports core events
[    43.425] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Device: "/dev/input/event1"
[    43.425] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Vendor 0x45e Product 0xdb
[    43.425] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found 1 mouse buttons
[    43.425] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found scroll wheel(s)
[    43.425] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found relative axes
[    43.425] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Forcing relative x/y axes to exist.
[    43.425] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found absolute axes
[    43.426] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Forcing absolute x/y axes to exist.
[    43.426] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found keys
[    43.426] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as mouse
[    43.426] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as keyboard
[    43.426] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Adding scrollwheel support
[    43.426] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: YAxisMapping: buttons 4 and 5
[    43.426] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.426] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input1/event1"
[    43.426] (II) XINPUT: Adding extended input device "Microsoft Natural® Ergonomic Keyboard 4000" (type: KEYBOARD, id 9)
[    43.426] (**) Option "xkb_rules" "evdev"
[    43.426] (**) Option "xkb_model" "evdev"
[    43.426] (**) Option "xkb_layout" "us"
[    43.452] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: initialized for relative axes.
[    43.452] (WW) evdev: Microsoft Natural® Ergonomic Keyboard 4000: ignoring absolute axes.
[    43.453] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) keeping acceleration scheme 1
[    43.453] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration profile 0
[    43.453] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration factor: 2.000
[    43.453] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration threshold: 4
[    43.454] (II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
[    43.454] (II) No input driver specified, ignoring this device.
[    43.454] (II) This device may have been added with another device file.
[    43.454] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event7)
[    43.454] (II) No input driver specified, ignoring this device.
[    43.454] (II) This device may have been added with another device file.
[    43.455] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event8)
[    43.455] (II) No input driver specified, ignoring this device.
[    43.455] (II) This device may have been added with another device file.
[    43.456] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event9)
[    43.456] (II) No input driver specified, ignoring this device.
[    43.456] (II) This device may have been added with another device file.
[    43.456] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
[    43.456] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    43.456] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    43.456] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    43.456] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
[    43.457] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    43.457] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    43.457] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    43.457] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    43.457] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    43.457] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    43.457] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    43.457] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    43.457] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.457] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    43.457] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 10)
[    43.457] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    43.458] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    43.458] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    43.458] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    43.458] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    43.458] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    43.459] (II) No input driver specified, ignoring this device.
[    43.459] (II) This device may have been added with another device file.
[    43.459] (II) config/udev: Adding input device PC Speaker (/dev/input/event4)
[    43.459] (II) No input driver specified, ignoring this device.
[    43.459] (II) This device may have been added with another device file.

```

Are there any modules or extensions that might have been enabled by TF2 that I can disable?

Any ideas?

(Using Arch and AwesomeWM)

---

### Post by EnigmaticCoder on 2012-12-09
Update: No video artifacts when using the nouveau driver. Still looking to get proprietary driver to work again.

---

