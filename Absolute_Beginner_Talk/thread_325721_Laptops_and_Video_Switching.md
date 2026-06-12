---
title: "Laptops and Video Switching"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by jbeiter on 2006-12-26
Hello,

I'm a new Ubuntu user (and quickly becoming a fan) and a long time Linux user. I just got a Dell D820 for work and I'm very impressed at how easily Ubuntu loaded and how little I had to configure things.

The only thing I'm trying to figure out is what I need to do in order to use the "FN-F8" keys to switch between LCD and external video (for overheads.)  Also, I suspect I will have problems with my docking station. Initially I tried to install Ubuntu on this while docked and the video didn't work at all.

Can anyone tell me what I need to put into my xorg.conf file for the 3 different video scenarios and how I can switch between them on the fly? I checked on the Linux laptops page and a couple of threads here but people seem to have had partial success at best. 

I have a Dell D820 with Quadro Nvidia
Ubuntu 6.10 Edgy EFT

Thank you!

---

### Post by jbeiter on 2006-12-26
bump?

---

### Post by jbeiter on 2006-12-28
I'm hoping someone can get me on track with setting this laptop up. I think I'm pretty close but I'm still stuck.

I'm trying to configure a Dell D820 laptop with Ubuntu and I'm struggling with getting X configured for the docking station and the built in LCD. At this point, I have the docking station display configured but the LCD is out of bounds. It seems like I can get one or the other configured, not both. I've been using Twinview to get them both working but it seems like X is selecting a virtual resolution that is screwing up one display or the other.

wish I could make scroll windows for this, don't know how. I'll post both my xorg.conf file and the log file..

the optimum resolution for the built in LCD is 1280x800, the external display (Dell 1707FP) is 1280x1024.

is there a way to restrict resolution for each device?

xorg.conf:

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg



Section "Files"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
EndSection



Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection



Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection



Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"

Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection


Section "InputDevice"

Identifier "Synaptics Touchpad"

Driver "synaptics"

Option "SendCoreEvents" "true"

Option "Device" "/dev/psaux"

Option "Protocol" "auto-dev"

Option "HorizScrollDelta" "0"

Option "VertScrollDelta" "0"

Option "SHMConfig" "on"

EndSection



Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo" "true"
Option "ConnectedMonitor" "DFP-0, CRT-0"
Option "UseDisplayDevice" "DFP-0, CRT-0"
Option "UseEdidFreqs" "false"
Option "UseEDID" "true"
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "SecondMonitorHorizSync" "30-81"
Option "SecondMonitorVertRefresh" "56-76"
Option "MetaModes" "DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1024x768,CRT-0:1280x1024; DFP-0:800x600,CRT-0:1280x1024"
Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
Option "DPI" "75 x 75"
Option "UseEdidDpi" "false"
Option "FlatPanelProperties" "Scaling = Centered, Dithering = Default"
Option "AddARGBGLXVisuals" "true"
Option "TripleBuffer" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-160
VertRefresh 30-85
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 8
Modes "1280x800" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---------------------------------------------
Xorg.0.log

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux jwb-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 08:27:25 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Generic Monitor"
(**) | |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) FontPath set to:
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/misc/,
/usr/share/fonts/X11/TTF/,
/usr/share/fonts/X11/OTF,
/usr/share/fonts/X11/Type1/,
/usr/share/fonts/X11/CID/,
/usr/share/fonts/X11/100dpi/,
/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
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

(II) PCI: PCI scan (all values are in hex)
---------------snipping PCI scan
---------------
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.2.0
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.0
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
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.8776
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.8776
Module class: X.Org Video Driver
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
compiled for 4.2.0, module version = 1.0.0
Module class: XFree86 XInput Driver
ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA X Driver 1.0-8776 Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 0.1.0
ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
-------- snipping resource ranges----------
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEDID" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0, CRT-0"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "TwinView" "true"
(**) NVIDIA(0): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-81"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56-76"
(**) NVIDIA(0): Option "MetaModes" "DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1024x768,CRT-0:1280x1024; DFP-0:800x600,CRT-0:1280x1024"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0, CRT-0"
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "75 x 75"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0): disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP-0, CRT-0"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 110M at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.fe
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(0): Dell 1707FP (CRT-0)
(--) NVIDIA(0): QDS (DFP-0)
(--) NVIDIA(0): Dell 1707FP (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): Internal Single Link LVDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): "DFP-0:1280x800,CRT-0:1280x1024"
(II) NVIDIA(0): "DFP-0:1280x800,CRT-0:1280x1024"
(II) NVIDIA(0): "DFP-0:1024x768,CRT-0:1280x1024"
(II) NVIDIA(0): "DFP-0:800x600,CRT-0:1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(**) NVIDIA(0): DPI set to (75, 75); computed from "DPI" X config option
(WW) NVIDIA(0): 32-bit ARGB GLX visuals are only supported in depth 24.
(II) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
----snip-----
(II) NVIDIA(0): Setting mode "DFP-0:1280x800,CRT-0:1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "TwinViewXineramaInfoOrder" is not used
(WW) NVIDIA(0): Option "FlatPanelProperties" is not used
(==) RandR enabled
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
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "SHMConfig" "on"
(--) Setting defaults to alps values
(**) Option "VertScrollDelta" "0"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
xkb_keycodes { include "xfree86+aliases(qwerty)" };
xkb_types { include "complete" };
xkb_compatibility { include "complete" };
xkb_symbols { include "pc(pc105)+us+level3(ralt_switch)" };
xkb_geometry { include "pc(pc105)" };
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
------------------------------------------------------------------

