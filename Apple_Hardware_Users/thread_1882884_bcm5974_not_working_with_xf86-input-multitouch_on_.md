---
title: "bcm5974 not working with xf86-input-multitouch on MacBoock Pro 5,5"
date: 2011-11-18
forum: Apple Hardware Users
---

### Post by blubber42 on 2011-11-18
Hi,

I'm trying to get the xf86-input-multitouch driver to work on Ubuntu 11.04, but it's not working. I have installed the bcm5974-dkms and xf86-input-multitouch packages from the mactel ppa. Upon inspecting the log I found this line:
```

[     8.530] (EE) multitouch: cannot configure device

```
However I cannot find any more information on this problem, I've tried disabling other mouse drivers to no avail. Below is a dump of the latest xorg log. Any help in fixing this would be greatly appreciated.
```

[     6.151] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[     6.151] X Protocol Version 11, Revision 0
[     6.151] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     6.151] Current Operating System: Linux wega 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[     6.151] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=d91e5aef-bcdf-44fb-9112-28af488f0cf6 ro quiet splash pcie_aspm=force vt.handoff=7
[     6.151] Build Date: 19 April 2011  03:40:45PM
[     6.151] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[     6.151] Current version of pixman: 0.20.2
[     6.151] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     6.151] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.151] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 18 09:20:45 2011
[     6.151] (==) Using config file: "/etc/X11/xorg.conf"
[     6.151] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.151] (==) No Layout section.  Using the first Screen section.
[     6.151] (==) No screen section available. Using defaults.
[     6.151] (**) |-->Screen "Default Screen Section" (0)
[     6.151] (**) |   |-->Monitor "<default monitor>"
[     6.152] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[     6.152] (**) |   |-->Device "Default Device"
[     6.152] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     6.152] (==) Automatically adding devices
[     6.152] (==) Automatically enabling devices
[     6.152] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.152] 	Entry deleted from font path.
[     6.152] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.152] 	Entry deleted from font path.
[     6.152] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.152] 	Entry deleted from font path.
[     6.152] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.152] 	Entry deleted from font path.
[     6.152] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.152] 	Entry deleted from font path.
[     6.152] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     6.152] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.152] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.152] (II) Loader magic: 0x7e0280
[     6.152] (II) Module ABI versions:
[     6.152] 	X.Org ANSI C Emulation: 0.4
[     6.152] 	X.Org Video Driver: 10.0
[     6.152] 	X.Org XInput driver : 12.3
[     6.152] 	X.Org Server Extension : 5.0
[     6.154] (--) PCI:*(0:2:0:0) 10de:0863:106b:00b9 rev 177, Mem @ 0x92000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00001000/128, BIOS @ 0x????????/131072
[     6.154] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.154] (II) LoadModule: "extmod"
[     6.155] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.155] (II) Module extmod: vendor="X.Org Foundation"
[     6.155] 	compiled for 1.10.1, module version = 1.0.0
[     6.155] 	Module class: X.Org Server Extension
[     6.155] 	ABI class: X.Org Server Extension, version 5.0
[     6.155] (II) Loading extension MIT-SCREEN-SAVER
[     6.155] (II) Loading extension XFree86-VidModeExtension
[     6.156] (II) Loading extension XFree86-DGA
[     6.156] (II) Loading extension DPMS
[     6.156] (II) Loading extension XVideo
[     6.156] (II) Loading extension XVideo-MotionCompensation
[     6.156] (II) Loading extension X-Resource
[     6.156] (II) LoadModule: "dbe"
[     6.156] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.156] (II) Module dbe: vendor="X.Org Foundation"
[     6.156] 	compiled for 1.10.1, module version = 1.0.0
[     6.156] 	Module class: X.Org Server Extension
[     6.156] 	ABI class: X.Org Server Extension, version 5.0
[     6.156] (II) Loading extension DOUBLE-BUFFER
[     6.156] (II) LoadModule: "glx"
[     6.156] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[     6.168] (II) Module glx: vendor="NVIDIA Corporation"
[     6.168] 	compiled for 4.0.2, module version = 1.0.0
[     6.168] 	Module class: X.Org Server Extension
[     6.168] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[     6.169] (II) Loading extension GLX
[     6.169] (II) LoadModule: "record"
[     6.169] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.169] (II) Module record: vendor="X.Org Foundation"
[     6.169] 	compiled for 1.10.1, module version = 1.13.0
[     6.169] 	Module class: X.Org Server Extension
[     6.169] 	ABI class: X.Org Server Extension, version 5.0
[     6.169] (II) Loading extension RECORD
[     6.169] (II) LoadModule: "dri"
[     6.169] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.170] (II) Module dri: vendor="X.Org Foundation"
[     6.170] 	compiled for 1.10.1, module version = 1.0.0
[     6.170] 	ABI class: X.Org Server Extension, version 5.0
[     6.170] (II) Loading extension XFree86-DRI
[     6.170] (II) LoadModule: "dri2"
[     6.170] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.170] (II) Module dri2: vendor="X.Org Foundation"
[     6.170] 	compiled for 1.10.1, module version = 1.2.0
[     6.170] 	ABI class: X.Org Server Extension, version 5.0
[     6.170] (II) Loading extension DRI2
[     6.170] (==) Matched nvidia as autoconfigured driver 0
[     6.170] (==) Matched nouveau as autoconfigured driver 1
[     6.170] (==) Matched nv as autoconfigured driver 2
[     6.170] (==) Matched vesa as autoconfigured driver 3
[     6.170] (==) Matched fbdev as autoconfigured driver 4
[     6.170] (==) Assigned the driver to the xf86ConfigLayout
[     6.170] (II) LoadModule: "nvidia"
[     6.170] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     6.171] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.171] 	compiled for 4.0.2, module version = 1.0.0
[     6.171] 	Module class: X.Org Video Driver
[     6.171] (II) LoadModule: "nouveau"
[     6.171] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     6.171] (II) Module nouveau: vendor="X.Org Foundation"
[     6.171] 	compiled for 1.10.0, module version = 0.0.16
[     6.171] 	Module class: X.Org Video Driver
[     6.171] 	ABI class: X.Org Video Driver, version 10.0
[     6.171] (II) LoadModule: "nv"
[     6.172] (WW) Warning, couldn't open module nv
[     6.172] (II) UnloadModule: "nv"
[     6.172] (II) Unloading nv
[     6.172] (EE) Failed to load module "nv" (module does not exist, 0)
[     6.172] (II) LoadModule: "vesa"
[     6.172] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.172] (II) Module vesa: vendor="X.Org Foundation"
[     6.172] 	compiled for 1.10.0, module version = 2.3.0
[     6.172] 	Module class: X.Org Video Driver
[     6.172] 	ABI class: X.Org Video Driver, version 10.0
[     6.172] (II) LoadModule: "fbdev"
[     6.173] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.173] (II) Module fbdev: vendor="X.Org Foundation"
[     6.173] 	compiled for 1.10.0, module version = 0.4.2
[     6.173] 	ABI class: X.Org Video Driver, version 10.0
[     6.173] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[     6.173] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.173] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[     6.173] (II) NOUVEAU driver for NVIDIA chipset families :
[     6.173] 	RIVA TNT    (NV04)
[     6.173] 	RIVA TNT2   (NV05)
[     6.173] 	GeForce 256 (NV10)
[     6.173] 	GeForce 2   (NV11, NV15)
[     6.173] 	GeForce 4MX (NV17, NV18)
[     6.173] 	GeForce 3   (NV20)
[     6.173] 	GeForce 4Ti (NV25, NV28)
[     6.173] 	GeForce FX  (NV3x)
[     6.173] 	GeForce 6   (NV4x)
[     6.173] 	GeForce 7   (G7x)
[     6.173] 	GeForce 8   (G8x)
[     6.173] (II) VESA: driver for VESA chipsets: vesa
[     6.173] (II) FBDEV: driver for framebuffer: fbdev
[     6.173] (++) using VT number 7

[     6.173] (II) Loading sub module "fb"
[     6.173] (II) LoadModule: "fb"
[     6.173] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.173] (II) Module fb: vendor="X.Org Foundation"
[     6.173] 	compiled for 1.10.1, module version = 1.0.0
[     6.173] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.173] (II) Loading sub module "wfb"
[     6.173] (II) LoadModule: "wfb"
[     6.174] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.174] (II) Module wfb: vendor="X.Org Foundation"
[     6.174] 	compiled for 1.10.1, module version = 1.0.0
[     6.174] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.174] (II) Loading sub module "ramdac"
[     6.174] (II) LoadModule: "ramdac"
[     6.174] (II) Module "ramdac" already built-in
[     6.174] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     6.174] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.174] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.174] (WW) Falling back to old probe method for vesa
[     6.174] (WW) Falling back to old probe method for fbdev
[     6.174] (II) Loading sub module "fbdevhw"
[     6.174] (II) LoadModule: "fbdevhw"
[     6.174] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.174] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.174] 	compiled for 1.10.1, module version = 0.0.2
[     6.174] 	ABI class: X.Org Video Driver, version 10.0
[     6.174] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     6.174] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.174] (==) NVIDIA(0): RGB weight 888
[     6.174] (==) NVIDIA(0): Default visual is TrueColor
[     6.174] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.174] (**) NVIDIA(0): Option "NoLogo" "True"
[     6.889] (II) NVIDIA(GPU-0): Display (Apple (DFP-0)) does not support NVIDIA 3D Vision
[     6.889] (II) NVIDIA(GPU-0):     stereo.
[     6.890] (II) NVIDIA(0): NVIDIA GPU GeForce 9400M (C79) at PCI:2:0:0 (GPU-0)
[     6.890] (--) NVIDIA(0): Memory: 524288 kBytes
[     6.890] (--) NVIDIA(0): VideoBIOS: 62.79.67.00.00
[     6.890] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     6.890] (--) NVIDIA(0): Connected display device(s) on GeForce 9400M at PCI:2:0:0
[     6.890] (--) NVIDIA(0):     Apple (DFP-0)
[     6.890] (--) NVIDIA(0): Apple (DFP-0): 165.0 MHz maximum pixel clock
[     6.890] (--) NVIDIA(0): Apple (DFP-0): Internal Single Link LVDS
[     6.908] (II) NVIDIA(0): Assigned Display Device: DFP-0
[     6.908] (==) NVIDIA(0): 
[     6.908] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     6.908] (==) NVIDIA(0):     will be used as the requested mode.
[     6.908] (==) NVIDIA(0): 
[     6.908] (II) NVIDIA(0): Validated modes:
[     6.908] (II) NVIDIA(0):     "nvidia-auto-select"
[     6.908] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
[     7.970] (--) NVIDIA(0): DPI set to (112, 112); computed from "UseEdidDpi" X config
[     7.970] (--) NVIDIA(0):     option
[     7.970] (II) UnloadModule: "nouveau"
[     7.970] (II) Unloading nouveau
[     7.970] (II) UnloadModule: "vesa"
[     7.970] (II) Unloading vesa
[     7.970] (II) UnloadModule: "fbdev"
[     7.970] (II) Unloading fbdev
[     7.970] (II) UnloadModule: "fbdevhw"
[     7.970] (II) Unloading fbdevhw
[     7.970] (--) Depth 24 pixmap format is 32 bpp
[     7.970] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     7.976] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[     8.246] (II) Loading extension NV-GLX
[     8.281] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.281] (==) NVIDIA(0): Backing store disabled
[     8.281] (==) NVIDIA(0): Silken mouse enabled
[     8.281] (==) NVIDIA(0): DPMS enabled
[     8.282] (II) Loading extension NV-CONTROL
[     8.282] (II) Loading extension XINERAMA
[     8.282] (II) Loading sub module "dri2"
[     8.282] (II) LoadModule: "dri2"
[     8.282] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     8.282] (II) Module dri2: vendor="X.Org Foundation"
[     8.282] 	compiled for 1.10.1, module version = 1.2.0
[     8.282] 	ABI class: X.Org Server Extension, version 5.0
[     8.282] (II) NVIDIA(0): [DRI2] Setup complete
[     8.282] (==) RandR enabled
[     8.282] (II) Initializing built-in extension Generic Event Extension
[     8.282] (II) Initializing built-in extension SHAPE
[     8.282] (II) Initializing built-in extension MIT-SHM
[     8.282] (II) Initializing built-in extension XInputExtension
[     8.282] (II) Initializing built-in extension XTEST
[     8.282] (II) Initializing built-in extension BIG-REQUESTS
[     8.282] (II) Initializing built-in extension SYNC
[     8.282] (II) Initializing built-in extension XKEYBOARD
[     8.282] (II) Initializing built-in extension XC-MISC
[     8.282] (II) Initializing built-in extension SECURITY
[     8.282] (II) Initializing built-in extension XINERAMA
[     8.282] (II) Initializing built-in extension XFIXES
[     8.282] (II) Initializing built-in extension RENDER
[     8.282] (II) Initializing built-in extension RANDR
[     8.282] (II) Initializing built-in extension COMPOSITE
[     8.282] (II) Initializing built-in extension DAMAGE
[     8.282] (II) Initializing built-in extension GESTURE
[     8.284] (II) Initializing extension GLX
[     8.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.312] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     8.312] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.312] (II) LoadModule: "evdev"
[     8.312] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.313] (II) Module evdev: vendor="X.Org Foundation"
[     8.313] 	compiled for 1.10.0.902, module version = 2.6.0
[     8.313] 	Module class: X.Org XInput Driver
[     8.313] 	ABI class: X.Org XInput driver, version 12.3
[     8.313] (II) Using input driver 'evdev' for 'Power Button'
[     8.313] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.313] (**) Power Button: always reports core events
[     8.313] (**) Power Button: Device: "/dev/input/event3"
[     8.340] (--) Power Button: Found keys
[     8.340] (II) Power Button: Configuring as keyboard
[     8.340] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     8.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.340] (**) Option "xkb_rules" "evdev"
[     8.340] (**) Option "xkb_model" "pc105"
[     8.340] (**) Option "xkb_layout" "us"
[     8.372] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.372] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.372] (II) Using input driver 'evdev' for 'Power Button'
[     8.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.372] (**) Power Button: always reports core events
[     8.372] (**) Power Button: Device: "/dev/input/event1"
[     8.380] (--) Power Button: Found keys
[     8.380] (II) Power Button: Configuring as keyboard
[     8.380] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[     8.380] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.380] (**) Option "xkb_rules" "evdev"
[     8.380] (**) Option "xkb_model" "pc105"
[     8.380] (**) Option "xkb_layout" "us"
[     8.380] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     8.380] (II) No input driver/identifier specified (ignoring)
[     8.381] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     8.381] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     8.381] (II) Using input driver 'evdev' for 'Sleep Button'
[     8.381] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.381] (**) Sleep Button: always reports core events
[     8.381] (**) Sleep Button: Device: "/dev/input/event2"
[     8.381] (--) Sleep Button: Found keys
[     8.381] (II) Sleep Button: Configuring as keyboard
[     8.381] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[     8.381] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[     8.381] (**) Option "xkb_rules" "evdev"
[     8.381] (**) Option "xkb_model" "pc105"
[     8.381] (**) Option "xkb_layout" "us"
[     8.383] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event5)
[     8.383] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[     8.383] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[     8.383] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.383] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[     8.383] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event5"
[     8.400] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found keys
[     8.400] (II) Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[     8.400] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input5/event5"
[     8.400] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
[     8.400] (**) Option "xkb_rules" "evdev"
[     8.400] (**) Option "xkb_model" "pc105"
[     8.400] (**) Option "xkb_layout" "us"
[     8.400] (II) config/udev: Adding input device bcm5974 (/dev/input/event6)
[     8.400] (**) bcm5974: Applying InputClass "Multitouch Touchpad"
[     8.400] (II) LoadModule: "multitouch"
[     8.401] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[     8.401] (II) Module multitouch: vendor="X.Org Foundation"
[     8.401] 	compiled for 1.10.0, module version = 0.1.0
[     8.401] 	Module class: X.Org XInput Driver
[     8.401] 	ABI class: X.Org XInput driver, version 12.3
[     8.401] (II) Using input driver 'multitouch' for 'bcm5974'
[     8.401] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[     8.401] (**) bcm5974: always reports core events
[     8.401] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input6/event6"
[     8.401] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
[     8.401] (II) device control: init
[     8.401] (**) Option "Device" "/dev/input/event6"
[     8.415] (II) multitouch: devname: bcm5974
[     8.415] (II) multitouch: devid: 5ac 237 1
[     8.415] (II) multitouch: caps: left mtdata ibt
[     8.415] (II) multitouch: 0: min: 0 max: 2048
[     8.415] (II) multitouch: 1: min: 0 max: 2048
[     8.415] (II) multitouch: 2: min: 0 max: 2048
[     8.415] (II) multitouch: 3: min: 0 max: 2048
[     8.415] (II) multitouch: 4: min: -16384 max: 16384
[     8.415] (II) multitouch: 5: min: -4460 max: 5166
[     8.415] (II) multitouch: 6: min: -75 max: 6700
[     8.460] (II) pointer_control
[     8.460] (**) bcm5974: (accel) keeping acceleration scheme 1
[     8.460] (II) pointer_property
[     8.460] (II) pointer_property
[     8.460] (**) bcm5974: (accel) acceleration profile 0
[     8.460] (II) pointer_property
[     8.460] (II) pointer_property
[     8.460] (**) bcm5974: (accel) acceleration factor: 2.000
[     8.460] (**) bcm5974: (accel) acceleration threshold: 4
[     8.460] (II) device control: on
[     8.495] (II) pointer_property
[     8.495] (II) pointer_property
[     8.495] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse0)
[     8.495] (**) bcm5974: Applying InputClass "Multitouch Touchpad"
[     8.495] (II) Using input driver 'multitouch' for 'bcm5974'
[     8.495] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[     8.495] (**) bcm5974: always reports core events
[     8.495] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input6/mouse0"
[     8.495] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
[     8.495] (II) device control: init
[     8.495] (**) Option "Device" "/dev/input/mouse0"
[     8.530] (EE) multitouch: cannot configure device
[     8.530] (EE) Couldn't init device "bcm5974"
[     8.530] (II) UnloadModule: "multitouch"
[     8.530] (II) Unloading multitouch
[     8.536] (II) config/udev: Adding input device applesmc (/dev/input/event4)
[     8.536] (II) No input driver/identifier specified (ignoring)
[     8.536] (II) config/udev: Adding input device applesmc (/dev/input/js0)
[     8.536] (II) No input driver/identifier specified (ignoring)
[    31.400] (II) pointer_property

```

