---
title: "could not start gnome session"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
hi,i installed xorg and gnome,including extras on my newly installed archlinux.When i booted into arch,and logged in as non-root user and typed:
"startx" in console,the screen made as if it were to start the graphical environment,but finally it could not,and i had a lot of things appearing as output.the last three lines read as below:

Using config file:"/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "record"(module does not exist, 0)
/home/sonujha/.xinitrc:line1:exec:startgnome:command not found

i had written "exec startgnome"(exactly this) in the above file in the first line.


Now,how do i solve this?i am desperate to see gnome into the act on arch.I have even installed all the software that i need.

---

### Post by stonecoldjha on 2009-02-04
sorry i forgot to include this
the following are the contents off my "/var/log/Xorg.0.log" file:

X.Org X Server 1.5.3
Release Date: 5 November 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.27-ARCH i686 
Current Operating System: Linux arch 2.6.28-ARCH #1 SMP PREEMPT Sun Jan 25 10:13:11 UTC 2009 i686
Build Date: 17 December 2008  08:20:05PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb  4 19:31:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xorg Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "PS/2 Mouse"
(**) Option "AllowMouseOpenFail" "true"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/PEX" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/cyrillic".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/cyrillic").
(WW) The directory "/usr/share/fonts/ttf/western" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/ttf/decoratives" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/openoffice" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/ttf-bitstream-vera" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/latex-ttf-fonts" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/CID" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/TrueType" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/misc,/usr/share/fonts/100dpi:unscaled,/usr/share/fonts/75dpi:unscaled,/usr/share/fonts/TTF,/usr/share/fonts/Type1.
(**) FontPath set to:
	/usr/share/fonts/misc:unscaled,
	/usr/share/fonts/misc,
	/usr/share/fonts/75dpi:unscaled,
	/usr/share/fonts/75dpi,
	/usr/share/fonts/100dpi:unscaled,
	/usr/share/fonts/100dpi,
	/usr/share/fonts/Type1,
	/usr/share/fonts/misc,
	/usr/share/fonts/100dpi:unscaled,
	/usr/share/fonts/75dpi:unscaled,
	/usr/share/fonts/TTF,
	/usr/share/fonts/Type1
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d5fe0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@3:0:0) nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] rev 161, Mem @ 0xfd000000/0, 0xd0000000/0, 0xfc000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.22  Tue Jan  6 09:58:42 PST 2009
(II) Loading extension GLX
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.3, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(WW) Warning, couldn't open module record
(II) UnloadModule: "record"
(EE) Failed to load module "record" (module does not exist, 0)
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  180.22  Tue Jan  6 09:35:46 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 TurboCache(TM) (NV44) at PCI:3:0:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.65.80
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 TurboCache(TM) at
(--) NVIDIA(0):     PCI:3:0:0:
(--) NVIDIA(0):     Acer AL1916W (CRT-0)
(--) NVIDIA(0): Acer AL1916W (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (63, 75); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) NVIDIA(0):     configuration option may not be set correctly.  When the
(II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms" "true"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(WW) Option "XkbVariant" requires an string value
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/psaux"
(II) PS/2 Mouse: Setting mouse protocol to "ExplorerPS/2"
(**) PS/2 Mouse: Device: "/dev/psaux"
(**) PS/2 Mouse: Protocol: "auto"
(**) Option "SendCoreEvents" "true"
(**) Option "CorePointer"
(**) PS/2 Mouse: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "true"
(**) Option "Emulate3Timeout" "70"
(**) PS/2 Mouse: Emulate3Buttons, Emulate3Timeout: 70
(**) Option "ZAxisMapping" "4 5"
(**) PS/2 Mouse: ZAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: Buttons: 9
(**) PS/2 Mouse: Sensitivity: 1
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (PS/2 Mouse)
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: Setting mouse protocol to "ExplorerPS/2"
(II) PS/2 Mouse: ps2EnableDataReporting: succeeded
(II) UnloadModule: "kbd"
(II) UnloadModule: "mouse"

---

### Post by smartboyathome on 2009-02-04
It says that it can't run startgnome (it's not found). That means that GNOME didn't completely install.

---

### Post by Rumor on 2009-02-04
> **stonecoldjha said:**
> hi,i installed xorg and gnome,including extras on my newly installed archlinux.When i booted into arch,and logged in as non-root user and typed:
"startx" in console,the screen made as if it were to start the graphical environment,but finally it could not,and i had a lot of things appearing as output.the last three lines read as below:

Using config file:"/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "record"(module does not exist, 0)
/home/sonujha/.xinitrc:line1:exec:startgnome:command not found

i had written "exec startgnome"(exactly this) in the above file in the first line.


Now,how do i solve this?i am desperate to see gnome into the act on arch.I have even installed all the software that i need.

You can comment out the two lines in your xorg.conf that are trying to load the type1 and record modules.

To start gnome in your xinitrc file, use the command exec gnome-session
 not exec startgnome.

---