Shouldn't X give each device their own resolution? I'm wondering if there is a special way to disable X from imposing a virtual resolution, which seems to be the problem.

---

### Post by jbeiter on 2006-12-30
okay, I never did get twinview working but I at least have it working so that the laptop LCD or the docking station monitor works, depending on if the laptop is docked or not.

If someone could be kind enough to send me a note on how to do the scroll-bar trick, I'll clean these posts up a bit.

Here is my xorg.conf file. If anyone actually works out the twinview part, I'd love a clue.

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
EndSection

#----------------------------------------------------------------------
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "LCD Panel 1920x1200"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0 - 60.0
    ModeLine       "1920x1200" 161.8 1920 2016 2048 2184 1200 1202 1208 1235 +hsync +vsync
    Option         "dpms"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "Videocard vendor"
    BoardName      "nVidia Corporation Unknown device 01d7"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
#---------------------------------------------------------------------------
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "0"
        Option          "SHMConfig"             "on"
EndSection

#Section "Device"
#       Identifier      "Generic Video Card"
#       Driver          "nvidia"
#       BusID           "PCI:1:0:0"
#       Option          "NoLogo"                        "true"
#       Option          "ConnectedMonitor"              "DFP-0, CRT-0"
#       Option          "UseDisplayDevice"              "DFP-0, CRT-0"
#       Option          "UseEdidFreqs"                  "false"
#       Option          "UseEDID"                       "true"
#       Option          "TwinView"                      "true"
#       Option          "TwinViewOrientation"           "Clone"
#       Option          "HorizSync" "DFP-0: 31-90; CRT-0: 30-81"
#       Option          "VertRefresh" "DFP-0: 60-60; CRT-0: 56-76"
##      Option          "SecondMonitorHorizSync"        "30-81"
##      Option          "SecondMonitorVertRefresh"      "56-76"
#       Option          "MetaModes"                     "DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1280x800,CRT-0:1280x1024; DFP-0:1024x768,CRT-0:1280x1024; DFP-0:800x600,CRT-0:1280x1024"
#       Option          "TwinViewXineramaInfoOrder"     "DFP-0, CRT-0"
#       Option          "DPI"                           "75 x 75"
#       Option          "UseEdidDpi"                    "false"
##      Option          "FlatPanelProperties"           "Scaling = Centered, Dithering = Default"
#       Option          "AddARGBGLXVisuals"             "true"
#       Option          "TripleBuffer"                  "true"
#EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
#       HorizSync       30-160
#       VertRefresh     30-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Videocard0"
        #Device         "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

#Section "ServerLayout"
#       Identifier      "Default Layout"
#       Screen          "Default Screen"
#       InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"
#       InputDevice     "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
       Screen          "Screen0"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"
       InputDevice     "Synaptics Touchpad"
EndSection


Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by WakkiTabakki on 2007-01-05
*Edit 2007-01-08: Updated app to 0.2, added checkbox to control whether X should restart*

Hi jbeiter
Sorry to end your one-man-show ;) 
The scrollbar trick is done by writing the stuff within code- or quote-tags.

I've written a small python script that I use to switch between different monitor layouts (it's really a quick hack so I'm a little bit embarrassed posting the code, but still, it may be useful for someone).
I have split my xorg.conf into two parts, one containing the common stuff (module loading, input layout etc) and one with the specifics for each monitor layout. The script simply merges the common-stuff-file with the file for the chosen monitor layout, writes the result to /etc/X11/xorg.conf and restarts gdm. 

I've posted the whole thing as an attachment. I you look in the folder XConfigs, you'll find:
* Common_config.xcfg - which contains the stuff common to all layouts
* xxx.myconf - These contain the specifics for each monitor layout

If you look in the myconf-files, you'll see how I have gotten twinview to work.

I use this on an ASUS A6JC laptop with an Nvidia 7300 Go using the nvidia 97.42 drivers. The laptop screen is refered to as DFT-0 in the myconf-files, the external flat-panel is refered to as CRT-0, and TV-0 is, well, a TV...


Hope it helps!
/N

PS! As always, don't forget to make a backup of your xorg.conf before trying this trick :p

---

