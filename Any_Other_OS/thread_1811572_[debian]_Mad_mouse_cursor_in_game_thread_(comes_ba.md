---
title: "[debian] Mad mouse cursor in game thread (comes back to screen center every 1s)"
date: 2011-07-25
forum: Any Other OS
---

### Post by noob+1 on 2011-07-25
Hello,

I'm experiencing a problem in debian (ubuntu being debian-based, you may have a solution).
I don't know the timeline of my problem, since I'm not a big gamer, it may have been after and X upgrade ?

Evry time I start a game thread, in full screen or in window mode (it seems to appear evry time a window 'captures' the mouse, though I don't have the problem in wine with wow for example), when I try to move it, the cursor automatically goes back to the center of the screen in a second or so. 

I wish I had a game that could log everything it's doing so I could see what's happening (it would have to start command line, if I have to configure it with the mouse I will need a shrink after...)

If you want to do some tests this appears in lbreakout2 and nexuiz for example

EDIT : There may be a permission problem involved, since I switched hard drive (with a dirty root fs copy - yeah I now...), and though I reset the right permission (comparing  the two file systems with a script), I did miss some suid files I had to chmod manually.

EDIT 2 : my desktop manager is lxde
--------------------------------------------------------------
Here are the specs I can think of about my config :
-------------------------------------------------------------

```

_**- mouse :**_ "Laser Glow Mouse 1600" (USB, with cable)

_**- Graphic system**_ : Nvidia GeForce 7300 GT, with driver nvidia (x86_64-275.19)

_**- X version **_:

[I]X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.39-2-amd64 x86_64 Debian
Current Operating System: Linux sexmachine 2.6.38-2-amd64 #1 SMP Sun May 8 13:51:57 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-2-amd64 root=UUID=9----------------------------------2 ro vga=758 quiet
Build Date: 02 July 2011  10:05:17AM
xorg-server 2:1.10.2.902-1 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.22.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[/I]


-_** Xorg.conf interesting parts :**_

[I]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
[/I]
_**- Xorg.0.log**_

X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[    15.430] X Protocol Version 11, Revision 0
[    15.430] Build Operating System: Linux 2.6.39-2-amd64 x86_64 Debian
[    15.430] Current Operating System: Linux sexmachine 2.6.38-2-amd64 #1 SMP Sun May 8 13:51:57 UTC 2011 x86_64
[    15.430] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-2-amd64 root=UUID=9------------------------------------------------2 ro vga=758 quiet
[    15.430] Build Date: 02 July 2011  10:05:17AM
[    15.430] xorg-server 2:1.10.2.902-1 (Cyril Brulebois <kibi@debian.org>) 
[    15.430] Current version of pixman: 0.22.2
[    15.430]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    15.430] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.430] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 25 09:23:13 2011
[    15.434] (==) Using config file: "/etc/X11/xorg.conf"
[    15.434] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.437] (==) ServerLayout "Layout0"
[    15.437] (**) |-->Screen "Screen0" (0)
[    15.437] (**) |   |-->Monitor "Monitor0"
[    15.438] (**) |   |-->Device "Device0"
[    15.438] (**) |-->Input Device "Keyboard0"
[    15.438] (**) |-->Input Device "Mouse0"
[    15.438] (**) Option "Xinerama" "0"
[    15.438] (==) Automatically adding devices
[    15.438] (==) Automatically enabling devices
[    15.441] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.441]     Entry deleted from font path.
[    15.444] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.444] (==) ModulePath set to "/usr/lib/xorg/modules"
[    15.444] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.444] (WW) Disabling Keyboard0
[    15.444] (WW) Disabling Mouse0
[    15.444] (II) Loader magic: 0x7d7f40
[    15.444] (II) Module ABI versions:
[    15.444]     X.Org ANSI C Emulation: 0.4
[    15.444]     X.Org Video Driver: 10.0
[    15.444]     X.Org XInput driver : 12.2
[    15.444]     X.Org Server Extension : 5.0
[    15.446] (--) PCI:*(0:1:0:0) 10de:0393:1458:341b rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
[    15.446] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.446] (II) LoadModule: "extmod"
[    15.451] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.453] (II) Module extmod: vendor="X.Org Foundation"
[    15.453]     compiled for 1.10.2.902, module version = 1.0.0
[    15.453]     Module class: X.Org Server Extension
[    15.453]     ABI class: X.Org Server Extension, version 5.0
[    15.453] (II) Loading extension SELinux
[    15.453] (II) Loading extension MIT-SCREEN-SAVER
[    15.453] (II) Loading extension XFree86-VidModeExtension
[    15.453] (II) Loading extension XFree86-DGA
[    15.453] (II) Loading extension DPMS
[    15.453] (II) Loading extension XVideo
[    15.453] (II) Loading extension XVideo-MotionCompensation
[    15.453] (II) Loading extension X-Resource
[    15.454] (II) LoadModule: "dbe"
[    15.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.455] (II) Module dbe: vendor="X.Org Foundation"
[    15.455]     compiled for 1.10.2.902, module version = 1.0.0
[    15.455]     Module class: X.Org Server Extension
[    15.455]     ABI class: X.Org Server Extension, version 5.0
[    15.455] (II) Loading extension DOUBLE-BUFFER
[    15.455] (II) LoadModule: "glx"
[    15.455] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.561] (II) Module glx: vendor="NVIDIA Corporation"
[    15.561]     compiled for 4.0.2, module version = 1.0.0
[    15.562]     Module class: X.Org Server Extension
[    15.562] (II) NVIDIA GLX Module  275.19  Tue Jul 12 18:31:51 PDT 2011
[    15.562] (II) Loading extension GLX
[    15.562] (II) LoadModule: "record"
[    15.562] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.563] (II) Module record: vendor="X.Org Foundation"
[    15.563]     compiled for 1.10.2.902, module version = 1.13.0
[    15.563]     Module class: X.Org Server Extension
[    15.563]     ABI class: X.Org Server Extension, version 5.0
[    15.563] (II) Loading extension RECORD
[    15.563] (II) LoadModule: "dri"
[    15.564] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.565] (II) Module dri: vendor="X.Org Foundation"
[    15.565]     compiled for 1.10.2.902, module version = 1.0.0
[    15.565]     ABI class: X.Org Server Extension, version 5.0
[    15.565] (II) Loading extension XFree86-DRI
[    15.565] (II) LoadModule: "dri2"
[    15.566] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.567] (II) Module dri2: vendor="X.Org Foundation"
[    15.567]     compiled for 1.10.2.902, module version = 1.2.0
[    15.567]     ABI class: X.Org Server Extension, version 5.0
[    15.567] (II) Loading extension DRI2
[    15.567] (II) LoadModule: "nvidia"
[    15.567] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    15.574] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.575]     compiled for 4.0.2, module version = 1.0.0
[    15.575]     Module class: X.Org Video Driver
[    17.633] (II) NVIDIA dlloader X Driver  275.19  Tue Jul 12 18:15:26 PDT 2011
[    17.633] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.634] (++) using VT number 7

[    17.644] (II) Loading sub module "fb"
[    17.644] (II) LoadModule: "fb"
[    17.644] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.645] (II) Module fb: vendor="X.Org Foundation"
[    17.645]     compiled for 1.10.2.902, module version = 1.0.0
[    17.645]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.645] (II) Loading sub module "wfb"
[    17.645] (II) LoadModule: "wfb"
[    17.646] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.647] (II) Module wfb: vendor="X.Org Foundation"
[    17.647]     compiled for 1.10.2.902, module version = 1.0.0
[    17.647]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.647] (II) Loading sub module "ramdac"
[    17.647] (II) LoadModule: "ramdac"
[    17.647] (II) Module "ramdac" already built-in
[    17.649] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    17.649] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.649] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.650] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.650] (==) NVIDIA(0): RGB weight 888
[    17.650] (==) NVIDIA(0): Default visual is TrueColor
[    17.650] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.650] (**) NVIDIA(0): Option "TVStandard" "PAL-B"
[    17.650] (**) NVIDIA(0): Option "TVOutFormat" "COMPOSITE"
[    17.650] (**) NVIDIA(0): Option "TwinView" "1"
[    17.650] (**) NVIDIA(0): Option "MetaModes" "TV: nvidia-auto-select +1680+0, DFP: 1680x1050 +0+0"
[    17.651] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    17.651] (**) NVIDIA(0): Forcing COMPOSITE video output
[    17.651] (**) NVIDIA(0): TV Standard string: "PAL-B"
[    19.113] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    19.113] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    19.116] (II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
[    19.116] (--) NVIDIA(0): Memory: 262144 kBytes
[    19.116] (--) NVIDIA(0): VideoBIOS: 05.73.22.50.03
[    19.116] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.116] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.116] (--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0
[    19.116] (--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
[    19.116] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[    19.116] (--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
[    19.116] (--) NVIDIA(0): TV encoder: NVIDIA
[    19.116] (**) NVIDIA(0): TwinView enabled
[    19.116] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, TV-0
[    19.117] (II) NVIDIA(0): Assigned Display Devices: DFP-0, TV-0
[    19.117] (II) NVIDIA(0): Validated modes:
[    19.117] (II) NVIDIA(0):     "TV:nvidia-auto-select+1680+0,DFP:1680x1050+0+0"
[    19.117] (II) NVIDIA(0): Virtual screen size determined to be 2704 x 1050
[    19.117] (++) NVIDIA(0): DPI set to (96, 96); computed from -dpi X commandline option
[    19.117] (--) Depth 24 pixmap format is 32 bpp
[    19.126] (II) NVIDIA(0): Setting mode "TV:nvidia-auto-select+1680+0,DFP:1680x1050+0+0"
[    19.507] (II) Loading extension NV-GLX
[    19.553] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.553] (==) NVIDIA(0): Backing store disabled
[    19.554] (==) NVIDIA(0): Silken mouse enabled
[    19.554] (**) NVIDIA(0): DPMS enabled
[    19.554] (II) Loading extension NV-CONTROL
[    19.555] (II) Loading extension XINERAMA
[    19.555] (II) Loading sub module "dri2"
[    19.555] (II) LoadModule: "dri2"
[    19.555] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.555] (II) Module dri2: vendor="X.Org Foundation"
[    19.555]     compiled for 1.10.2.902, module version = 1.2.0
[    19.555]     ABI class: X.Org Server Extension, version 5.0
[    19.555] (II) NVIDIA(0): [DRI2] Setup complete
[    19.555] (==) RandR enabled
[    19.555] (II) Initializing built-in extension Generic Event Extension
[    19.555] (II) Initializing built-in extension SHAPE
[    19.555] (II) Initializing built-in extension MIT-SHM
[    19.555] (II) Initializing built-in extension XInputExtension
[    19.555] (II) Initializing built-in extension XTEST
[    19.555] (II) Initializing built-in extension BIG-REQUESTS
[    19.555] (II) Initializing built-in extension SYNC
[    19.555] (II) Initializing built-in extension XKEYBOARD
[    19.555] (II) Initializing built-in extension XC-MISC
[    19.555] (II) Initializing built-in extension SECURITY
[    19.555] (II) Initializing built-in extension XINERAMA
[    19.555] (II) Initializing built-in extension XFIXES
[    19.555] (II) Initializing built-in extension RENDER
[    19.555] (II) Initializing built-in extension RANDR
[    19.555] (II) Initializing built-in extension COMPOSITE
[    19.555] (II) Initializing built-in extension DAMAGE
[    19.555] (II) SELinux: Disabled on system
[    19.558] (II) Initializing extension GLX
[    19.653] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    19.653] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.653] (II) LoadModule: "evdev"
[    19.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.654] (II) Module evdev: vendor="X.Org Foundation"
[    19.654]     compiled for 1.10.1, module version = 2.6.0
[    19.654]     Module class: X.Org XInput Driver
[    19.654]     ABI class: X.Org XInput driver, version 12.2
[    19.654] (II) Using input driver 'evdev' for 'Power Button'
[    19.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.654] (**) Power Button: always reports core events
[    19.654] (**) Power Button: Device: "/dev/input/event3"
[    19.672] (--) Power Button: Found keys
[    19.672] (II) Power Button: Configuring as keyboard
[    19.672] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    19.672] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.672] (**) Option "xkb_rules" "evdev"
[    19.672] (**) Option "xkb_model" "pc105"
[    19.672] (**) Option "xkb_layout" "fr"
[    19.672] (**) Option "xkb_variant" "latin9"
[    19.672] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.715] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.716] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.716] (II) Using input driver 'evdev' for 'Power Button'
[    19.716] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.716] (**) Power Button: always reports core events
[    19.716] (**) Power Button: Device: "/dev/input/event2"
[    19.740] (--) Power Button: Found keys
[    19.740] (II) Power Button: Configuring as keyboard
[    19.740] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    19.740] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.740] (**) Option "xkb_rules" "evdev"
[    19.740] (**) Option "xkb_model" "pc105"
[    19.740] (**) Option "xkb_layout" "fr"
[    19.740] (**) Option "xkb_variant" "latin9"
[    19.740] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.745] (II) config/udev: Adding input device HOLTEK Laser Gaming mouse (/dev/input/event1)
[    19.745] (**) HOLTEK Laser Gaming mouse: Applying InputClass "evdev pointer catchall"
[    19.745] (II) Using input driver 'evdev' for 'HOLTEK Laser Gaming mouse'
[    19.745] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.746] (**) HOLTEK Laser Gaming mouse: always reports core events
[    19.746] (**) HOLTEK Laser Gaming mouse: Device: "/dev/input/event1"
[    19.756] (--) HOLTEK Laser Gaming mouse: Found 15 mouse buttons
[    19.756] (--) HOLTEK Laser Gaming mouse: Found scroll wheel(s)
[    19.756] (--) HOLTEK Laser Gaming mouse: Found relative axes
[    19.756] (--) HOLTEK Laser Gaming mouse: Found x and y relative axes
[    19.756] (II) HOLTEK Laser Gaming mouse: Configuring as mouse
[    19.756] (II) HOLTEK Laser Gaming mouse: Adding scrollwheel support
[    19.756] (**) HOLTEK Laser Gaming mouse: YAxisMapping: buttons 4 and 5
[    19.756] (**) HOLTEK Laser Gaming mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.756] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb4/4-2/4-2:1.0/input/input1/event1"
[    19.756] (II) XINPUT: Adding extended input device "HOLTEK Laser Gaming mouse" (type: MOUSE)
[    19.756] (II) HOLTEK Laser Gaming mouse: initialized for relative axes.
[    19.756] (**) HOLTEK Laser Gaming mouse: (accel) keeping acceleration scheme 1
[    19.756] (**) HOLTEK Laser Gaming mouse: (accel) acceleration profile 0
[    19.756] (**) HOLTEK Laser Gaming mouse: (accel) acceleration factor: 2.000
[    19.756] (**) HOLTEK Laser Gaming mouse: (accel) acceleration threshold: 4
[    19.756] (II) config/udev: Adding input device HOLTEK Laser Gaming mouse (/dev/input/mouse0)
[    19.757] (II) No input driver/identifier specified (ignoring)
[    19.759] (II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event4)
[    19.759] (II) No input driver/identifier specified (ignoring)
[    19.760] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event5)
[    19.760] (II) No input driver/identifier specified (ignoring)
[    19.762] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[    19.762] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.762] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.762] (**) AT Translated Set 2 keyboard: always reports core events
[    19.762] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[    19.762] (--) AT Translated Set 2 keyboard: Found keys
[    19.762] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.762] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input0/event0"
[    19.762] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.762] (**) Option "xkb_rules" "evdev"
[    19.762] (**) Option "xkb_model" "pc105"
[    19.762] (**) Option "xkb_layout" "fr"
[    19.762] (**) Option "xkb_variant" "latin9"
[    19.762] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.767] (II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event7)
[    19.767] (**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
[    19.767] (II) Using input driver 'evdev' for 'ACPI Virtual Keyboard Device'
[    19.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.768] (**) ACPI Virtual Keyboard Device: always reports core events
[    19.768] (**) ACPI Virtual Keyboard Device: Device: "/dev/input/event7"
[    19.768] (--) ACPI Virtual Keyboard Device: Found keys
[    19.768] (II) ACPI Virtual Keyboard Device: Configuring as keyboard
[    19.768] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    19.768] (II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
[    19.768] (**) Option "xkb_rules" "evdev"
[    19.768] (**) Option "xkb_model" "pc105"
[    19.768] (**) Option "xkb_layout" "fr"
[    19.768] (**) Option "xkb_variant" "latin9"
[    19.768] (**) Option "xkb_options" "lv3:ralt_switch"
```

---

