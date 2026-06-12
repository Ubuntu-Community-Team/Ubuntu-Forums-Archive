---
title: "cannot log in after kde installation"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by frtorreira on 2006-07-22
Hi,

I installed Ubuntu yesterday and spent the whole configuring my system. Everything worked great :-) I also installed kde by doing "sudo apt-get install kubuntu-desktop". I could log on to kde and everything worked fine. However, when I turned on the computer this morning, I was not able to log in either to gnome nor kde. When I entered my user name and password, the screen went black and the log in screen appeared after 2 seconds just as for the first time. Fortunately, I could log in to gnome in safe mode, but that is as far as I can go. I am a total newbie and would like to know what's going on. Thanks a lot for your help.

---

### Post by philippe_carlo on 2006-07-22
Can you post the output of 
```
cat ~/.xsession-errors
```? Make sure to do this as the common user (at the console), not root.

---

### Post by frtorreira on 2006-07-22
Thanks. This is what I get:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mapashito"

/etc/gdm/Xsession: Beginning session setup...

X connection to :0.0 broken (explicit kill or server shutdown).
>

---

### Post by philippe_carlo on 2006-07-22
I've encountered similar problems due to the fact that there was an 
```
.Xsession
``` file in the user's home directory that was owned by root. If this is the case here, you should remove it first.

---

### Post by frtorreira on 2006-07-22
Well, i remember (re)moving (cannot remember which) a "wireless" folder when trying to install my wireless adapter (I read this in a thread and tried...). The thing is that I cannot find it anymore (tried with 'wireless' in the search bar in nautilus). Moreover, the computer seemed to work well for several reboots after that folder was moved... Does this mean I need to reinstall the whole Ubuntu?
Apart from that, did you ask me to type .Xsession in the console? It does not recognize this funtion.
Thanks again.

---

### Post by philippe_carlo on 2006-07-22
No,no. Try typing ls -al at the console and see if there is a file called .Xsession. If so, remove it.

---

### Post by frtorreira on 2006-07-22
In my home folder (/home/myname/) I type ls -al and can see .Xauthority and .xsession-errors apart from other files not related to X. I think I will buy a "Linux-for-noobs" book soon :-)

---

### Post by frtorreira on 2006-07-22
After looking for similar problems in the forum I found instructions to remove .ICEauthority and .Xauthority. I did so and checked that they were gone. I tried to log in again, but the problem persisted. When I looked again in my home folder in a new session, .ICEauthority and .Xauthority were still there.

---

### Post by philippe_carlo on 2006-07-22
These files are created every time X is run. You should post the output of 
```
cat /var/log/Xorg.0.log
``` here.

---

### Post by frtorreira on 2006-07-22
Here it is:

        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 3200
        BnkNumberOfImagePages: 3
        LinNumberOfImagePages: 3
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 0
*Mode: 13c (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 4096
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 4096
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 0
*Mode: 13d (1280x1024)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 5120
        XResolution: 1280
        YResolution: 1024
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 5120
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 0
*(WW) (1600x1200,SyncMaster) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,SyncMaster) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,SyncMaster) mode clock 189MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,SyncMaster) mode clock 202.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,SyncMaster) mode clock 229.5MHz exceeds DDC maximum 140MHz
(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
Mode: 13e (1600x1200)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 6400
        XResolution: 1600
        YResolution: 1200
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 6400
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 0
Mode: 13f (1920x1440)
        ModeAttributes: 0x9f
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 1920
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1920
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 140 (1920x1440)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 3840
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 3840
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
*(WW) (1920x1440,SyncMaster) mode clock 234MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,SyncMaster) mode clock 297MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,SyncMaster) mode clock 341.35MHz exceeds DDC maximum 140MHz
(II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
Mode: 141 (1920x1440)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 7680
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 7680
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 0
Mode: 14 (1280x960)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0xa000
        WinFuncPtr: 0xc0002ddd
        BytesPerScanline: 2560
        XResolution: 1280
        YResolution: 960
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 2560
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(WW) VESA(0): config file vrefresh range 50-160Hz not within DDC vrefresh ranges.
(II) VESA(0): SyncMaster: Using hsync range of 30.00-70.00 kHz
(II) VESA(0): SyncMaster: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Not using mode "1152x864" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(--) VESA(0): Display dimensions: (340, 270) mm
(--) VESA(0): DPI set to (95, 96)
(WW) (1280x1024,SyncMaster) mode clock 157.5MHz exceeds DDC maximum 140MHz
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (13d)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (13c)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (13b)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (13a)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xcfff7800 - 0xcfff7fff (0x800) MX[B]
        [5] -1  0       0xcfff7700 - 0xcfff77ff (0x100) MX[B]
        [6] -1  0       0xcfff8000 - 0xcfff8fff (0x1000) MX[B]
        [7] -1  0       0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
        [8] -1  0       0xcfffa000 - 0xcfffafff (0x1000) MX[B]
        [9] -1  0       0xcfff9000 - 0xcfff9fff (0x1000) MX[B]
        [10] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [11] -1 0       0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
        [12] -1 0       0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000c800 - 0x0000c87f (0x80) IX[B]
        [19] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [20] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [21] -1 0       0x0000cc00 - 0x0000cc7f (0x80) IX[B]
        [22] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [23] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [24] -1 0       0x0000d800 - 0x0000d87f (0x80) IX[B]
        [25] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [26] -1 0       0x0000ff00 - 0x0000ff0f (0x10) IX[B]
        [27] -1 0       0x00000c00 - 0x00000c1f (0x20) IX[B]
        [28] -1 0       0x00008c00 - 0x00008c7f (0x80) IX[B](B)
        [29] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [30] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: SiS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor:
(II) VESA(0): VESA VBE OEM Product:
(II) VESA(0): VESA VBE OEM Product Rev:
(II) VESA(0): virtual address = 0xb38b6000,
        physical address = 0xc0000000, size = 67043328
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
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
(**) Option "XkbVariant" "us"
(**) Generic Keyboard: XkbVariant: "us"
(**) Option "XkbOptions" "us"
(**) Generic Keyboard: XkbOptions: "us"
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by philippe_carlo on 2006-07-22
You should probably try reinstalling (or reconfiguring) the Xorg packages. You may want to check what the abover errors are about too.

---

### Post by frtorreira on 2006-07-22
Thanks so much for yor help. I think my xorg is completely sc**wed up. Since I don't know how to repair it I will reinstall Ubuntu again. Otherwise this thread might get veeeeery long. Thanks again.

---

