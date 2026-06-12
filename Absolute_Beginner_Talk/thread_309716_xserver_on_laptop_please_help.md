---
title: "xserver on laptop please help"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by dude420 on 2006-11-30
I've been trying to get an answer to this for a while now, but I guess I have been asking the wrong questions.  I have been trying to get ubuntu to work on my laptop (works great on desktop) but I can only seem to get xserver to work in agp 8 bit.  Not real effective, can't see much.  But it was a start.  I am using a Inspiron 2600 w/ Intel 830mg chip set & 830mg integrated graphics.  I have downloaded and installed the Intel driver per reference page destructions but I get the same xserver failed to start message.  Here is most of my Xorg.0.log - I cut a little for space, if I deleted the wrong stuff please let me know.  Any help would be appreciated.  I am about to give up on this whole laptop thing.:( 

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntulaptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 27 23:24:01 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(--) PCI:*(0:2:0) Intel Corporation 82830 CGC [Chipset Graphics Controller] rev 4, Mem @ 0xe8000000/27, 0xe0000000/19
(--) PCI: (0:2:1) Intel Corporation 82830 CGC [Chipset Graphics Controller] rev 0, Mem @ 0xf0000000/27, 0xe0080000/19
 (II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vga"
(II) Loading /usr/lib/xorg/modules/drivers/vga_drv.so
(II) Module vga: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 4.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) VGA: Generic VGA driver (version 4.1) for chipsets: generic
(II) Primary Device is: PCI 00:02:0
(--) Chipset generic found
(II) resource ranges after xf86ClaimFixedResources() call:
	
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VGA(0): initializing int10.
(WW) VGA(0): Bad V_BIOS checksum
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(**) VGA(0): Depth 8, (--) framebuffer bpp 8
(==) VGA(0): RGB weight 666
(==) VGA(0): Default visual is PseudoColor
(==) VGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) VGA(0): videoRam: 64 kBytes.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) VGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VGA(0): Generic Monitor: Using hsync range of 28.00-49.00 kHz
(II) VGA(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(II) VGA(0): Clock range:  23.17 to  30.32 MHz
(II) VGA(0): Not using default mode "640x350" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VGA(0): Not using default mode "640x400" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VGA(0): Not using default mode "720x400" (insufficient memory for mode)
(II) VGA(0): Not using default mode "360x200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x240" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x240" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x240" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "320x240" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "400x300" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "400x300" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "400x300" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "400x300" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "400x300" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "512x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "512x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "512x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "512x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "512x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) VGA(0): Not using default mode "576x432" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x480" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x512" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x512" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x512" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) VGA(0): Not using default mode "896x672" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) VGA(0): Not using default mode "896x672" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) VGA(0): Not using default mode "928x696" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) VGA(0): Not using default mode "928x696" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) VGA(0): Not using default mode "960x720" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) VGA(0): Not using default mode "960x720" (insufficient memory for mode)
(II) VGA(0): Not using default mode "832x624" (insufficient memory for mode)
(II) VGA(0): Not using default mode "416x312" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1280x800" (insufficient memory for mode)
(II) VGA(0): Not using default mode "640x400" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1152x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "576x384" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) VGA(0): Not using default mode "576x432" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) VGA(0): Not using default mode "700x525" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) VGA(0): Not using default mode "700x525" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) VGA(0): Not using default mode "700x525" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) VGA(0): Not using default mode "700x525" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) VGA(0): Not using default mode "720x450" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) VGA(0): Not using default mode "800x512" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) VGA(0): Not using default mode "840x525" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "960x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) VGA(0): Not using default mode "960x600" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) VGA(0): Not using default mode "960x720" (insufficient memory for mode)
(II) VGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) VGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) VGA(0): Not using default mode "1024x768" (insufficient memory for mode)
(WW) VGA(0): Mode pool is empty
(==) VGA(0): Virtual size is 320x200 (pitch 320)
(**) VGA(0):  Built-in mode "Generic 320x200 default mode": 12.6 MHz (scaled from 25.2 MHz), 31.5 kHz, 70.2 Hz (VScan)
(II) VGA(0): Modeline "Generic 320x200 default mode"   12.59  320 336 384 400  200 206 207 224 vscan 2 -hsync +vsync
(==) VGA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	
(**) Option "dpms"
(**) VGA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
Synaptics DeviceOff called
(II) Open ACPI successful (/var/run/acpid.socket)
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by riven0 on 2006-11-30
dude420, this may sound stupid but have you tried sudo dpkg-reconfigure xserver-xorg?