That pointer_property line is repeated throughout the session.

---

### Post by QB89Dragon on 2011-11-19
Same problem here, Macbook Pro 5,5
Tried installing touchegg, using kernel bcm5974 driver, installed xserver-xorg-input-multitouch
I have the same error in my Xorg.0.log file.
Anyone have any solutions? I was really excited at the though of getting multitouch working for me on Oneiric.

---

### Post by _markd on 2011-11-21
I had the same problems on a Macbook Pro 8.2 (late 2011 with ATI Graphics).
- touchpad only working as a 1 button mouse
- fn key not working (no Page Up/Down keys, no volume control keys etc)

What I just did is upgrading to precise pangolin (12.04) repositories , install linux-image-3.2.0-1-generic and xserver-xorg-input-mtrack.

Then I configured /etc/X11/xorg.conf.d/50-mtrack.conf:
```

Section "InputClass"
        MatchIsTouchpad "true"
        Identifier "touchpad"
        Driver "mtrack"
EndSection

```

I tried two finger scroll and two finger tap for right click. Those work fine now. I'm missing touchpad configuration in system settings though.

The Fn Keys work well except for the display dimming. There's a nice pop up displaying the dim state when I press the keys, but the display does not respond to that and stays dimmed the way it is.

Some more off topic things:
My display is 1680x1050 and I had problems attaching another display (also 1680x1050) to the thunderbold port. When the X server is started with the display attached, I have two 1440x900 displays in mirror mode. When I start without the external monitor connected and attach after X is started/I'm logged in, I get two 1680x1050 displays in dual head mode.

Furthermore I tried the AHCI mode described in [1]. Works well but disables suspend/resume functionality. There's a patch for that, which I haven't tried yet [2].
[1]
[http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro#AHCI](http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro#AHCI)

[2]
[http://www.gossamer-threads.com/lists/linux/kernel/1251299](http://www.gossamer-threads.com/lists/linux/kernel/1251299)

hth, Mark

---

