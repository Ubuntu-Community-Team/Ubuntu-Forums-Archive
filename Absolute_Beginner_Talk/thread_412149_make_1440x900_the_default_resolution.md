---
title: "make 1440x900 the default resolution"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by sway.jd on 2007-04-17
hi everybody.


I'm a newb around ubuntu and linux itself. I got some problems getting ubuntu to run my resolution. 1440x900 (19' widescreen). but I got it.

I'm am running Ubuntu 6.10.


the problem is that everytime I reboot the computer, when I get back at X, it is at 1152x864 (something like this) and I have to go to nvidia settings or the screen resolution embebed in ubuntu and fix it.


in the drivers I have the options to "write to xorg.conf" wich I always do but with 0 result. and in the screen resoltuion of ubuntu I marked the "make default for this monitor" and nothing worked. I figured that I have to edit the xorg.conf myself and that is _not_ a problem since I got a very close relationship with it, when I was trying to make 1440x900 work. lol. spent hours at it.

anyway, anyone knows hot to do the trick?

thnaks in advance!


PS: I'm from Portugal so forgive me for any english mistakes.

---

### Post by ayenack on 2007-04-17
Try visiting this site [http://ubuntuguide.org](http://ubuntuguide.org) scroll down to 1.11.9 Monitors / displays how to enable large widescreen support this should help.

Best of luck. ayenack.

---

### Post by sway.jd on 2007-04-18
thats for large screens. mine its only 19''. but thanks anyway.

---

### Post by Woodsy on 2007-04-18
Hi, I'm also a newbie! Try running nvidia settings as root

type : sudo nvidia-settings 

in a terminal window.

this is how I got mine to work :-)

---

### Post by ayenack on 2007-04-18
> *thats for large screens. mine its only 19''. but thanks anyway.*

sway.jd it tells you how to open your x11 xconf.org config. You need to type this in a terminal. **sudo gedit /etc/X11/xorg.conf** it will open a text file with the config of your monitor. Scroll down till you find **section screen** bit it will look something like this 

[B]Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Monitor        "DELL M770"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x350" "640x480"[/B]

But with more entries. Then enter the desired mode/s res output and save this should make it possible to change res. that's it. Simple.

Best of luck. ayenack.

---

### Post by sway.jd on 2007-04-18
I thought it was pretty clear that I know how to edit the xorg.conf in my 1st post.

and I already did all of that but everytime I reboot it goes into 1152x860 and I have to fix it trough nvidia settings.

so what I want is to put 1440x900 as the default/startup resolution.

---

### Post by ayenack on 2007-04-18
So you did:-\" My mistake try [THIS]("http://ubuntuforums.org/showthread.php?t=83973") link there's lots of useful info and links here that may be of help.

Best of luck. ayenack.

---

### Post by electricshoes on 2007-04-18
If it works on 1440x900 but then reverts back to 1152x. Try and put 1440x900 in your xorg.conf and remove the other resolutions. [B]

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Monitor        "DELL M770"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"[/B]


Sorry if you have already tried this.

---

### Post by sway.jd on 2007-04-18
good idea.

its working now. big thanks both you and ayenack.

---

### Post by electricshoes on 2007-04-18
Awesome, good to hear.

---

### Post by ayenack on 2007-04-18
GOOOOD CATCH!!

Best of luck. ayenack.

---

### Post by SonicSteve on 2007-04-18
> **sway.jd said:**
> I thought it was pretty clear that I know how to edit the xorg.conf in my 1st post.

.

Hi,
I know I haven't been part of this thread but just to clarify, there is semi unwritten rule around here that help is given in a very foolproof way. 
Ie. if I told you to edit your xorg.conf and and you new how to just from me telling you to edit it that would only be good for you. If a complete and utter newbie comes looking for help tthey would then have to search other threads to find out how to edit the xorg.conf and even to find out what the heck it is. 
Hence the sudo gedit /etc/X11/xorg.conf 
I'm not trying to be snotty I hope you understand

---

### Post by sway.jd on 2007-04-18
I was kinda of rough but I wrote that in the initial post so that I wouldnt get answers like: change the Driver "nv" to "nvidia".

I only posted because I had already searched both here and google for a problem like mine and I havent found any. I tried almost everything that even for the slightest detail would have anything to do with the problem and nothing worked and that was what I wanted you to know.

but yes I shouldn't have said that in that way.


cheers! and thanks!

---

### Post by teosd on 2007-06-19
I have the same problem and figured I wouldn't start a new topic because the problem is the same, I can not get Kubuntu Feisty to start on 1440x900 resolution and always have to change it manually from nvidia-settings. I have tried various things, including:

- nvidia-settings -> save to xorg
- sudo nvidia-settings -> save to xorg
- both auto resolution and 1440x900
- creating a modeline myself for 1440x900
- removing all other modelines from xorg.conf
- listening to christian rock while summoning my monitors spirits

When I boot, the nvidia splash screen shows before kdm, the log-in screen is probably 1024 and from there it just keeps on going with 1024.

I have a strong suggestion that KDE's own settings prevent 1440x900 on boot because when I go to system settings -> monitor the resolution bar seems to be all the way to the right and the refresh rate is 52Hz, other choises for refresh rate is given 50, 51, 53, 54 Hz. Also the Hardware tab shows that the driver in use is "nv", there is no "nvidia" on the list of drivers and I dont know how to set it manually.

My monitor is Samsing SyncMaster 940BW 19" widescreen with native 1440x900@60hz and it's connected to the vga port of my geforce 3 (dvi seemed to be burning the colors and I could not get that fixed so I turned back to vga)

Here is my xorg.conf before I changed the resolution manually:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    #Option         "DPMS"
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync

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
        Modes      "1440x900"
    EndSubSection
EndSection

#Section "Extensions"
#    Option         "Composite" "Disable"
#EndSection

```

And here is /var/log/Xorg.0.log before the manual change:

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce3 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.10.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xe0000000 - 0xe007ffff (0x80000) MX[B]
        [1] 0   0       0xdc000000 - 0xdfffffff (0x4000000) MX[B]
        [2] 0   0       0xd4000000 - 0xd4ffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xe4000000 - 0xe40000ff (0x100) MX[B]
        [8] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [9] -1  0       0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
        [10] -1 0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [11] -1 0       0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [19] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [20] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [21] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [22] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[B]
        [23] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [24] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1024x768_60"
BOGUS LENGTH in write keyboard desc, expected 5340, got 5344

```

---

### Post by teosd on 2007-06-20
> **razeshkale said:**
> [http://ubuntuforum.blogspot.com/](http://ubuntuforum.blogspot.com/)

915resolution only works with Intel 800/900 series, which I don't have.
I believe you ment the "Customise Screen Resolution in Ubuntu" topic about resolution on that blog, but as I said, it doesn't work because I can not install 915resolution.

---