EDIT: Also, try booting with vga=771. Take a look [here.]("http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem-2.html")

---

### Post by dude420 on 2006-11-30
tried time and time again, like i said i could get xserver running in agp 8 bit but none of the intel drivers listed would work.  Any other suggestions??   and thx

---

### Post by robinl on 2006-11-30
does it work using VESA drivers? Comment out GLX and DRI and things like that just in case when using the VESA driver.  

```
 (WW) VGA(0): Bad V_BIOS checksum
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(**) VGA(0): Depth 8, (--) framebuffer bpp 8
(==) VGA(0): RGB weight 666
(==) VGA(0): Default visual is PseudoColor
(==) VGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) VGA(0): videoRam: 64 kBytes.
```

This is the culprit here, it seems like it didn't detect your graphics card properly and well you can't do much with 64kb of vram.

---

### Post by dude420 on 2006-11-30
O.k. so I've tried the vesa thing w/o glx or dri or vbe still the same xserver failed to start.  ](*,)   Robinl you pointed out my problem, but do you have any other ideas about how to fix this.  When I ran dpkg-reconfigure xserver-xorg I said to give 512kb still nothing.  What do I do next??   thx in advance

---

### Post by CatKiller on 2006-11-30
> **dude420 said:**
> ...When I ran dpkg-reconfigure xserver-xorg I said to give 512kb still nothing...

512 kB is still tiny. Something like 8 MB might be more appropriate. (EDIT: 1024x768 at 24 bits takes just over 2 megs, I think).

What happens if you don't specify anything? Also, many laptops share main memory for their vRAM. It might be worth setting it to whatever number that's set to in the BIOS.

---

### Post by dude420 on 2006-11-30
I've tried to give it up to 128mb still nothing.  When I leave it blank same thing.  It is Intel 830mg integrated graphics on a Dell.  There is no bios setting for the video.  Nothing at all on any screen that says video anything.  And even if it did i couldn't change it.

---

### Post by dude420 on 2006-11-30
Anyone else have any ideas?? Any help would be greatly appreciated.
:D

---

### Post by CatKiller on 2006-11-30
It's likely that you're having two separate problems - the log you posted was definitely not working because you had far too little memory either specified or detected. So after you've corrected that, we can look at what your other problem might be.

Given that your manual describes your graphics as > Inspiron 2600 

    System memory 128 MB | UMA; shared with system memory up to 32 MB


    System memory 256 MB | UMA; shared with system memory up to 48 MB it should certainly be configurable in the BIOS. You'll need to check your documentation for exactly how to do so.

You should be using the i810 driver: > Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, and i945 series
 chips.

EDIT: You could also search around for your model number to see if others have solved problems with your laptop - if you need to specify a kernel option or whatever. Also, if you put [CODE] tags around your log, it will put it in a scrolly box that's marginally easier to read.

---

### Post by novosirj on 2007-03-30
The solution to this problem is that this machine requires BIOS version A08 in order to have Linux work properly. I upgraded a machine last night from A05 to A11 and it went from only displaying in 640x480 to not working at all. I just did the update back to A08 due to some recommendations I found elsewhere on the 'net, and lo and behold, it is working beautifully at 1024x768 in full color.

If you need a link to download the BIOS, it is currently available at [this location]("ftp://ftp.dell.com/bios/I2600A08.exe") on the Dell FTP site. You will need floppies, but it's a SMALL price to pay!

---

