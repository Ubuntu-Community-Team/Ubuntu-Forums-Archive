---
title: "Cube G4 Lubuntu 14.04.3 display freeze"
date: 2016-01-03
forum: Apple Hardware Users
---

### Post by kyle69 on 2016-01-03
I finally got my somewhat hod-rodded cube, (1ghz cpu, 1.5gb memory, radeon 7500 mac), working by using the magic yaboot sequence of:

[noparse]radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1[/noparse]

I got a nice desktop and everything seemed ok, but then I get random freezes where it's locked up but the mouse still moves, (but doesn't click). I can't seem to use any keyboard commands and I can't use ssh to get in remotely either. It seems to be triggered by 'big' graphics events, large window resize, etc. Looking at the task manager, I was surprised how much cpu is used just by dragging windows around. The other thing I see wonky so far is I get a "0000:00:10:0 Invalid ROM contents" at startup.

I wasn't sure what log parts to post, so suggestions are welcome, many thanks-

---

### Post by este.el.paz on 2016-01-04
> **kyle69 said:**
> I finally got my somewhat hod-rodded cube, (1ghz cpu, 1.5gb memory, radeon 7500 mac), by using the magic yaboot sequence of:

radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1

I got a nice desktop and everything seemed ok, but then I get random freezes where it's locked up but the mouse still moves, (but doesn't click). I can't seem to use any keyboard commands and I can't use ssh to get in remotely either. It seems to be triggered by 'big' graphics events, large window resize, etc. Looking at the task manager, I was surprised how much cpu is used just by dragging windows around. The other thing I see wonky so far is I get a "0000:00:10:0 Invalid ROM contents" at startup.

I wasn't sure what log parts to post, so suggestions are welcome, many thanks-

kyle:

Yes, the "random freezes" in the GUI is something I've experienced with Lu 14 . . . recently, and in subsequent versions of Lu for PPC.  There is probably a bug report that you could add your name to . . . .  Nothing seems to happen too fast in PPC-land.  I wouldn't worry too much about the "invalid ROM contents" error, as long as things are running OK in the GUI; I tried to boot the Lu 14.04.2 live DVD a few days ago in my PM 3,1 and got a bunch of "SQUASHFS" errors . . . those are more serious, as the GUI doesn't load . . . it's a "crash."

I have a "XFCE" desktop that I added to a ubuntu 14.04 mini installer install on my iBook 933 MHz . . . adding the boot params to the Yaboot config file after installation . . . technically Xubuntu doesn't support PPC, but I kept having the same issues you are talking about with Lu, so . . . built my own, and XFCE seems to run pretty well on the 14.o4 base.

And, back over in my PM . . . ATI video card . . . looks like I tweaked my install or the Yaboot loader for my Xu 12.04/ToriOS install . . . so looking around for ways to fix it . . . or, nuke/pave . . . I might try my mini installer method of 14.04 . . . and add a DE . . . possibly XFCE again, or, maybe GNOME!!!!???

Lots of games to try out . . . try them . . . .

e...

---

### Post by rican-linux on 2016-01-04
What video card does the cube have?

---

### Post by kyle69 on 2016-01-04
Thanks este, it's nice to know I wasn't totally losing my head... it was really weird to have the mouse sort of working but nothing else. I will certainly try xfce, or possibly the debian/openbox setup as outlined by ppcluddite. I originally went this route, but I wasn't getting any joy, (black screen). That was before discovering the yaboot sequence though, so I went back to what I sort of know- lubuntu. I've been running lu with very good results on an old mactel mini that I boosted the cpu, etc. 

I also noticed another thing odd last night, I was using a 20" cinema monitor and I thought maybe the resolution was pushing the radeon 7500 too hard. So I plugged in a 15" lcd studio display, did my yaboot trick and... nothing, (blackscreen). It was getting late so I gave up there, although I might try forcing the resolution on the 15" for grins. 

If I ever get the cube in a decent place, it might be time to look at my cranky g5 again... :eek:

-kyle

---

### Post by kyle69 on 2016-01-04
> **rican-linux said:**
> What video card does the cube have?

It's a radeon 7500 mac edition, using the adc output, thanks-

---

### Post by este.el.paz on 2016-01-04
> **kyle69 said:**
> 
If I ever get the cube in a decent place, it might be time to look at my cranky g5 again... :eek:

-kyle

Talk with rican-linux about the g5 world . . . .

---

### Post by kyle69 on 2016-01-04
I'm now trying a debian-jessie/openbox setup on the cube. Seems a little cleaner/lighter and isn't working the wee powerpc so hard. But still getting the exact same lockups, the system freezes but can still move the mouse cursor around, (but no clicks or keyboard). This chunk of Lucite would be sweet if I can just get around the crashes.

---

### Post by rican-linux on 2016-01-05
if it is freezing try turning off HW acceleration in Xorg.

```
Option  NoRenderAccel  "True"
```

---

### Post by kyle69 on 2016-01-05
I now added:

Option "NoRenderAccel" "True"

to the Section "Device" area of an xorg.conf file I generated earlier. Same symptoms.

---

### Post by este.el.paz on 2016-01-05
> **kyle69 said:**
> I'm now trying a debian-jessie/openbox setup on the cube. Seems a little cleaner/lighter and isn't working the wee powerpc so hard. But still getting the exact same lockups, the system freezes but can still move the mouse cursor around, (but no clicks or keyboard). This chunk of Lucite would be sweet if I can just get around the crashes.

@kyle:

Well, ubuntu uses the debian kernel, so possibly changing to debian would not get you around the problem . . . ???  Not sure, I've been wrong countless times . . . .  Also, speaking of your Yaboot.conf file . . . did you add those boot params you listed at the beginning to the "append" line ????  just a thought.

e..

---

### Post by abtabt on 2016-01-05
kyle 
give us xorg.conf and Xorg log

elpaz 
ubuntu uses the debian kernel NOT

---

### Post by kyle69 on 2016-01-05
@este I was trying the ppc luddite's ([ppcluddite.blogspot.com/]("http://ppcluddite.blogspot.com/")) approach because he seems to like a bare-bones setup-

@abtabt thanks-

xorg.conf

```
Section "ServerLayout"    Identifier     "X.org Configured"
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
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "ColorTiling"            # [<bool>]
        #Option     "ColorTiling2D"          # [<bool>]
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "AccelMethod"            # <str>
        #Option     "EXAVSync"               # [<bool>]
        #Option     "EXAPixmaps"             # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
    Option      "NoRenderAccel" "True"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:0:16:0"
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

log:

```
[    11.081] X.Org X Server 1.16.4
Release Date: 2014-12-20
[    11.083] X Protocol Version 11, Revision 0
[    11.083] Build Operating System: Linux 3.2.0-4-powerpc64 ppc Debian
[    11.083] Current Operating System: Linux toaster 3.16.0-4-powerpc #1 Debian 3.16.7-ckt20-1+deb8u1 (2015-12-14) ppc
[    11.084] Kernel command line: root=UUID=11758325-78b3-4cc0-9cb2-d0cd860c4e5d ro radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1 
[    11.084] Build Date: 11 February 2015  01:13:01AM
[    11.084] xorg-server 2:1.16.4-1 (http://www.debian.org/support) 
[    11.084] Current version of pixman: 0.32.6
[    11.084]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.084] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.084] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  5 12:23:17 2016
[    11.092] (==) Using config file: "/etc/X11/xorg.conf"
[    11.092] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.097] (==) ServerLayout "X.org Configured"
[    11.097] (**) |-->Screen "Screen0" (0)
[    11.097] (**) |   |-->Monitor "Monitor0"
[    11.098] (**) |   |-->Device "Card0"
[    11.098] (**) |-->Input Device "Mouse0"
[    11.098] (**) |-->Input Device "Keyboard0"
[    11.098] (==) Automatically adding devices
[    11.098] (==) Automatically enabling devices
[    11.098] (==) Automatically adding GPU devices
[    11.115] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.115]     Entry deleted from font path.
[    11.117] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.117]     Entry deleted from font path.
[    11.117] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    11.117] (**) ModulePath set to "/usr/lib/xorg/modules"
[    11.117] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    11.117] (WW) Disabling Mouse0
[    11.117] (WW) Disabling Keyboard0
[    11.118] (II) Loader magic: 0x205ce698
[    11.118] (II) Module ABI versions:
[    11.118]     X.Org ANSI C Emulation: 0.4
[    11.118]     X.Org Video Driver: 18.0
[    11.118]     X.Org XInput driver : 21.0
[    11.118]     X.Org Server Extension : 8.0
[    11.119] (II) xfree86: Adding drm device (/dev/dri/card0)
[    11.121] (--) PCI:*(0:0:16:0) 1002:5157:1002:5157 rev 0, Mem @ 0x98000000/134217728, 0x90000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    11.124] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    11.125] (II) LoadModule: "glx"
[    11.131] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.165] (II) Module glx: vendor="X.Org Foundation"
[    11.165]     compiled for 1.16.4, module version = 1.0.0
[    11.165]     ABI class: X.Org Server Extension, version 8.0
[    11.165] (==) AIGLX enabled
[    11.167] (II) LoadModule: "radeon"
[    11.167] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    11.179] (II) Module radeon: vendor="X.Org Foundation"
[    11.179]     compiled for 1.16.1, module version = 7.5.0
[    11.179]     Module class: X.Org Video Driver
[    11.180]     ABI class: X.Org Video Driver, version 18.0
[    11.180] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    11.214] (--) using VT number 2


[    11.242] (II) [KMS] Kernel modesetting enabled.
[    11.242] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    11.242] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    11.242] (==) RADEON(0): Default visual is TrueColor
[    11.242] (**) RADEON(0): Option "NoRenderAccel" "True"
[    11.243] (==) RADEON(0): RGB weight 888
[    11.243] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    11.243] (--) RADEON(0): Chipset: "ATI Radeon 7500 QW (AGP/PCI)" (ChipID = 0x5157)
[    11.243] (II) Loading sub module "dri2"
[    11.243] (II) LoadModule: "dri2"
[    11.243] (II) Module "dri2" already built-in
[    11.243] (II) Loading sub module "exa"
[    11.243] (II) LoadModule: "exa"
[    11.243] (II) Loading /usr/lib/xorg/modules/libexa.so
[    11.251] (II) Module exa: vendor="X.Org Foundation"
[    11.251]     compiled for 1.16.4, module version = 2.6.0
[    11.251]     ABI class: X.Org Video Driver, version 18.0
[    11.251] (II) RADEON(0): KMS Color Tiling: disabled
[    11.251] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    11.252] (II) RADEON(0): KMS Pageflipping: enabled
[    11.252] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    11.358] (II) RADEON(0): Output DVI-0 using monitor section Monitor0
[    11.367] (II) RADEON(0): Output VGA-0 has no monitor section
[    11.373] (II) RADEON(0): Output S-video has no monitor section
[    11.436] (II) RADEON(0): EDID for output DVI-0
[    11.436] (II) RADEON(0): Manufacturer: APP  Model: 9219  Serial#: 50202096
[    11.436] (II) RADEON(0): Year: 2004  Week: 19
[    11.436] (II) RADEON(0): EDID Version: 1.3
[    11.436] (II) RADEON(0): Digital Display Input
[    11.436] (II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[    11.436] (II) RADEON(0): Gamma: 2.20
[    11.436] (II) RADEON(0): DPMS capabilities: Off
[    11.436] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    11.436] (II) RADEON(0): Default color space is primary color space
[    11.436] (II) RADEON(0): First detailed timing is preferred mode
[    11.436] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    11.436] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    11.436] (II) RADEON(0): Manufacturer's mask: 0
[    11.436] (II) RADEON(0): Supported detailed timing:
[    11.436] (II) RADEON(0): clock: 117.1 MHz   Image Size:  433 x 270 mm
[    11.436] (II) RADEON(0): h_active: 1680  h_sync: 1744  h_sync_end 1776 h_blank_end 1840 h_border: 0
[    11.437] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1056 v_blanking: 1062 v_border: 0
[    11.437] (II) RADEON(0): Monitor name: Apple Cinema
[    11.437] (II) RADEON(0): Monitor name: Display
[    11.437] (II) RADEON(0): Unknown vendor-specific block 0
[    11.437] (II) RADEON(0): Number of EDID sections to follow: 1
[    11.437] (II) RADEON(0): EDID (in hex):
[    11.437] (II) RADEON(0):     00ffffffffffff0006101992f005fe02
[    11.437] (II) RADEON(0):     130e0103802b1b782ee691a3544a9926
[    11.437] (II) RADEON(0):     0f505400000001010101010101010101
[    11.437] (II) RADEON(0):     010101010101c12d90a0601a0c404020
[    11.437] (II) RADEON(0):     3300b10e1100001e000000fc00417070
[    11.437] (II) RADEON(0):     6c652043696e656d6120000000fc0044
[    11.437] (II) RADEON(0):     6973706c61790a000000000000000000
[    11.437] (II) RADEON(0):     00061003001c00030000000000000190
[    11.437] (II) RADEON(0):     400102000000007600a500a50102031a
[    11.437] (II) RADEON(0):     1aa80100000000004000000000000000
[    11.437] (II) RADEON(0):     00000000000000000000000000000000
[    11.437] (II) RADEON(0):     00000000000000000000000000000000
[    11.437] (II) RADEON(0):     00000000000000000000000000000000
[    11.437] (II) RADEON(0):     00000000000000000000000000000000
[    11.437] (II) RADEON(0):     00000000000000000000000000000000
[    11.437] (II) RADEON(0):     000000000000000000000000000000da
[    11.437] (II) RADEON(0): Printing probed modes for output DVI-0
[    11.438] (II) RADEON(0): Modeline "1680x1050"x59.9  117.13  1680 1744 1776 1840  1050 1053 1056 1062 +hsync +vsync (63.7 kHz eP)
[    11.443] (II) RADEON(0): EDID for output VGA-0
[    11.449] (II) RADEON(0): EDID for output S-video
[    11.449] (II) RADEON(0): Output DVI-0 connected
[    11.449] (II) RADEON(0): Output VGA-0 disconnected
[    11.449] (II) RADEON(0): Output S-video disconnected
[    11.449] (II) RADEON(0): Using exact sizes for initial modes
[    11.449] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
[    11.450] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    11.450] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:2000000 visible:1df4000
[    11.450] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    11.450] (==) RADEON(0): DPI set to (96, 96)
[    11.450] (II) Loading sub module "fb"
[    11.450] (II) LoadModule: "fb"
[    11.450] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.456] (II) Module fb: vendor="X.Org Foundation"
[    11.456]     compiled for 1.16.4, module version = 1.0.0
[    11.456]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.456] (II) Loading sub module "ramdac"
[    11.456] (II) LoadModule: "ramdac"
[    11.456] (II) Module "ramdac" already built-in
[    11.456] (--) Depth 24 pixmap format is 32 bpp
[    11.458] (II) RADEON(0): [DRI2] Setup complete
[    11.458] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    11.458] (II) RADEON(0): [DRI2]   VDPAU driver: radeon
[    11.459] (II) RADEON(0): Front buffer size: 7088K
[    11.459] (II) RADEON(0): VRAM usage limit set to 21196K
[    11.465] (==) RADEON(0): Backing store enabled
[    11.465] (II) RADEON(0): Direct rendering enabled
[    11.465] (II) EXA(0): Driver allocated offscreen pixmaps
[    11.465] (II) EXA(0): Driver registered support for the following operations:
[    11.465] (II)         Solid
[    11.465] (II)         Copy
[    11.465] (II)         UploadToScreen
[    11.465] (II)         DownloadFromScreen
[    11.465] (II) RADEON(0): Acceleration enabled
[    11.465] (==) RADEON(0): DPMS enabled
[    11.465] (==) RADEON(0): Silken mouse enabled
[    11.467] (II) RADEON(0): Set up textured video
[    11.467] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    11.467] (II) RADEON(0): [XvMC] Extension initialized.
[    11.467] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    11.471] (--) RandR disabled
[    11.538] (II) SELinux: Disabled on system
[    11.619] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    11.619] (II) AIGLX: enabled GLX_ARB_create_context
[    11.619] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    11.619] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    11.619] (II) AIGLX: enabled GLX_INTEL_swap_event
[    11.619] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    11.619] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    11.619] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    11.619] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    11.620] (II) AIGLX: Loaded and initialized radeon
[    11.620] (II) GLX: Initialized DRI2 GL provider for screen 0
[    11.954] (II) RADEON(0): Setting screen physical size to 444 x 277
[    12.346] (II) config/udev: Adding input device Apple Computer, Inc. Speakers (/dev/input/event1)
[    12.346] (**) Apple Computer, Inc. Speakers: Applying InputClass "evdev keyboard catchall"
[    12.346] (II) LoadModule: "evdev"
[    12.347] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.353] (II) Module evdev: vendor="X.Org Foundation"
[    12.353]     compiled for 1.16.0, module version = 2.9.0
[    12.353]     Module class: X.Org XInput Driver
[    12.353]     ABI class: X.Org XInput driver, version 21.0
[    12.353] (II) Using input driver 'evdev' for 'Apple Computer, Inc. Speakers'
[    12.354] (**) Apple Computer, Inc. Speakers: always reports core events
[    12.354] (**) evdev: Apple Computer, Inc. Speakers: Device: "/dev/input/event1"
[    12.354] (--) evdev: Apple Computer, Inc. Speakers: Vendor 0x5ac Product 0x1101
[    12.354] (--) evdev: Apple Computer, Inc. Speakers: Found keys
[    12.354] (II) evdev: Apple Computer, Inc. Speakers: Configuring as keyboard
[    12.354] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1:1.2/0003:05AC:1101.0001/input/input1/event1"
[    12.354] (II) XINPUT: Adding extended input device "Apple Computer, Inc. Speakers" (type: KEYBOARD, id 6)
[    12.354] (**) Option "xkb_rules" "evdev"
[    12.354] (**) Option "xkb_model" "pc105"
[    12.354] (**) Option "xkb_layout" "us"
[    12.357] (II) config/udev: Adding input device Alps Electric Apple Extended USB Keyboard (/dev/input/event2)
[    12.357] (**) Alps Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    12.357] (II) Using input driver 'evdev' for 'Alps Electric Apple Extended USB Keyboard'
[    12.357] (**) Alps Electric Apple Extended USB Keyboard: always reports core events
[    12.357] (**) evdev: Alps Electric Apple Extended USB Keyboard: Device: "/dev/input/event2"
[    12.358] (--) evdev: Alps Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    12.358] (--) evdev: Alps Electric Apple Extended USB Keyboard: Found keys
[    12.358] (II) evdev: Alps Electric Apple Extended USB Keyboard: Configuring as keyboard
[    12.358] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:05AC:0204.0003/input/input2/event2"
[    12.358] (II) XINPUT: Adding extended input device "Alps Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 7)
[    12.358] (**) Option "xkb_rules" "evdev"
[    12.358] (**) Option "xkb_model" "pc105"
[    12.358] (**) Option "xkb_layout" "us"
[    12.360] (II) config/udev: Adding input device Alps Electric Apple Extended USB Keyboard (/dev/input/event3)
[    12.361] (**) Alps Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    12.361] (II) Using input driver 'evdev' for 'Alps Electric Apple Extended USB Keyboard'
[    12.361] (**) Alps Electric Apple Extended USB Keyboard: always reports core events
[    12.361] (**) evdev: Alps Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
[    12.361] (--) evdev: Alps Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    12.361] (--) evdev: Alps Electric Apple Extended USB Keyboard: Found keys
[    12.361] (II) evdev: Alps Electric Apple Extended USB Keyboard: Configuring as keyboard
[    12.361] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:05AC:0204.0004/input/input3/event3"
[    12.361] (II) XINPUT: Adding extended input device "Alps Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 8)
[    12.361] (**) Option "xkb_rules" "evdev"
[    12.361] (**) Option "xkb_model" "pc105"
[    12.361] (**) Option "xkb_layout" "us"
[    12.363] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/event4)
[    12.364] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    12.364] (II) Using input driver 'evdev' for 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'
[    12.364] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
[    12.364] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
[    12.364] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x47
[    12.364] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
[    12.364] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    12.364] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found relative axes
[    12.364] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    12.364] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
[    12.364] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    12.364] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    12.364] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.365] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:045E:0047.0005/input/input4/event4"
[    12.365] (II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 9)
[    12.365] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    12.365] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    12.365] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    12.366] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    12.366] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    12.367] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    12.367] (II) No input driver specified, ignoring this device.
[    12.367] (II) This device may have been added with another device file.
[    12.369] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    12.369] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    12.369] (II) Using input driver 'evdev' for 'PMU'
[    12.369] (**) PMU: always reports core events
[    12.369] (**) evdev: PMU: Device: "/dev/input/event0"
[    12.369] (--) evdev: PMU: Vendor 0x1 Product 0x1
[    12.369] (--) evdev: PMU: Found keys
[    12.369] (II) evdev: PMU: Configuring as keyboard
[    12.369] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    12.369] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD, id 10)
[    12.369] (**) Option "xkb_rules" "evdev"
[    12.370] (**) Option "xkb_model" "pc105"
[    12.370] (**) Option "xkb_layout" "us"
[    12.371] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event5)
[    12.371] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    12.372] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    12.372] (**) Mouseemu virtual keyboard: always reports core events
[    12.372] (**) evdev: Mouseemu virtual keyboard: Device: "/dev/input/event5"
[    12.372] (--) evdev: Mouseemu virtual keyboard: Vendor 0x1f Product 0x1f
[    12.372] (--) evdev: Mouseemu virtual keyboard: Found keys
[    12.372] (II) evdev: Mouseemu virtual keyboard: Configuring as keyboard
[    12.372] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    12.372] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD, id 11)
[    12.372] (**) Option "xkb_rules" "evdev"
[    12.372] (**) Option "xkb_model" "pc105"
[    12.372] (**) Option "xkb_layout" "us"
[    12.374] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event6)
[    12.374] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    12.374] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    12.374] (**) Mouseemu virtual mouse: always reports core events
[    12.374] (**) evdev: Mouseemu virtual mouse: Device: "/dev/input/event6"
[    12.375] (--) evdev: Mouseemu virtual mouse: Vendor 0x1f Product 0x1e
[    12.375] (--) evdev: Mouseemu virtual mouse: Found 3 mouse buttons
[    12.375] (--) evdev: Mouseemu virtual mouse: Found scroll wheel(s)
[    12.375] (--) evdev: Mouseemu virtual mouse: Found relative axes
[    12.375] (--) evdev: Mouseemu virtual mouse: Found x and y relative axes
[    12.375] (II) evdev: Mouseemu virtual mouse: Configuring as mouse
[    12.375] (II) evdev: Mouseemu virtual mouse: Adding scrollwheel support
[    12.375] (**) evdev: Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    12.375] (**) evdev: Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.375] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    12.375] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE, id 12)
[    12.375] (II) evdev: Mouseemu virtual mouse: initialized for relative axes.
[    12.376] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    12.376] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    12.376] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    12.376] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4
[    12.377] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse1)
[    12.377] (II) No input driver specified, ignoring this device.
[    12.377] (II) This device may have been added with another device file.
[    12.390] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse1)
[    12.390] (II) No input driver specified, ignoring this device.
[    12.390] (II) This device may have been added with another device file.
[    12.393] (II) config/udev: removing device Mouseemu virtual keyboard
[    12.393] (II) evdev: Mouseemu virtual keyboard: Close
[    12.394] (II) UnloadModule: "evdev"
[    12.394] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event5)
[    12.394] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    12.394] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    12.395] (**) Mouseemu virtual keyboard: always reports core events
[    12.395] (**) evdev: Mouseemu virtual keyboard: Device: "/dev/input/event5"
[    12.395] (--) evdev: Mouseemu virtual keyboard: Vendor 0x1f Product 0x1f
[    12.395] (--) evdev: Mouseemu virtual keyboard: Found keys
[    12.395] (II) evdev: Mouseemu virtual keyboard: Configuring as keyboard
[    12.395] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    12.395] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD, id 11)
[    12.395] (**) Option "xkb_rules" "evdev"
[    12.395] (**) Option "xkb_model" "pc105"
[    12.395] (**) Option "xkb_layout" "us"
[    12.396] (II) config/udev: removing device Mouseemu virtual mouse
[    12.398] (II) evdev: Mouseemu virtual mouse: Close
[    12.398] (II) UnloadModule: "evdev"
[    12.399] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event6)
[    12.399] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    12.399] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    12.399] (**) Mouseemu virtual mouse: always reports core events
[    12.399] (**) evdev: Mouseemu virtual mouse: Device: "/dev/input/event6"
[    12.399] (--) evdev: Mouseemu virtual mouse: Vendor 0x1f Product 0x1e
[    12.399] (--) evdev: Mouseemu virtual mouse: Found 3 mouse buttons
[    12.399] (--) evdev: Mouseemu virtual mouse: Found scroll wheel(s)
[    12.399] (--) evdev: Mouseemu virtual mouse: Found relative axes
[    12.399] (--) evdev: Mouseemu virtual mouse: Found x and y relative axes
[    12.399] (II) evdev: Mouseemu virtual mouse: Configuring as mouse
[    12.399] (II) evdev: Mouseemu virtual mouse: Adding scrollwheel support
[    12.400] (**) evdev: Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    12.400] (**) evdev: Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.400] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    12.400] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE, id 12)
[    12.400] (II) evdev: Mouseemu virtual mouse: initialized for relative axes.
[    12.400] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    12.400] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    12.401] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    12.401] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4



```

---

### Post by abtabt on 2016-01-05
long shot
try 

rename xorg.conf to xorg.confbak 

nomodeset video=radeonfb:off video=offb:off radeon.agpmode=-1 single
 

reboot

if you get CLI just   Ctrl+D       To boot up

if no change

next try 

nomodeset radeon.agpmode=-1 single

if you get CLI just   Ctrl+D       To boot up

---

### Post by kyle69 on 2016-01-05
@abtabt your first yaboot config didn't boot to the CLI, the second one did. However, it failed in the same way after a short bit. In any case I thought nomodeset turns off KMS, and also was under the impression that KMS is desirable with the more recent kernels. 

Here is a syslog copy, maybe there are some clues:

```
Jan  4 19:32:55 toaster rsyslogd: [origin software="rsyslogd" swVersion="8.4.2" x-pid="543" x-info="http://www.rsyslog.com"] startJan  4 19:32:55 toaster systemd-modules-load[126]: Inserted module 'lp'
Jan  4 19:32:55 toaster systemd-modules-load[126]: Failed to find module 'ppdev'
Jan  4 19:32:55 toaster systemd-modules-load[126]: Inserted module 'parport_pc'
Jan  4 19:32:55 toaster systemd[1]: Started Create Static Device Nodes in /dev.
Jan  4 19:32:55 toaster systemd[1]: Starting udev Kernel Device Manager...
Jan  4 19:32:55 toaster systemd[1]: Started udev Kernel Device Manager.
Jan  4 19:32:55 toaster systemd[1]: Starting Copy rules generated while the root was ro...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Tune IDE hard disks...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Set preliminary keymap...
Jan  4 19:32:55 toaster systemd[1]: Started Copy rules generated while the root was ro.
Jan  4 19:32:55 toaster hdparm[148]: Setting parameters of disc: (none).
Jan  4 19:32:55 toaster systemd[1]: Started LSB: Tune IDE hard disks.
Jan  4 19:32:55 toaster systemd-modules-load[126]: Inserted module 'airport'
Jan  4 19:32:55 toaster systemd-modules-load[126]: Failed to find module 'apm_emu'
Jan  4 19:32:55 toaster systemd[1]: systemd-modules-load.service: main process exited, code=exited, status=1/FAILURE
Jan  4 19:32:55 toaster systemd[1]: Failed to start Load Kernel Modules.
Jan  4 19:32:55 toaster systemd[1]: Unit systemd-modules-load.service entered failed state.
Jan  4 19:32:55 toaster systemd[1]: Found device OWC_Mercury_Electra_3G_SSD swap.
Jan  4 19:32:55 toaster systemd[1]: Starting Sound Card.
Jan  4 19:32:55 toaster systemd[1]: Reached target Sound Card.
Jan  4 19:32:55 toaster systemd[1]: Starting system-systemd\x2drfkill.slice.
Jan  4 19:32:55 toaster systemd[1]: Created slice system-systemd\x2drfkill.slice.
Jan  4 19:32:55 toaster systemd[1]: Starting system-ifup.slice.
Jan  4 19:32:55 toaster systemd[1]: Created slice system-ifup.slice.
Jan  4 19:32:55 toaster systemd[1]: Activating swap /dev/disk/by-uuid/3e5e50c4-f33d-4fce-81e1-d6d45f990c09...
Jan  4 19:32:55 toaster systemd[1]: Starting system-systemd\x2dbacklight.slice.
Jan  4 19:32:55 toaster systemd[1]: Created slice system-systemd\x2dbacklight.slice.
Jan  4 19:32:55 toaster systemd[1]: Mounted FUSE Control File System.
Jan  4 19:32:55 toaster systemd[1]: Started LSB: Set preliminary keymap.
Jan  4 19:32:55 toaster keyboard-setup[150]: Setting preliminary keymap...done.
Jan  4 19:32:55 toaster systemd[1]: Starting Remount Root and Kernel File Systems...
Jan  4 19:32:55 toaster systemd[1]: Starting Swap.
Jan  4 19:32:55 toaster systemd[1]: Reached target Swap.
Jan  4 19:32:55 toaster systemd[1]: Started Remount Root and Kernel File Systems.
Jan  4 19:32:55 toaster systemd[1]: Starting Load/Save RF Kill Switch Status of rfkill0...
Jan  4 19:32:55 toaster systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:appledisplay0...
Jan  4 19:32:55 toaster systemd[1]: Starting Various fixups to make systemd work better on Debian...
Jan  4 19:32:55 toaster systemd[1]: Starting Load/Save Random Seed...
Jan  4 19:32:55 toaster systemd[1]: Starting Local File Systems (Pre).
Jan  4 19:32:55 toaster systemd[1]: Reached target Local File Systems (Pre).
Jan  4 19:32:55 toaster systemd[1]: Starting Local File Systems.
Jan  4 19:32:55 toaster systemd[1]: Reached target Local File Systems.
Jan  4 19:32:55 toaster systemd[1]: Starting Create Volatile Files and Directories...
Jan  4 19:32:55 toaster systemd[1]: Starting Remote File Systems.
Jan  4 19:32:55 toaster systemd[1]: Reached target Remote File Systems.
Jan  4 19:32:55 toaster systemd[1]: Starting Trigger Flushing of Journal to Persistent Storage...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Prepare console...
Jan  4 19:32:55 toaster systemd[1]: Started Load/Save RF Kill Switch Status of rfkill0.
Jan  4 19:32:55 toaster systemd[1]: Started Load/Save Screen Backlight Brightness of backlight:appledisplay0.
Jan  4 19:32:55 toaster systemd[1]: Started Various fixups to make systemd work better on Debian.
Jan  4 19:32:55 toaster systemd[1]: Started Load/Save Random Seed.
Jan  4 19:32:55 toaster systemd[1]: Started Create Volatile Files and Directories.
Jan  4 19:32:55 toaster kbd[304]: Setting console screen modes.
Jan  4 19:32:55 toaster systemd[1]: Started Trigger Flushing of Journal to Persistent Storage.
Jan  4 19:32:55 toaster kbd[304]: setterm: $TERM is not defined.
Jan  4 19:32:55 toaster systemd[1]: Started LSB: Prepare console.
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Set console font and keymap...
Jan  4 19:32:55 toaster systemd[1]: Starting Update UTMP about System Boot/Shutdown...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Raise network interfaces....
Jan  4 19:32:55 toaster systemd[1]: Started Update UTMP about System Boot/Shutdown.
Jan  4 19:32:55 toaster networking[337]: Configuring network interfaces...done.
Jan  4 19:32:55 toaster systemd[1]: Started LSB: Raise network interfaces..
Jan  4 19:32:55 toaster systemd[1]: Starting ifup for eth0...
Jan  4 19:32:55 toaster systemd[1]: Started ifup for eth0.
Jan  4 19:32:55 toaster systemd[1]: Starting Network.
Jan  4 19:32:55 toaster systemd[1]: Reached target Network.
Jan  4 19:32:55 toaster systemd[1]: Starting Network is Online.
Jan  4 19:32:55 toaster systemd[1]: Reached target Network is Online.
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: RPC portmapper replacement...
Jan  4 19:32:55 toaster kernel: [    0.000000] Using PowerMac machine description
Jan  4 19:32:55 toaster kernel: [    0.000000] Total memory = 1536MB; using 4096kB for hash table (at cfc00000)
Jan  4 19:32:55 toaster kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  4 19:32:55 toaster kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  4 19:32:55 toaster kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  4 19:32:55 toaster kernel: [    0.000000] Linux version 3.16.0-4-powerpc (debian-kernel@lists.debian.org) (gcc version 4.8.4 (Debian 4.8.4-1) ) #1 Debian 3.16.7-ckt20-1+deb8u1 (2015-12-14)
Jan  4 19:32:55 toaster kernel: [    0.000000] Found initrd at 0xc1600000:0xc2369000
Jan  4 19:32:55 toaster kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x08
Jan  4 19:32:55 toaster kernel: [    0.000000] Mapped at 0xff7c0000
Jan  4 19:32:55 toaster kernel: [    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xff740000
Jan  4 19:32:55 toaster kernel: [    0.000000] Processor NAP mode on idle enabled.
Jan  4 19:32:55 toaster kernel: [    0.000000] PowerMac motherboard: PowerMac G4 Cube
Jan  4 19:32:55 toaster kernel: [    0.000000] bootconsole [udbg0] enabled
Jan  4 19:32:55 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
Jan  4 19:32:55 toaster kernel: [    0.000000] PCI host bridge /pci@f0000000  ranges:
Jan  4 19:32:55 toaster kernel: [    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
Jan  4 19:32:55 toaster kernel: [    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
Jan  4 19:32:55 toaster kernel: [    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
Jan  4 19:32:55 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
Jan  4 19:32:55 toaster kernel: [    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
Jan  4 19:32:55 toaster kernel: [    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
Jan  4 19:32:55 toaster kernel: [    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
Jan  4 19:32:55 toaster kernel: [    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
Jan  4 19:32:55 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
Jan  4 19:32:55 toaster kernel: [    0.000000] PCI host bridge /pci@f4000000  ranges:
Jan  4 19:32:55 toaster kernel: [    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
Jan  4 19:32:55 toaster kernel: [    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
Jan  4 19:32:55 toaster kernel: [    0.000000] via-pmu: Server Mode is disabled
Jan  4 19:32:55 toaster kernel: [    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: Checking bank 0...
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: gen0=166, gen1=165
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: Active bank is: 0
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: OF partition at 0x210
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: XP partition at 0x1a30
Jan  4 19:32:55 toaster kernel: [    0.000000] nvram: NR partition at 0x1b30
Jan  4 19:32:55 toaster kernel: [    0.000000] Top of RAM: 0x60000000, Total RAM: 0x60000000
Jan  4 19:32:55 toaster kernel: [    0.000000] Memory hole size: 0MB
Jan  4 19:32:55 toaster kernel: [    0.000000] Zone ranges:
Jan  4 19:32:55 toaster kernel: [    0.000000]   DMA      [mem 0x00000000-0x2fffffff]
Jan  4 19:32:55 toaster kernel: [    0.000000]   Normal   empty
Jan  4 19:32:55 toaster kernel: [    0.000000]   HighMem  [mem 0x30000000-0x5fffffff]
Jan  4 19:32:55 toaster kernel: [    0.000000] Movable zone start for each node
Jan  4 19:32:55 toaster kernel: [    0.000000] Early memory node ranges
Jan  4 19:32:55 toaster kernel: [    0.000000]   node   0: [mem 0x00000000-0x5fffffff]
Jan  4 19:32:55 toaster kernel: [    0.000000] On node 0 totalpages: 393216
Jan  4 19:32:55 toaster kernel: [    0.000000] free_area_init_node: node 0, pgdat c072b1ec, node_mem_map c08b3000
Jan  4 19:32:55 toaster kernel: [    0.000000]   DMA zone: 1536 pages used for memmap
Jan  4 19:32:55 toaster kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  4 19:32:55 toaster kernel: [    0.000000]   DMA zone: 196608 pages, LIFO batch:31
Jan  4 19:32:55 toaster kernel: [    0.000000]   HighMem zone: 1536 pages used for memmap
Jan  4 19:32:55 toaster kernel: [    0.000000]   HighMem zone: 196608 pages, LIFO batch:31
Jan  4 19:32:55 toaster kernel: [    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
Jan  4 19:32:55 toaster kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan  4 19:32:55 toaster kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 391680
Jan  4 19:32:55 toaster kernel: [    0.000000] Kernel command line: root=UUID=11758325-78b3-4cc0-9cb2-d0cd860c4e5d ro 
Jan  4 19:32:55 toaster kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  4 19:32:55 toaster kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  4 19:32:55 toaster kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  4 19:32:55 toaster kernel: [    0.000000] Sorting __ex_table...
Jan  4 19:32:55 toaster kernel: [    0.000000] Memory: 1532512K/1572864K available (5184K kernel code, 420K rwdata, 1428K rodata, 404K init, 1403K bss, 40352K reserved, 786432K highmem)
Jan  4 19:32:55 toaster kernel: [    0.000000] Kernel virtual memory layout:
Jan  4 19:32:55 toaster kernel: [    0.000000]   * 0xfffcf000..0xfffff000  : fixmap
Jan  4 19:32:55 toaster kernel: [    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
Jan  4 19:32:55 toaster kernel: [    0.000000]   * 0xfdd66000..0xff800000  : early ioremap
Jan  4 19:32:55 toaster kernel: [    0.000000]   * 0xf1000000..0xfdd66000  : vmalloc & ioremap
Jan  4 19:32:55 toaster kernel: [    0.000000] NR_IRQS:512 nr_irqs:512 16
Jan  4 19:32:55 toaster kernel: [    0.000000] mpic: Resetting
Jan  4 19:32:55 toaster kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 1 CPUs
Jan  4 19:32:55 toaster kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Jan  4 19:32:55 toaster kernel: [    0.000000] mpic: Initializing for 64 sources
Jan  4 19:32:55 toaster kernel: [    0.000000] GMT Delta read from XPRAM: -240 minutes, DST: on
Jan  4 19:32:55 toaster kernel: [    0.000000] time_init: decrementer frequency = 24.907667 MHz
Jan  4 19:32:55 toaster kernel: [    0.000000] time_init: processor frequency   = 1000.000000 MHz
Jan  4 19:32:55 toaster kernel: [    0.000015] clocksource: timebase mult[2825f5b5] shift[24] registered
Jan  4 19:32:55 toaster kernel: [    0.000437] clockevent: decrementer mult[660594f] shift[32] cpu[0]
Jan  4 19:32:55 toaster kernel: [    0.000677] Console: colour dummy device 80x25
Jan  4 19:32:55 toaster kernel: [    0.001070] console [tty0] enabled
Jan  4 19:32:55 toaster kernel: [    0.001447] bootconsole [udbg0] disabled
Jan  4 19:32:55 toaster kernel: [    0.001880] pmac_zilog: i2c-modem detected, id: 1
Jan  4 19:32:55 toaster kernel: [    0.002168] pid_max: default: 32768 minimum: 301
Jan  4 19:32:55 toaster kernel: [    0.002266] Security Framework initialized
Jan  4 19:32:55 toaster kernel: [    0.002349] AppArmor: AppArmor disabled by boot time parameter
Jan  4 19:32:55 toaster kernel: [    0.002362] Yama: disabled by default; enable with sysctl kernel.yama.*
Jan  4 19:32:55 toaster kernel: [    0.002427] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  4 19:32:55 toaster kernel: [    0.002443] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  4 19:32:55 toaster kernel: [    0.003190] Initializing cgroup subsys memory
Jan  4 19:32:55 toaster kernel: [    0.003225] Initializing cgroup subsys devices
Jan  4 19:32:55 toaster kernel: [    0.003257] Initializing cgroup subsys freezer
Jan  4 19:32:55 toaster kernel: [    0.003275] Initializing cgroup subsys net_cls
Jan  4 19:32:55 toaster kernel: [    0.003304] Initializing cgroup subsys blkio
Jan  4 19:32:55 toaster kernel: [    0.003325] Initializing cgroup subsys perf_event
Jan  4 19:32:55 toaster kernel: [    0.003339] Initializing cgroup subsys net_prio
Jan  4 19:32:55 toaster kernel: [    0.003396] ftrace: allocating 17986 entries in 53 pages
Jan  4 19:32:55 toaster kernel: [    0.025344] MPC7450 family performance monitor hardware support registered
Jan  4 19:32:55 toaster kernel: [    0.029398] devtmpfs: initialized
Jan  4 19:32:55 toaster kernel: [    0.030752] device-tree: Duplicate name in PowerPC,G4@0, renamed to "l2-cache#1"
Jan  4 19:32:55 toaster kernel: [    0.030810] device-tree: Duplicate name in l2-cache#1, renamed to "l2-cache#1"
Jan  4 19:32:55 toaster kernel: [    0.033664] NET: Registered protocol family 16
Jan  4 19:32:55 toaster kernel: [    0.034797] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Jan  4 19:32:55 toaster kernel: [    0.034830]  channel 0 bus <multibus>
Jan  4 19:32:55 toaster kernel: [    0.034842]  channel 1 bus <multibus>
Jan  4 19:32:55 toaster kernel: [    0.034899] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Jan  4 19:32:55 toaster kernel: [    0.034916]  channel 0 bus <multibus>
Jan  4 19:32:55 toaster kernel: [    0.034950] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
Jan  4 19:32:55 toaster kernel: [    0.034967]  channel 1 bus <multibus>
Jan  4 19:32:55 toaster kernel: [    0.034979]  channel 2 bus <multibus>
Jan  4 19:32:55 toaster kernel: [    0.035381] PCI: Probing PCI hardware
Jan  4 19:32:55 toaster kernel: [    0.035520] PCI host bridge to bus 0000:00
Jan  4 19:32:55 toaster kernel: [    0.035544] pci_bus 0000:00: root bus resource [io  0x802000-0x1001fff] (bus address [0x0000-0x7fffff])
Jan  4 19:32:55 toaster kernel: [    0.035567] pci_bus 0000:00: root bus resource [mem 0xf1000000-0xf1ffffff]
Jan  4 19:32:55 toaster kernel: [    0.035583] pci_bus 0000:00: root bus resource [mem 0x90000000-0x9fffffff]
Jan  4 19:32:55 toaster kernel: [    0.035601] pci_bus 0000:00: root bus resource [bus 00-ff]
Jan  4 19:32:55 toaster dhclient: Internet Systems Consortium DHCP Client 4.3.1
Jan  4 19:32:55 toaster ifup[429]: Internet Systems Consortium DHCP Client 4.3.1
Jan  4 19:32:55 toaster dhclient: Copyright 2004-2014 Internet Systems Consortium.
Jan  4 19:32:55 toaster ifup[429]: Copyright 2004-2014 Internet Systems Consortium.
Jan  4 19:32:55 toaster dhclient: All rights reserved.
Jan  4 19:32:55 toaster dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  4 19:32:55 toaster dhclient: 
Jan  4 19:32:55 toaster ifup[429]: All rights reserved.
Jan  4 19:32:55 toaster ifup[429]: For info, please visit https://www.isc.org/software/dhcp/
Jan  4 19:32:55 toaster rpcbind[430]: Starting rpcbind daemon....
Jan  4 19:32:55 toaster systemd[1]: Started LSB: RPC portmapper replacement.
Jan  4 19:32:55 toaster systemd[1]: Starting RPC Port Mapper.
Jan  4 19:32:55 toaster systemd[1]: Reached target RPC Port Mapper.
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: NFS support files common to client and server...
Jan  4 19:32:55 toaster dhclient: Listening on LPF/eth0/00:30:65:c1:28:32
Jan  4 19:32:55 toaster dhclient: Sending on   LPF/eth0/00:30:65:c1:28:32
Jan  4 19:32:55 toaster dhclient: Sending on   Socket/fallback
Jan  4 19:32:55 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  4 19:32:55 toaster ifup[429]: Listening on LPF/eth0/00:30:65:c1:28:32
Jan  4 19:32:55 toaster ifup[429]: Sending on   LPF/eth0/00:30:65:c1:28:32
Jan  4 19:32:55 toaster ifup[429]: Sending on   Socket/fallback
Jan  4 19:32:55 toaster ifup[429]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  4 19:32:55 toaster console-setup[335]: Setting up console font and keymap...done.
Jan  4 19:32:55 toaster systemd[1]: Started LSB: Set console font and keymap.
Jan  4 19:32:55 toaster rpc.statd[458]: Version 1.2.8 starting
Jan  4 19:32:55 toaster sm-notify[459]: Version 1.2.8 starting
Jan  4 19:32:55 toaster rpc.statd[458]: Failed to read /var/lib/nfs/state: Success
Jan  4 19:32:55 toaster rpc.statd[458]: Initializing NSM state
Jan  4 19:32:55 toaster nfs-common[449]: Starting NFS common utilities: statd idmapd.
Jan  4 19:32:55 toaster systemd[1]: Started LSB: NFS support files common to client and server.
Jan  4 19:32:55 toaster systemd[1]: Starting System Initialization.
Jan  4 19:32:55 toaster systemd[1]: Reached target System Initialization.
Jan  4 19:32:55 toaster systemd[1]: Starting Avahi mDNS/DNS-SD Stack Activation Socket.
Jan  4 19:32:55 toaster systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Jan  4 19:32:55 toaster systemd[1]: Starting D-Bus System Message Bus Socket.
Jan  4 19:32:55 toaster systemd[1]: Listening on D-Bus System Message Bus Socket.
Jan  4 19:32:55 toaster systemd[1]: Starting Daily Cleanup of Temporary Directories.
Jan  4 19:32:55 toaster systemd[1]: Started Daily Cleanup of Temporary Directories.
Jan  4 19:32:55 toaster systemd[1]: Starting Timers.
Jan  4 19:32:55 toaster systemd[1]: Reached target Timers.
Jan  4 19:32:55 toaster systemd[1]: Starting CUPS Printing Service Sockets.
Jan  4 19:32:55 toaster systemd[1]: Listening on CUPS Printing Service Sockets.
Jan  4 19:32:55 toaster systemd[1]: Starting Sockets.
Jan  4 19:32:55 toaster systemd[1]: Reached target Sockets.
Jan  4 19:32:55 toaster systemd[1]: Starting CUPS Printer Service Spool.
Jan  4 19:32:55 toaster systemd[1]: Started CUPS Printer Service Spool.
Jan  4 19:32:55 toaster systemd[1]: Starting Paths.
Jan  4 19:32:55 toaster systemd[1]: Reached target Paths.
Jan  4 19:32:55 toaster systemd[1]: Starting Basic System.
Jan  4 19:32:55 toaster systemd[1]: Reached target Basic System.
Jan  4 19:32:55 toaster systemd[1]: Starting Deferred execution scheduler...
Jan  4 19:32:55 toaster systemd[1]: Started Deferred execution scheduler.
Jan  4 19:32:55 toaster systemd[1]: Starting OpenBSD Secure Shell server...
Jan  4 19:32:55 toaster systemd[1]: Started OpenBSD Secure Shell server.
Jan  4 19:32:55 toaster systemd[1]: Starting Regular background program processing daemon...
Jan  4 19:32:55 toaster cron[475]: (CRON) INFO (pidfile fd = 3)
Jan  4 19:32:55 toaster systemd[1]: Started Regular background program processing daemon.
Jan  4 19:32:55 toaster systemd[1]: Starting /etc/rc.local Compatibility...
Jan  4 19:32:55 toaster systemd[1]: Started getty on tty2-tty6 if dbus and logind are not available.
Jan  4 19:32:55 toaster systemd[1]: Starting Login Service...
Jan  4 19:32:55 toaster kernel: [    0.035619] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to ff
Jan  4 19:32:55 toaster kernel: [    0.035663] pci 0000:00:0b.0: [106b:0020] type 00 class 0x060000
Jan  4 19:32:55 toaster kernel: [    0.035888] pci 0000:00:10.0: [1002:5157] type 00 class 0x030000
Jan  4 19:32:55 toaster kernel: [    0.035914] pci 0000:00:10.0: reg 0x10: [mem 0x98000000-0x9fffffff pref]
Jan  4 19:32:55 toaster kernel: [    0.035926] pci 0000:00:10.0: reg 0x14: [io  0x802400-0x8024ff]
Jan  4 19:32:55 toaster kernel: [    0.035937] pci 0000:00:10.0: reg 0x18: [mem 0x90000000-0x9000ffff]
Jan  4 19:32:55 toaster kernel: [    0.035965] pci 0000:00:10.0: reg 0x30: [mem 0x90020000-0x9003ffff pref]
Jan  4 19:32:55 toaster kernel: [    0.036005] pci 0000:00:10.0: supports D1 D2
Jan  4 19:32:55 toaster kernel: [    0.036181] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 00
Jan  4 19:32:55 toaster kernel: [    0.036309] PCI host bridge to bus 0001:10
Jan  4 19:32:55 toaster kernel: [    0.036327] pci_bus 0001:10: root bus resource [io  0x0000-0x7fffff]
Jan  4 19:32:55 toaster kernel: [    0.036343] pci_bus 0001:10: root bus resource [mem 0xf3000000-0xf3ffffff]
Jan  4 19:32:55 toaster kernel: [    0.036359] pci_bus 0001:10: root bus resource [mem 0x80000000-0x8fffffff]
Jan  4 19:32:55 toaster kernel: [    0.036375] pci_bus 0001:10: root bus resource [bus 10-ff]
Jan  4 19:32:55 toaster kernel: [    0.036391] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to ff
Jan  4 19:32:55 toaster kernel: [    0.036421] pci 0001:10:0b.0: [106b:001f] type 00 class 0x060000
Jan  4 19:32:55 toaster kernel: [    0.036601] pci 0001:10:17.0: [106b:0022] type 00 class 0xff0000
Jan  4 19:32:55 toaster kernel: [    0.036618] pci 0001:10:17.0: reg 0x10: [mem 0x80000000-0x8007ffff]
Jan  4 19:32:55 toaster kernel: [    0.036794] pci 0001:10:18.0: [106b:0019] type 00 class 0x0c0310
Jan  4 19:32:55 toaster kernel: [    0.036811] pci 0001:10:18.0: reg 0x10: [mem 0x80082000-0x80082fff]
Jan  4 19:32:55 toaster kernel: [    0.036974] pci 0001:10:19.0: [106b:0019] type 00 class 0x0c0310
Jan  4 19:32:55 toaster kernel: [    0.036990] pci 0001:10:19.0: reg 0x10: [mem 0x80081000-0x80081fff]
Jan  4 19:32:55 toaster kernel: [    0.037189] pci 0001:10:1a.0: [104c:8020] type 00 class 0x0c0010
Jan  4 19:32:55 toaster kernel: [    0.037210] pci 0001:10:1a.0: reg 0x10: [mem 0x80080000-0x800807ff]
Jan  4 19:32:55 toaster kernel: [    0.037221] pci 0001:10:1a.0: reg 0x14: [mem 0x80084000-0x80087fff]
Jan  4 19:32:55 toaster kernel: [    0.037280] pci 0001:10:1a.0: supports D2
Jan  4 19:32:55 toaster kernel: [    0.037286] pci 0001:10:1a.0: PME# supported from D2 D3hot
Jan  4 19:32:55 toaster kernel: [    0.037498] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to 10
Jan  4 19:32:55 toaster kernel: [    0.037625] PCI host bridge to bus 0002:20
Jan  4 19:32:55 toaster kernel: [    0.037645] pci_bus 0002:20: root bus resource [io  0xff7fe000-0xffffdfff] (bus address [0x0000-0x7fffff])
Jan  4 19:32:55 toaster kernel: [    0.037669] pci_bus 0002:20: root bus resource [mem 0xf5000000-0xf5ffffff]
Jan  4 19:32:55 toaster kernel: [    0.037685] pci_bus 0002:20: root bus resource [bus 20-ff]
Jan  4 19:32:55 toaster kernel: [    0.037701] pci_bus 0002:20: busn_res: [bus 20-ff] end is updated to ff
Jan  4 19:32:55 toaster kernel: [    0.037727] pci 0002:20:0b.0: [106b:001e] type 00 class 0x060000
Jan  4 19:32:55 toaster kernel: [    0.037893] pci 0002:20:0f.0: [106b:0021] type 00 class 0x020000
Jan  4 19:32:55 toaster kernel: [    0.037909] pci 0002:20:0f.0: reg 0x10: [mem 0xf5200000-0xf53fffff]
Jan  4 19:32:55 toaster kernel: [    0.037945] pci 0002:20:0f.0: reg 0x30: [mem 0xf5000000-0xf50fffff pref]
Jan  4 19:32:55 toaster kernel: [    0.038113] pci_bus 0002:20: busn_res: [bus 20-ff] end is updated to 20
Jan  4 19:32:55 toaster kernel: [    0.038176] PCI 0000:00 Cannot reserve Legacy IO [io  0x802000-0x802fff]
Jan  4 19:32:55 toaster kernel: [    0.038194] pci_bus 0000:00: resource 4 [io  0x802000-0x1001fff]
Jan  4 19:32:55 toaster kernel: [    0.038201] pci_bus 0000:00: resource 5 [mem 0xf1000000-0xf1ffffff]
Jan  4 19:32:55 toaster kernel: [    0.038207] pci_bus 0000:00: resource 6 [mem 0x90000000-0x9fffffff]
Jan  4 19:32:55 toaster kernel: [    0.038216] pci_bus 0001:10: resource 4 [io  0x0000-0x7fffff]
Jan  4 19:32:55 toaster kernel: [    0.038223] pci_bus 0001:10: resource 5 [mem 0xf3000000-0xf3ffffff]
Jan  4 19:32:55 toaster kernel: [    0.038229] pci_bus 0001:10: resource 6 [mem 0x80000000-0x8fffffff]
Jan  4 19:32:55 toaster kernel: [    0.038237] pci_bus 0002:20: resource 4 [io  0xff7fe000-0xffffdfff]
Jan  4 19:32:55 toaster kernel: [    0.038244] pci_bus 0002:20: resource 5 [mem 0xf5000000-0xf5ffffff]
Jan  4 19:32:55 toaster kernel: [    0.041651] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
Jan  4 19:32:55 toaster kernel: [    0.041685] vgaarb: loaded
Jan  4 19:32:55 toaster kernel: [    0.041694] vgaarb: bridge control possible 0000:00:10.0
Jan  4 19:32:55 toaster kernel: [    0.041974] SCSI subsystem initialized
Jan  4 19:32:55 toaster kernel: [    0.042103] libata version 3.00 loaded.
Jan  4 19:32:55 toaster kernel: [    0.042653] Switched to clocksource timebase
Jan  4 19:32:55 toaster kernel: [    0.055930] NET: Registered protocol family 2
Jan  4 19:32:55 toaster kernel: [    0.056660] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jan  4 19:32:55 toaster kernel: [    0.056749] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
Jan  4 19:32:55 toaster kernel: [    0.056829] TCP: Hash tables configured (established 8192 bind 8192)
Jan  4 19:32:55 toaster kernel: [    0.057012] TCP: reno registered
Jan  4 19:32:55 toaster kernel: [    0.057028] UDP hash table entries: 512 (order: 1, 8192 bytes)
Jan  4 19:32:55 toaster kernel: [    0.057059] UDP-Lite hash table entries: 512 (order: 1, 8192 bytes)
Jan  4 19:32:55 toaster kernel: [    0.057224] NET: Registered protocol family 1
Jan  4 19:32:55 toaster kernel: [    0.057333] pci 0001:10:18.0: enabling device (0000 -> 0002)
Jan  4 19:32:55 toaster kernel: [    0.110716] pci 0001:10:19.0: enabling device (0000 -> 0002)
Jan  4 19:32:55 toaster kernel: [    0.166684] PCI: CLS mismatch (32 != 1020), using 32 bytes
Jan  4 19:32:55 toaster kernel: [    0.166888] Unpacking initramfs...
Jan  4 19:32:55 toaster kernel: [    0.823460] Freeing initrd memory: 13732K (c1600000 - c2369000)
Jan  4 19:32:55 toaster kernel: [    0.823984] Thermal assist unit not available
Jan  4 19:32:55 toaster kernel: [    0.824866] futex hash table entries: 256 (order: -1, 3072 bytes)
Jan  4 19:32:55 toaster kernel: [    0.824937] audit: initializing netlink subsys (disabled)
Jan  4 19:32:55 toaster kernel: [    0.825024] audit: type=2000 audit(1451968363.812:1): initialized
Jan  4 19:32:55 toaster kernel: [    0.825894] zbud: loaded
Jan  4 19:32:55 toaster kernel: [    0.826098] VFS: Disk quotas dquot_6.5.2
Jan  4 19:32:55 toaster kernel: [    0.826143] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  4 19:32:55 toaster kernel: [    0.826247] msgmni has been set to 1486
Jan  4 19:32:55 toaster kernel: [    0.827324] alg: No test for stdrng (krng)
Jan  4 19:32:55 toaster kernel: [    0.827419] bounce: pool size: 64 pages
Jan  4 19:32:55 toaster kernel: [    0.827476] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan  4 19:32:55 toaster kernel: [    0.827629] io scheduler noop registered
Jan  4 19:32:55 toaster kernel: [    0.827649] io scheduler deadline registered
Jan  4 19:32:55 toaster kernel: [    0.827747] io scheduler cfq registered (default)
Jan  4 19:32:55 toaster kernel: [    0.828417] Using unsupported 1680x1050 ATY,BlueStone_A at 9c008000, depth=8, pitch=1792
Jan  4 19:32:55 toaster kernel: [    0.863322] Console: switching to colour frame buffer device 210x65
Jan  4 19:32:55 toaster kernel: [    0.897509] fb0: Open Firmware frame buffer device on /pci@f0000000/ATY,BlueStoneParent@10/ATY,BlueStone_A
Jan  4 19:32:55 toaster kernel: [    0.897850] Using unsupported 640x480 ATY,BlueStone_B at 99008000, depth=8, pitch=768
Jan  4 19:32:55 toaster kernel: [    0.898107] checking generic (9c008000 1cb600) vs hw (99008000 5a000)
Jan  4 19:32:55 toaster kernel: [    0.898268] fb1: Open Firmware frame buffer device on /pci@f0000000/ATY,BlueStoneParent@10/ATY,BlueStone_B
Jan  4 19:32:55 toaster kernel: [    0.898740] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
Jan  4 19:32:55 toaster kernel: [    0.899774] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Jan  4 19:32:55 toaster kernel: [    0.900035] Serial: MPC52xx PSC UART driver
Jan  4 19:32:55 toaster kernel: [    0.900217] Generic non-volatile memory driver v1.1
Jan  4 19:32:55 toaster kernel: [    0.900459] Linux agpgart interface v0.103
Jan  4 19:32:55 toaster kernel: [    0.900628] agpgart-uninorth 0000:00:0b.0: Apple UniNorth chipset
Jan  4 19:32:55 toaster kernel: [    0.903153] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
Jan  4 19:32:55 toaster kernel: [    0.903466] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
Jan  4 19:32:55 toaster kernel: [    0.903856] MacIO PCI driver attached to Keylargo chipset
Jan  4 19:32:55 toaster kernel: [    0.905456] 0.00013020:ch-a: ttyPZ0 at MMIO 0x80013020 (irq = 22, base_baud = 230400) is a Z85c30 ESCC - Internal modem
Jan  4 19:32:55 toaster kernel: [    0.906118] 0.00013000:ch-b: ttyPZ1 at MMIO 0x80013000 (irq = 50, base_baud = 230400) is a Z85c30 ESCC - Serial port
Jan  4 19:32:55 toaster kernel: [    0.907347] adb: starting probe task...
Jan  4 19:32:55 toaster kernel: [    0.907476] adb: finished probe task...
Jan  4 19:32:55 toaster kernel: [    1.926686] pata-macio 0.0001f000:ata-4: Activating pata-macio chipset KeyLargo ATA-4, Apple bus ID 2
Jan  4 19:32:55 toaster kernel: [    1.927598] scsi0 : pata_macio
Jan  4 19:32:55 toaster kernel: [    1.927891] ata1: PATA max UDMA/66 irq 19
Jan  4 19:32:55 toaster kernel: [    2.100459] ata1.00: ATA-8: OWC Mercury Electra 3G SSD, 603ABBF0, max UDMA/133
Jan  4 19:32:55 toaster kernel: [    2.100684] ata1.00: 117231408 sectors, multi 1: LBA48 NCQ (depth 0/32)
Jan  4 19:32:55 toaster kernel: [    2.100895] ata1.01: ATAPI: MATSHITADVD-ROM SR-8186, F113, max UDMA/33
Jan  4 19:32:55 toaster kernel: [    2.108383] ata1.00: configured for UDMA/66
Jan  4 19:32:55 toaster kernel: [    2.122990] ata1.01: configured for UDMA/33
Jan  4 19:32:55 toaster kernel: [    2.124244] scsi 0:0:0:0: Direct-Access     ATA      OWC Mercury Elec BBF0 PQ: 0 ANSI: 5
Jan  4 19:32:55 toaster kernel: [    2.125951] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8186  F113 PQ: 0 ANSI: 5
Jan  4 19:32:55 toaster kernel: [    2.946645] pata-macio 0.00020000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 0
Jan  4 19:32:55 toaster kernel: [    2.947531] scsi1 : pata_macio
Jan  4 19:32:55 toaster kernel: [    2.947794] ata2: PATA max MWDMA2 irq 20
Jan  4 19:32:55 toaster kernel: [    3.966664] pata-macio 0.00021000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 1
Jan  4 19:32:55 toaster kernel: [    3.967537] scsi2 : pata_macio
Jan  4 19:32:55 toaster kernel: [    3.967798] ata3: PATA max MWDMA2 irq 21
Jan  4 19:32:55 toaster kernel: [    3.968238] mousedev: PS/2 mouse device common for all mice
Jan  4 19:32:55 toaster kernel: [    3.968912] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
Jan  4 19:32:55 toaster kernel: [    3.969250] PowerMac i2c bus pmu 2 registered
Jan  4 19:32:55 toaster kernel: [    3.969462] PowerMac i2c bus pmu 1 registered
Jan  4 19:32:55 toaster kernel: [    3.969667] PowerMac i2c bus mac-io 0 registered
Jan  4 19:32:55 toaster kernel: [    3.969817] i2c i2c-2: No i2c address for /pci@f2000000/mac-io@17/i2c@18000/i2c-modem
Jan  4 19:32:55 toaster cron[475]: (CRON) INFO (Running @reboot jobs)
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: handle special hotkeys of Apple computers...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: exim Mail Transport Agent...
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: Emulate mouse buttons and mouse wheel...
Jan  4 19:32:55 toaster systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Jan  4 19:32:55 toaster systemd[1]: Starting D-Bus System Message Bus...
Jan  4 19:32:55 toaster pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration.
Jan  4 19:32:55 toaster avahi-daemon[487]: Found user 'avahi' (UID 105) and group 'avahi' (GID 112).
Jan  4 19:32:55 toaster systemd[1]: Started D-Bus System Message Bus.
Jan  4 19:32:55 toaster avahi-daemon[487]: Successfully dropped root privileges.
Jan  4 19:32:55 toaster avahi-daemon[487]: avahi-daemon 0.6.31 starting up.
Jan  4 19:32:55 toaster pbbuttonsd[479]: Starting pbbuttonsd:ERROR: Can't attach card 'default': No such file or directory
Jan  4 19:32:55 toaster pbbuttonsd: ERROR: Can't attach card 'default': No such file or directory
Jan  4 19:32:55 toaster pbbuttonsd: ERROR: Can't open mixer device [/dev/mixer]. No such file or directory
Jan  4 19:32:55 toaster pbbuttonsd: INFO: Soundsystem requested: auto, detected: ALSA and at least activated: none.
Jan  4 19:32:55 toaster pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf.
Jan  4 19:32:55 toaster pbbuttonsd[479]: ERROR: Can't open mixer device [/dev/mixer]. No such file or directory
Jan  4 19:32:55 toaster pbbuttonsd[479]: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 19:32:55 toaster pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 19:32:55 toaster pbbuttonsd[479]: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 19:32:55 toaster pbbuttonsd[479]: .
Jan  4 19:32:55 toaster avahi-daemon[487]: Successfully called chroot().
Jan  4 19:32:55 toaster avahi-daemon[487]: Successfully dropped remaining capabilities.
Jan  4 19:32:55 toaster avahi-daemon[487]: No service file found in /etc/avahi/services.
Jan  4 19:32:55 toaster avahi-daemon[487]: Network interface enumeration completed.
Jan  4 19:32:55 toaster avahi-daemon[487]: Registering HINFO record with values 'PPC'/'LINUX'.
Jan  4 19:32:55 toaster avahi-daemon[487]: Server startup complete. Host name is toaster.local. Local service cookie is 3848221040.
Jan  4 19:32:55 toaster systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Jan  4 19:32:55 toaster systemd[1]: Starting LSB: SANE network scanner server...
Jan  4 19:32:55 toaster systemd[1]: Starting System Logging Service...
Jan  4 19:32:55 toaster systemd[1]: Starting CUPS Printing Service...
Jan  4 19:32:55 toaster saned[532]: saned disabled; edit /etc/default/saned.
Jan  4 19:32:55 toaster systemd[1]: Started CUPS Printing Service.
Jan  4 19:32:55 toaster systemd[1]: Starting Make remote CUPS printers available locally...
Jan  4 19:32:55 toaster pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' lauched but exitcode is not null
Jan  4 19:32:55 toaster kernel: [    3.970130] PowerMac i2c bus uni-n 1 registered
Jan  4 19:32:55 toaster kernel: [    3.970344] PowerMac i2c bus uni-n 0 registered
Jan  4 19:32:55 toaster kernel: [    3.979590] ledtrig-cpu: registered to indicate activity on CPUs
Jan  4 19:32:55 toaster kernel: [    3.988959] TCP: cubic registered
Jan  4 19:32:55 toaster kernel: [    3.998083] NET: Registered protocol family 10
Jan  4 19:32:55 toaster kernel: [    4.007715] mip6: Mobile IPv6
Jan  4 19:32:55 toaster kernel: [    4.016861] NET: Registered protocol family 17
Jan  4 19:32:55 toaster kernel: [    4.025983] mpls_gso: MPLS GSO support
Jan  4 19:32:55 toaster kernel: [    4.035537] registered taskstats version 1
Jan  4 19:32:55 toaster kernel: [    4.045188] input: PMU as /devices/virtual/input/input0
Jan  4 19:32:55 toaster kernel: [    4.054492] rtc-generic rtc-generic: setting system clock to 2016-01-05 00:32:47 UTC (1451953967)
Jan  4 19:32:55 toaster kernel: [    4.063795] PM: Hibernation image not present or could not be loaded.
Jan  4 19:32:55 toaster kernel: [    4.123510] Freeing unused kernel memory: 404K (c0679000 - c06de000)
Jan  4 19:32:55 toaster kernel: [    4.216353] random: systemd-udevd urandom read with 0 bits of entropy available
Jan  4 19:32:55 toaster kernel: [    4.293763] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
Jan  4 19:32:55 toaster kernel: [    4.303428] sr0: scsi3-mmc drive: 46x/46x cd/rw xa/form2 cdda tray
Jan  4 19:32:55 toaster kernel: [    4.312923] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  4 19:32:55 toaster kernel: [    4.351356] sungem.c:v1.0 David S. Miller <davem@redhat.com>
Jan  4 19:32:55 toaster kernel: [    4.368632] firewire_ohci 0001:10:1a.0: enabling device (0010 -> 0012)
Jan  4 19:32:55 toaster kernel: [    4.383717] sd 0:0:0:0: [sda] Write Protect is off
Jan  4 19:32:55 toaster kernel: [    4.393291] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  4 19:32:55 toaster kernel: [    4.408474] sr 0:0:1:0: Attached scsi CD-ROM sr0
Jan  4 19:32:55 toaster kernel: [    4.416890] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  4 19:32:55 toaster kernel: [    4.429760] usbcore: registered new interface driver usbfs
Jan  4 19:32:55 toaster kernel: [    4.441583] gem 0002:20:0f.0 eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:30:65:c1:28:32
Jan  4 19:32:55 toaster kernel: [    4.463452] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  4 19:32:55 toaster kernel: [    4.489187] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jan  4 19:32:55 toaster kernel: [    4.501756] usbcore: registered new interface driver hub
Jan  4 19:32:55 toaster kernel: [    4.511477] firewire_ohci 0001:10:1a.0: added OHCI v1.0 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
Jan  4 19:32:55 toaster kernel: [    4.543341]  sda: [mac] sda1 sda2 sda3 sda4 sda5
Jan  4 19:32:55 toaster kernel: [    4.565563] usbcore: registered new device driver usb
Jan  4 19:32:55 toaster kernel: [    4.585843] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  4 19:32:55 toaster kernel: [    4.598803] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  4 19:32:55 toaster kernel: [    4.624087] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  4 19:32:55 toaster kernel: [    4.639436] ehci-pci: EHCI PCI platform driver
Jan  4 19:32:55 toaster kernel: [    4.653908] ohci-pci: OHCI PCI platform driver
Jan  4 19:32:55 toaster kernel: [    4.664616] ohci-pci 0001:10:18.0: OHCI PCI host controller
Jan  4 19:32:55 toaster kernel: [    4.674172] ohci-pci 0001:10:18.0: new USB bus registered, assigned bus number 1
Jan  4 19:32:55 toaster kernel: [    4.683813] ohci-pci 0001:10:18.0: irq 27, io mem 0x80082000
Jan  4 19:32:55 toaster kernel: [    4.766234] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
Jan  4 19:32:55 toaster kernel: [    4.775676] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  4 19:32:55 toaster kernel: [    4.785061] usb usb1: Product: OHCI PCI host controller
Jan  4 19:32:55 toaster kernel: [    4.794298] usb usb1: Manufacturer: Linux 3.16.0-4-powerpc ohci_hcd
Jan  4 19:32:55 toaster kernel: [    4.803654] usb usb1: SerialNumber: 0001:10:18.0
Jan  4 19:32:55 toaster kernel: [    4.831444] hub 1-0:1.0: USB hub found
Jan  4 19:32:55 toaster kernel: [    4.841029] hub 1-0:1.0: 2 ports detected
Jan  4 19:32:55 toaster kernel: [    4.852614] ohci-pci 0001:10:19.0: OHCI PCI host controller
Jan  4 19:32:55 toaster kernel: [    4.862035] ohci-pci 0001:10:19.0: new USB bus registered, assigned bus number 2
Jan  4 19:32:55 toaster kernel: [    4.872052] ohci-pci 0001:10:19.0: irq 28, io mem 0x80081000
Jan  4 19:32:55 toaster kernel: [    4.954132] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jan  4 19:32:55 toaster kernel: [    4.963308] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  4 19:32:55 toaster kernel: [    4.972512] usb usb2: Product: OHCI PCI host controller
Jan  4 19:32:55 toaster kernel: [    4.981646] usb usb2: Manufacturer: Linux 3.16.0-4-powerpc ohci_hcd
Jan  4 19:32:55 toaster kernel: [    4.990815] usb usb2: SerialNumber: 0001:10:19.0
Jan  4 19:32:55 toaster kernel: [    5.000571] hub 2-0:1.0: USB hub found
Jan  4 19:32:55 toaster kernel: [    5.009502] hub 2-0:1.0: 2 ports detected
Jan  4 19:32:55 toaster kernel: [    5.018865] firewire_core 0001:10:1a.0: created device fw0: GUID 003065fffec12832, S400
Jan  4 19:32:55 toaster kernel: [    5.102898] PM: Starting manual resume from disk
Jan  4 19:32:55 toaster kernel: [    5.112012] PM: Hibernation image partition 8:4 present
Jan  4 19:32:55 toaster kernel: [    5.112018] PM: Looking for hibernation image.
Jan  4 19:32:55 toaster kernel: [    5.114019] PM: Image not found (code -22)
Jan  4 19:32:55 toaster kernel: [    5.114026] PM: Hibernation image not present or could not be loaded.
Jan  4 19:32:55 toaster kernel: [    5.262691] usb 1-1: new full-speed USB device number 2 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    5.333428] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Jan  4 19:32:55 toaster kernel: [    5.473753] usb 1-1: New USB device found, idVendor=05ac, idProduct=1101
Jan  4 19:32:55 toaster kernel: [    5.483513] usb 1-1: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Jan  4 19:32:55 toaster kernel: [    5.493142] usb 1-1: Product: Speakers
Jan  4 19:32:55 toaster kernel: [    5.502686] usb 1-1: Manufacturer: Apple Computer, Inc.
Jan  4 19:32:55 toaster kernel: [    5.512233] usb 1-1: SerialNumber: p4000
Jan  4 19:32:55 toaster kernel: [    5.702192] usb 1-2: new full-speed USB device number 3 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    5.907737] usb 1-2: New USB device found, idVendor=05ac, idProduct=9119
Jan  4 19:32:55 toaster kernel: [    5.917912] usb 1-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jan  4 19:32:55 toaster kernel: [    5.930374] hub 1-2:1.0: USB hub found
Jan  4 19:32:55 toaster kernel: [    5.941964] hub 1-2:1.0: 3 ports detected
Jan  4 19:32:55 toaster kernel: [    6.126678] usb 2-1: new full-speed USB device number 2 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    6.336722] usb 2-1: New USB device found, idVendor=05ac, idProduct=1002
Jan  4 19:32:55 toaster kernel: [    6.336727] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  4 19:32:55 toaster kernel: [    6.336730] usb 2-1: Product: Hub in Apple Extended USB Keyboard
Jan  4 19:32:55 toaster kernel: [    6.336734] usb 2-1: Manufacturer: Alps Electric
Jan  4 19:32:55 toaster kernel: [    6.338820] hub 2-1:1.0: USB hub found
Jan  4 19:32:55 toaster kernel: [    6.395046] hub 2-1:1.0: 3 ports detected
Jan  4 19:32:55 toaster kernel: [    6.557294] usb 1-2.3: new low-speed USB device number 4 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    6.693866] lp: driver loaded but no devices found
Jan  4 19:32:55 toaster kernel: [    6.695771] usb 1-2.3: New USB device found, idVendor=05ac, idProduct=9219
Jan  4 19:32:55 toaster kernel: [    6.695776] usb 1-2.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan  4 19:32:55 toaster kernel: [    6.695780] usb 1-2.3: Product: Studio Display
Jan  4 19:32:55 toaster kernel: [    6.806722] usb 2-1.1: new full-speed USB device number 3 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    6.829594] cfg80211: Calling CRDA to update world regulatory domain
Jan  4 19:32:55 toaster kernel: [    6.851366] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
Jan  4 19:32:55 toaster kernel: [    6.852560] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Jan  4 19:32:55 toaster kernel: [    6.852637] airport: Physical address 80030000
Jan  4 19:32:55 toaster kernel: [    7.209788] usb 2-1.1: New USB device found, idVendor=05ac, idProduct=0204
Jan  4 19:32:55 toaster kernel: [    7.209793] usb 2-1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan  4 19:32:55 toaster kernel: [    7.209797] usb 2-1.1: Product: Apple Extended USB Keyboard
Jan  4 19:32:55 toaster kernel: [    7.209801] usb 2-1.1: Manufacturer: Alps Electric
Jan  4 19:32:55 toaster kernel: [    7.334726] usb 2-1.3: new low-speed USB device number 4 using ohci-pci
Jan  4 19:32:55 toaster kernel: [    7.462714] usb 2-1.3: New USB device found, idVendor=045e, idProduct=0047
Jan  4 19:32:55 toaster kernel: [    7.472224] usb 2-1.3: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan  4 19:32:55 toaster kernel: [    7.481635] usb 2-1.3: Product: Microsoft 5-Button Mouse with IntelliEye(TM)
Jan  4 19:32:55 toaster kernel: [    7.491088] usb 2-1.3: Manufacturer: Microsoft
Jan  4 19:32:55 toaster kernel: [    7.534757] random: nonblocking pool is initialized
Jan  4 19:32:55 toaster kernel: [    7.934725] appledisplay: Apple Cinema Display connected
Jan  4 19:32:55 toaster kernel: [    8.055389] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
Jan  4 19:32:55 toaster kernel: [    8.065120] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
Jan  4 19:32:55 toaster kernel: [    8.074557] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
Jan  4 19:32:55 toaster kernel: [    8.105973] usbcore: registered new interface driver appledisplay
Jan  4 19:32:55 toaster kernel: [    8.232779] [drm] Initialized drm 1.1.0 20060810
Jan  4 19:32:55 toaster kernel: [    8.254157] airport 0.00030000:radio: firmware: failed to load agere_sta_fw.bin (-2)
Jan  4 19:32:55 toaster kernel: [    8.273371] hidraw: raw HID events driver (C) Jiri Kosina
Jan  4 19:32:55 toaster kernel: [    8.379108] airport 0.00030000:radio: firmware: failed to load agere_sta_fw.bin (-2)
Jan  4 19:32:55 toaster kernel: [    8.388710] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
Jan  4 19:32:55 toaster kernel: [    8.398105] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
Jan  4 19:32:55 toaster kernel: [    8.407329] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
Jan  4 19:32:55 toaster kernel: [    8.416549] airport 0.00030000:radio: Ad-hoc demo mode supported
Jan  4 19:32:55 toaster kernel: [    8.425681] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
Jan  4 19:32:55 toaster kernel: [    8.434852] airport 0.00030000:radio: WEP supported, 104-bit key
Jan  4 19:32:55 toaster kernel: [    8.588862] usbcore: registered new interface driver usbhid
Jan  4 19:32:55 toaster kernel: [    8.598157] usbhid: USB HID core driver
Jan  4 19:32:55 toaster kernel: [    9.186716] input: Apple Computer, Inc. Speakers as /devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1:1.2/0003:05AC:1101.0001/input/input1
Jan  4 19:32:55 toaster kernel: [    9.294693] hid-generic 0003:05AC:1101.0001: input,hidraw0: USB HID v1.00 Device [Apple Computer, Inc. Speakers] on usb-0001:10:18.0-1/input2
Jan  4 19:32:55 toaster kernel: [    9.341589] [drm] radeon kernel modesetting enabled.
Jan  4 19:32:55 toaster kernel: [    9.341736] checking generic (9c008000 1cb600) vs hw (98000000 8000000)
Jan  4 19:32:55 toaster kernel: [    9.341738] fb: switching to radeondrmfb from OFfb ATY,BlueSt
Jan  4 19:32:55 toaster kernel: [    9.356423] input: Alps Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:05AC:0204.0002/input/input2
Jan  4 19:32:55 toaster kernel: [    9.359108] hid-generic 0003:05AC:0204.0002: input,hidraw1: USB HID v1.10 Keyboard [Alps Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input0
Jan  4 19:32:55 toaster kernel: [    9.363045] input: Alps Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:05AC:0204.0003/input/input3
Jan  4 19:32:55 toaster kernel: [    9.415500] Console: switching to colour dummy device 80x25
Jan  4 19:32:55 toaster kernel: [    9.415723] checking generic (99008000 5a000) vs hw (98000000 8000000)
Jan  4 19:32:55 toaster kernel: [    9.415730] fb: switching to radeondrmfb from OFfb ATY,BlueSt
Jan  4 19:32:55 toaster kernel: [    9.416708] radeon 0000:00:10.0: enabling device (0086 -> 0087)
Jan  4 19:32:55 toaster kernel: [    9.417769] [drm] initializing kernel modesetting (RV200 0x1002:0x5157 0x1002:0x5157).
Jan  4 19:32:55 toaster kernel: [    9.417814] [drm] register mmio base: 0x90000000
Jan  4 19:32:55 toaster kernel: [    9.417826] [drm] register mmio size: 65536
Jan  4 19:32:55 toaster kernel: [    9.417940] radeon 0000:00:10.0: Invalid ROM contents
Jan  4 19:32:55 toaster kernel: [    9.502823] [drm] Not an x86 BIOS ROM, not using.
Jan  4 19:32:55 toaster kernel: [    9.502869] [drm] Using device-tree clock info
Jan  4 19:32:55 toaster kernel: [    9.502922] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 2x mode
Jan  4 19:32:55 toaster kernel: [    9.502943] radeon 0000:00:10.0: putting AGP V2 device into 2x mode
Jan  4 19:32:55 toaster kernel: [    9.502986] radeon 0000:00:10.0: GTT: 256M 0x00000000 - 0x0FFFFFFF
Jan  4 19:32:55 toaster kernel: [    9.503009] radeon 0000:00:10.0: VRAM: 128M 0x0000000098000000 - 0x000000009FFFFFFF (32M used)
Jan  4 19:32:55 toaster kernel: [    9.503075] [drm] Detected VRAM RAM=128M, BAR=128M
Jan  4 19:32:55 toaster kernel: [    9.503087] [drm] RAM width 128bits DDR
Jan  4 19:32:55 toaster kernel: [    9.503669] hid-generic 0003:05AC:0204.0003: input,hidraw2: USB HID v1.10 Device [Alps Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input1
Jan  4 19:32:55 toaster kernel: [    9.508110] [TTM] Zone  kernel: Available graphics memory: 380618 kiB
Jan  4 19:32:55 toaster kernel: [    9.508139] [TTM] Zone highmem: Available graphics memory: 773834 kiB
Jan  4 19:32:55 toaster kernel: [    9.508152] [TTM] Initializing pool allocator
Jan  4 19:32:55 toaster kernel: [    9.508255] [drm] radeon: 32M of VRAM memory ready
Jan  4 19:32:55 toaster kernel: [    9.508270] [drm] radeon: 256M of GTT memory ready.
Jan  4 19:32:55 toaster kernel: [    9.509029] radeon 0000:00:10.0: WB disabled
Jan  4 19:32:55 toaster kernel: [    9.509055] radeon 0000:00:10.0: fence driver on ring 0 use gpu addr 0x0000000000000000 and cpu addr 0xf269e000
Jan  4 19:32:55 toaster kernel: [    9.509078] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan  4 19:32:55 toaster kernel: [    9.509091] [drm] Driver supports precise vblank timestamp query.
Jan  4 19:32:55 toaster kernel: [    9.509142] [drm] radeon: irq initialized.
Jan  4 19:32:55 toaster kernel: [    9.509187] [drm] Loading R100 Microcode
Jan  4 19:32:55 toaster kernel: [    9.509262] radeon 0000:00:10.0: firmware: failed to load radeon/R100_cp.bin (-2)
Jan  4 19:32:55 toaster kernel: [    9.509285] [drm:r100_cp_init] *ERROR* Failed to load firmware!
Jan  4 19:32:55 toaster kernel: [    9.509301] radeon 0000:00:10.0: failed initializing CP (-2).
Jan  4 19:32:55 toaster kernel: [    9.509315] radeon 0000:00:10.0: Disabling GPU acceleration
Jan  4 19:32:55 toaster kernel: [    9.509331] [drm] radeon: cp finalized
Jan  4 19:32:55 toaster kernel: [    9.509401] [drm] radeon: cp finalized
Jan  4 19:32:55 toaster kernel: [    9.509456] [TTM] Finalizing pool allocator
Jan  4 19:32:55 toaster kernel: [    9.514667] [TTM] Zone  kernel: Used memory at exit: 0 kiB
Jan  4 19:32:55 toaster kernel: [    9.514695] [TTM] Zone highmem: Used memory at exit: 0 kiB
Jan  4 19:32:55 toaster kernel: [    9.514709] [drm] radeon: ttm finalized
Jan  4 19:32:55 toaster kernel: [    9.514720] [drm] Forcing AGP to PCI mode
Jan  4 19:32:55 toaster kernel: [    9.514794] radeon 0000:00:10.0: Invalid ROM contents
Jan  4 19:32:55 toaster kernel: [    9.598524] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:045E:0047.0004/input/input4
Jan  4 19:32:55 toaster kernel: [    9.599327] hid-generic 0003:045E:0047.0004: input,hidraw3: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0001:10:19.0-1.3/input0
Jan  4 19:32:55 toaster kernel: [    9.680668] usb 1-1: Warning! Unlikely big volume range (=768), cval->res is probably wrong.
Jan  4 19:32:55 toaster kernel: [    9.680721] usb 1-1: [2] FU [PCM Playback Volume] ch = 2, val = -12288/0/16
Jan  4 19:32:55 toaster kernel: [    9.753609] usbcore: registered new interface driver snd-usb-audio
Jan  4 19:32:55 toaster kernel: [    9.852333] Adding 2439860k swap on /dev/sda4.  Priority:-1 extents:1 across:2439860k SSFS
Jan  4 19:32:55 toaster kernel: [    9.869384] [drm] Not an x86 BIOS ROM, not using.
Jan  4 19:32:55 toaster kernel: [    9.869448] [drm] Using device-tree clock info
Jan  4 19:32:55 toaster kernel: [    9.869479] radeon 0000:00:10.0: VRAM: 128M 0x0000000098000000 - 0x000000009FFFFFFF (32M used)
Jan  4 19:32:55 toaster kernel: [    9.869502] radeon 0000:00:10.0: GTT: 512M 0x0000000078000000 - 0x0000000097FFFFFF
Jan  4 19:32:55 toaster kernel: [    9.869529] [drm] Detected VRAM RAM=128M, BAR=128M
Jan  4 19:32:55 toaster kernel: [    9.869541] [drm] RAM width 128bits DDR
Jan  4 19:32:55 toaster kernel: [    9.874843] [TTM] Zone  kernel: Available graphics memory: 380618 kiB
Jan  4 19:32:55 toaster kernel: [    9.874870] [TTM] Zone highmem: Available graphics memory: 773834 kiB
Jan  4 19:32:55 toaster kernel: [    9.874883] [TTM] Initializing pool allocator
Jan  4 19:32:55 toaster kernel: [    9.874988] [drm] radeon: 32M of VRAM memory ready
Jan  4 19:32:55 toaster kernel: [    9.875002] [drm] radeon: 512M of GTT memory ready.
Jan  4 19:32:55 toaster kernel: [    9.875057] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jan  4 19:32:55 toaster kernel: [    9.884396] [drm] PCI GART of 512M enabled (table at 0x000000002EC00000).
Jan  4 19:32:55 toaster kernel: [    9.910772] radeon 0000:00:10.0: WB disabled
Jan  4 19:32:55 toaster kernel: [    9.910819] radeon 0000:00:10.0: fence driver on ring 0 use gpu addr 0x0000000078000000 and cpu addr 0xc1e55000
Jan  4 19:32:55 toaster kernel: [    9.910844] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan  4 19:32:55 toaster kernel: [    9.910857] [drm] Driver supports precise vblank timestamp query.
Jan  4 19:32:55 toaster kernel: [    9.910907] [drm] radeon: irq initialized.
Jan  4 19:32:55 toaster kernel: [    9.910921] [drm] Loading R100 Microcode
Jan  4 19:32:55 toaster kernel: [    9.910965] radeon 0000:00:10.0: firmware: failed to load radeon/R100_cp.bin (-2)
Jan  4 19:32:55 toaster kernel: [    9.910987] [drm:r100_cp_init] *ERROR* Failed to load firmware!
Jan  4 19:32:55 toaster kernel: [    9.911002] radeon 0000:00:10.0: failed initializing CP (-2).
Jan  4 19:32:55 toaster kernel: [    9.911017] radeon 0000:00:10.0: Disabling GPU acceleration
Jan  4 19:32:55 toaster kernel: [    9.911033] [drm] radeon: cp finalized
Jan  4 19:32:55 toaster kernel: [    9.930753] [drm] Connector Table: 1 (generic)
Jan  4 19:32:55 toaster kernel: [    9.930805] [drm] No TMDS info found in BIOS
Jan  4 19:32:55 toaster kernel: [    9.930823] [drm] No TV DAC info found in BIOS
Jan  4 19:32:55 toaster kernel: [    9.931574] [drm] Radeon Display Connectors
Jan  4 19:32:55 toaster kernel: [    9.931593] [drm] Connector 0:
Jan  4 19:32:55 toaster kernel: [    9.931603] [drm]   DVI-I-1
Jan  4 19:32:55 toaster kernel: [    9.931612] [drm]   HPD1
Jan  4 19:32:55 toaster kernel: [    9.931624] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jan  4 19:32:55 toaster kernel: [    9.931636] [drm]   Encoders:
Jan  4 19:32:55 toaster kernel: [    9.931647] [drm]     DFP1: INTERNAL_TMDS1
Jan  4 19:32:55 toaster kernel: [    9.931658] [drm]     CRT2: INTERNAL_DAC2
Jan  4 19:32:55 toaster kernel: [    9.931668] [drm] Connector 1:
Jan  4 19:32:55 toaster kernel: [    9.931677] [drm]   VGA-1
Jan  4 19:32:55 toaster kernel: [    9.931688] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Jan  4 19:32:55 toaster kernel: [    9.931700] [drm]   Encoders:
Jan  4 19:32:55 toaster kernel: [    9.931709] [drm]     CRT1: INTERNAL_DAC1
Jan  4 19:32:55 toaster kernel: [    9.931719] [drm] Connector 2:
Jan  4 19:32:55 toaster kernel: [    9.931728] [drm]   SVIDEO-1
Jan  4 19:32:55 toaster kernel: [    9.931737] [drm]   Encoders:
Jan  4 19:32:55 toaster kernel: [    9.931746] [drm]     TV1: INTERNAL_DAC2
Jan  4 19:32:55 toaster kernel: [   10.068134] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
Jan  4 19:32:55 toaster kernel: [   10.166740] [drm] fb mappable at 0x98040000
Jan  4 19:32:55 toaster kernel: [   10.166773] [drm] vram apper at 0x98000000
Jan  4 19:32:55 toaster kernel: [   10.166783] [drm] size 1884160
Jan  4 19:32:55 toaster kernel: [   10.166793] [drm] fb depth is 8
Jan  4 19:32:55 toaster kernel: [   10.166803] [drm]    pitch is 1792
Jan  4 19:32:55 toaster kernel: [   10.227799] Console: switching to colour frame buffer device 210x65
Jan  4 19:32:55 toaster kernel: [   10.248934] radeon 0000:00:10.0: fb0: radeondrmfb frame buffer device
Jan  4 19:32:55 toaster kernel: [   10.248938] radeon 0000:00:10.0: registered panic notifier
Jan  4 19:32:55 toaster kernel: [   10.315494] [drm] Initialized radeon 2.39.0 20080528 for 0000:00:10.0 on minor 0
Jan  4 19:32:55 toaster kernel: [   10.951181] sungem_phy: PHY ID: 1378e1, addr: 0
Jan  4 19:32:55 toaster kernel: [   10.951213] gem 0002:20:0f.0 eth0: Found Generic MII PHY
Jan  4 19:32:55 toaster kernel: [   10.951622] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  4 19:32:55 toaster kernel: [   11.517300] RPC: Registered named UNIX socket transport module.
Jan  4 19:32:55 toaster kernel: [   11.517459] RPC: Registered udp transport module.
Jan  4 19:32:55 toaster kernel: [   11.517553] RPC: Registered tcp transport module.
Jan  4 19:32:55 toaster kernel: [   11.517645] RPC: Registered tcp NFSv4.1 backchannel transport module.
Jan  4 19:32:55 toaster kernel: [   11.532775] FS-Cache: Loaded
Jan  4 19:32:55 toaster kernel: [   11.566215] FS-Cache: Netfs 'nfs' registered for caching
Jan  4 19:32:55 toaster kernel: [   11.608801] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jan  4 19:32:55 toaster systemd[1]: Started Make remote CUPS printers available locally.
Jan  4 19:32:55 toaster systemd[1]: Starting Permit User Sessions...
Jan  4 19:32:55 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:33:25 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:32:55 toaster systemd[1]: Started System Logging Service.
Jan  4 19:32:56 toaster systemd[1]: Started /etc/rc.local Compatibility.
Jan  4 19:32:56 toaster systemd[1]: Started LSB: handle special hotkeys of Apple computers.
Jan  4 19:32:56 toaster systemd[1]: Started LSB: SANE network scanner server.
Jan  4 19:32:56 toaster systemd[1]: Started Permit User Sessions.
Jan  4 19:32:56 toaster systemd[1]: Started Login Service.
Jan  4 19:32:56 toaster systemd[1]: Starting Getty on tty1...
Jan  4 19:32:56 toaster systemd[1]: Started Getty on tty1.
Jan  4 19:32:56 toaster systemd[1]: Starting Login Prompts.
Jan  4 19:32:56 toaster systemd[1]: Reached target Login Prompts.
Jan  4 19:32:56 toaster mouseemu[761]: mouseemu 0.15 (C) Colin Leroy <colin@colino.net>
Jan  4 19:32:56 toaster mouseemu[761]: using (0+68) as middle button, (0+87) as right button, (56) as scroll.
Jan  4 19:32:56 toaster mouseemu[484]: Starting mouse emulation daemon: mouseemu.
Jan  4 19:32:56 toaster systemd[1]: Started LSB: Emulate mouse buttons and mouse wheel.
Jan  4 19:32:56 toaster exim4[481]: Starting MTA: exim4.
Jan  4 19:32:56 toaster systemd[1]: Started LSB: exim Mail Transport Agent.
Jan  4 19:32:56 toaster systemd[1]: Starting Multi-User System.
Jan  4 19:32:56 toaster systemd[1]: Reached target Multi-User System.
Jan  4 19:32:56 toaster systemd[1]: Starting Graphical Interface.
Jan  4 19:32:56 toaster systemd[1]: Reached target Graphical Interface.
Jan  4 19:32:56 toaster systemd[1]: Starting Update UTMP about System Runlevel Changes...
Jan  4 19:32:56 toaster systemd[1]: Started Update UTMP about System Runlevel Changes.
Jan  4 19:32:56 toaster systemd[1]: Startup finished in 5.573s (kernel) + 7.789s (userspace) = 13.362s.
Jan  4 19:32:56 toaster kernel: [   13.358813] gem 0002:20:0f.0 eth0: Link is up at 100 Mbps, full-duplex
Jan  4 19:32:56 toaster kernel: [   13.358921] gem 0002:20:0f.0 eth0: Pause is disabled
Jan  4 19:32:56 toaster kernel: [   13.372915] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan  4 19:32:57 toaster mouseemu[764]: Trying to open /dev/uinput...
Jan  4 19:32:57 toaster mouseemu[764]:  ok.
Jan  4 19:32:57 toaster kernel: [   14.106269] input: Mouseemu virtual keyboard as /devices/virtual/input/input5
Jan  4 19:32:57 toaster kernel: [   14.107295] input: Mouseemu virtual mouse as /devices/virtual/input/input6
Jan  4 19:32:57 toaster mouseemu[764]: Trying to open /dev/uinput...
Jan  4 19:32:57 toaster mouseemu[764]:  ok.
Jan  4 19:32:57 toaster avahi-daemon[487]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:65ff:fec1:2832.
Jan  4 19:32:57 toaster avahi-daemon[487]: New relevant interface eth0.IPv6 for mDNS.
Jan  4 19:32:57 toaster avahi-daemon[487]: Registering new address record for fe80::230:65ff:fec1:2832 on eth0.*.
Jan  4 19:32:57 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan  4 19:32:57 toaster ifup[429]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan  4 19:32:59 toaster dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  4 19:32:59 toaster dhclient: DHCPOFFER from 192.168.0.1
Jan  4 19:32:59 toaster ifup[429]: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  4 19:32:59 toaster ifup[429]: DHCPOFFER from 192.168.0.1
Jan  4 19:33:02 toaster dhclient: DHCPACK from 192.168.0.1
Jan  4 19:33:02 toaster ifup[429]: DHCPACK from 192.168.0.1
Jan  4 19:33:02 toaster avahi-daemon[487]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.113.
Jan  4 19:33:02 toaster avahi-daemon[487]: New relevant interface eth0.IPv4 for mDNS.
Jan  4 19:33:02 toaster avahi-daemon[487]: Registering new address record for 192.168.0.113 on eth0.IPv4.
Jan  4 19:33:02 toaster dhclient: bound to 192.168.0.113 -- renewal in 19393 seconds.
Jan  4 19:33:02 toaster ifup[429]: bound to 192.168.0.113 -- renewal in 19393 seconds.
Jan  4 19:34:33 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:35:03 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:34:33 toaster systemd[1]: Starting user-0.slice.
Jan  4 19:34:33 toaster systemd[1]: Created slice user-0.slice.
Jan  4 19:34:33 toaster systemd[1]: Starting Session 1 of user root.
Jan  4 19:34:33 toaster systemd[1]: Started Session 1 of user root.
Jan  4 19:34:33 toaster systemd[1]: Starting User Manager for UID 0...
Jan  4 19:34:33 toaster systemd[859]: Starting Paths.
Jan  4 19:34:33 toaster systemd[859]: Reached target Paths.
Jan  4 19:34:33 toaster systemd[859]: Starting Timers.
Jan  4 19:34:33 toaster systemd[859]: Reached target Timers.
Jan  4 19:34:33 toaster systemd[859]: Starting Sockets.
Jan  4 19:34:33 toaster systemd[859]: Reached target Sockets.
Jan  4 19:34:33 toaster systemd[859]: Starting Basic System.
Jan  4 19:34:33 toaster systemd[859]: Reached target Basic System.
Jan  4 19:34:33 toaster systemd[859]: Starting Default.
Jan  4 19:34:33 toaster systemd[859]: Reached target Default.
Jan  4 19:34:33 toaster systemd[859]: Startup finished in 29ms.
Jan  4 19:34:33 toaster systemd[1]: Started User Manager for UID 0.
Jan  4 19:37:01 toaster kernel: [  257.690981] sr 0:0:1:0: [sr0]  
Jan  4 19:37:01 toaster kernel: [  257.691072] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan  4 19:37:01 toaster kernel: [  257.691185] sr 0:0:1:0: [sr0]  
Jan  4 19:37:01 toaster kernel: [  257.691250] Sense Key : Illegal Request [current] 
Jan  4 19:37:01 toaster kernel: [  257.691358] Info fld=0x50c10
Jan  4 19:37:01 toaster kernel: [  257.691419] sr 0:0:1:0: [sr0]  
Jan  4 19:37:01 toaster kernel: [  257.691502] Add. Sense: Illegal mode for this track
Jan  4 19:37:01 toaster kernel: [  257.691604] sr 0:0:1:0: [sr0] CDB: 
Jan  4 19:37:01 toaster kernel: [  257.691675] Read(10): 28 00 00 05 0c 10 00 00 02 00
Jan  4 19:37:01 toaster kernel: [  257.691827] end_request: I/O error, dev sr0, sector 1323072
Jan  4 19:37:01 toaster kernel: [  257.691940] Buffer I/O error on device sr0, logical block 165384
Jan  4 19:37:01 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:37:31 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:37:03 toaster kernel: [  259.834970] sr 0:0:1:0: [sr0]  
Jan  4 19:37:03 toaster kernel: [  259.835051] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan  4 19:37:03 toaster kernel: [  259.835162] sr 0:0:1:0: [sr0]  
Jan  4 19:37:03 toaster kernel: [  259.835225] Sense Key : Illegal Request [current] 
Jan  4 19:37:03 toaster kernel: [  259.835329] Info fld=0x50c10
Jan  4 19:37:03 toaster kernel: [  259.835390] sr 0:0:1:0: [sr0]  
Jan  4 19:37:03 toaster kernel: [  259.835464] Add. Sense: Illegal mode for this track
Jan  4 19:37:03 toaster kernel: [  259.835566] sr 0:0:1:0: [sr0] CDB: 
Jan  4 19:37:03 toaster kernel: [  259.835634] Read(10): 28 00 00 05 0c 10 00 00 02 00
Jan  4 19:37:03 toaster kernel: [  259.835784] end_request: I/O error, dev sr0, sector 1323072
Jan  4 19:37:03 toaster kernel: [  259.835896] Buffer I/O error on device sr0, logical block 165384
Jan  4 19:38:59 toaster kernel: [  375.722650] UDF-fs: warning (device sr0): udf_fill_super: No partition found (2)
Jan  4 19:38:59 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:39:29 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:38:59 toaster kernel: [  375.726951] ISO 9660 Extensions: Microsoft Joliet Level 3
Jan  4 19:38:59 toaster kernel: [  375.834178] ISO 9660 Extensions: RRIP_1991A
Jan  4 19:39:05 toaster systemd[1]: Reloading.
Jan  4 19:39:08 toaster systemd[1]: Reloading.
Jan  4 19:47:59 toaster systemd[1]: Starting Cleanup of Temporary Directories...
Jan  4 19:47:59 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:48:29 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:47:59 toaster systemd[1]: Started Cleanup of Temporary Directories.
Jan  4 19:57:39 toaster systemd[1]: Reloading.
Jan  4 19:57:39 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:58:09 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:58:12 toaster systemd[1]: Reloading.
Jan  4 19:58:12 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 19:58:42 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 19:58:13 toaster systemd[1]: Reloading.
Jan  4 19:58:13 toaster systemd[1]: Reloading.
Jan  4 19:58:13 toaster dbus[491]: [system] Reloaded configuration
Jan  4 19:58:28 toaster systemd[1]: Reloading.
Jan  4 20:17:01 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:17:31 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:17:01 toaster CRON[9948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 20:18:32 toaster kernel: [ 2749.470780] fuse init (API version 7.23)
Jan  4 20:18:32 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:19:02 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:19:48 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:19:48 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:20:18 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:19:49 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:19:49 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:19:49 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:25:34 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:25:34 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:26:34 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:26:55 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:26:55 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:27:55 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:26:55 toaster systemd-udevd[145]: specified user 'usbmux' unknown
Jan  4 20:28:37 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:28:37 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:29:37 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:32:17 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:32:17 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:33:17 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:32:17 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:32:17 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:32:18 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:32:43 toaster systemd[1]: Reloading.
Jan  4 20:32:44 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:32:54 toaster systemd[1]: Reloading.
Jan  4 20:32:57 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:33:02 toaster systemd[1]: Reloading.
Jan  4 20:33:02 toaster dbus[491]: [system] Reloaded configuration
Jan  4 20:34:20 toaster systemd[1]: Starting Synchronise Hardware Clock to System Clock...
Jan  4 20:34:20 toaster rsyslogd-2007: action 'action 17' suspended, next retry is Mon Jan  4 20:35:20 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:34:20 toaster systemd[1]: Deactivating swap /dev/disk/by-uuid/3e5e50c4-f33d-4fce-81e1-d6d45f990c09...
Jan  4 20:34:20 toaster systemd[1]: Deactivating swap /dev/disk/by-uuid/3e5e50c4-f33d-4fce-81e1-d6d45f990c09...
Jan  4 20:34:20 toaster systemd[1]: Stopping Session 1 of user root.
Jan  4 20:34:20 toaster systemd[1]: Stopping system-ifup.slice.
Jan  4 20:34:20 toaster systemd[1]: Removed slice system-ifup.slice.
Jan  4 20:34:20 toaster systemd[1]: Stopping Sound Card.
Jan  4 20:34:20 toaster systemd[1]: Stopped target Sound Card.
Jan  4 20:34:20 toaster systemd[1]: Stopping User Manager for UID 0...
Jan  4 20:34:20 toaster systemd[1]: Stopping Graphical Interface.
Jan  4 20:34:20 toaster systemd[1]: Stopped target Graphical Interface.
Jan  4 20:34:20 toaster systemd[1]: Stopping Multi-User System.
Jan  4 20:34:20 toaster systemd[859]: Stopping Default.
Jan  4 20:34:20 toaster systemd[859]: Stopped target Default.
Jan  4 20:34:20 toaster systemd[859]: Stopping Basic System.
Jan  4 20:34:20 toaster systemd[859]: Stopped target Basic System.
Jan  4 20:34:20 toaster systemd[859]: Stopping Paths.
Jan  4 20:34:20 toaster systemd[859]: Stopped target Paths.
Jan  4 20:34:20 toaster systemd[859]: Stopping Timers.
Jan  4 20:34:20 toaster systemd[859]: Stopped target Timers.
Jan  4 20:34:20 toaster systemd[859]: Stopping Sockets.
Jan  4 20:34:20 toaster systemd[859]: Stopped target Sockets.
Jan  4 20:34:20 toaster systemd[859]: Starting Shutdown.
Jan  4 20:34:20 toaster systemd[859]: Reached target Shutdown.
Jan  4 20:34:20 toaster systemd[859]: Starting Exit the Session...
Jan  4 20:34:20 toaster systemd[859]: Received SIGRTMIN+24 from PID 29906 (kill).
Jan  4 20:34:20 toaster systemd[1]: Stopped target Multi-User System.
Jan  4 20:34:20 toaster systemd[1]: Stopping Deferred execution scheduler...
Jan  4 20:34:20 toaster systemd[1]: Stopping OpenBSD Secure Shell server...
Jan  4 20:34:20 toaster systemd[1]: Stopping Regular background program processing daemon...
Jan  4 20:34:20 toaster systemd[1]: Stopping Make remote CUPS printers available locally...
Jan  4 20:34:20 toaster systemd[1]: Stopping Login Prompts.
Jan  4 20:34:20 toaster systemd[1]: Stopped target Login Prompts.
Jan  4 20:34:20 toaster systemd[1]: Stopping Getty on tty1...
Jan  4 20:34:20 toaster systemd[1]: Stopping LSB: handle special hotkeys of Apple computers...
Jan  4 20:34:20 toaster systemd[1]: Stopping LSB: SANE network scanner server...
Jan  4 20:34:20 toaster systemd[1]: Stopping LSB: exim Mail Transport Agent...
Jan  4 20:34:20 toaster pbbuttonsd[29912]: Stopping pbbuttonsd: pbbuttonsd.
Jan  4 20:34:20 toaster systemd[1]: Stopping LSB: Emulate mouse buttons and mouse wheel...
Jan  4 20:34:20 toaster saned[29914]: saned disabled; edit /etc/default/saned.
Jan  4 20:34:20 toaster systemd[1]: Stopping D-Bus System Message Bus...
Jan  4 20:34:21 toaster avahi-daemon[487]: Disconnected from D-Bus, exiting.
Jan  4 20:34:21 toaster avahi-daemon[487]: Got SIGTERM, quitting.
Jan  4 20:34:21 toaster avahi-daemon[487]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::230:65ff:fec1:2832.
Jan  4 20:34:21 toaster avahi-daemon[487]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.113.
Jan  4 20:34:21 toaster systemd[1]: Stopping System Logging Service...
Jan  4 20:34:21 toaster avahi-daemon[487]: avahi-daemon 0.6.31 exiting.
Jan  4 20:34:21 toaster mouseemu[764]: mouseemu: cleaning...
Jan  4 20:34:21 toaster rsyslogd: [origin software="rsyslogd" swVersion="8.4.2" x-pid="543" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan  4 20:36:20 toaster rsyslogd: [origin software="rsyslogd" swVersion="8.4.2" x-pid="545" x-info="http://www.rsyslog.com"] start
Jan  4 20:36:20 toaster systemd-modules-load[126]: Inserted module 'lp'
Jan  4 20:36:20 toaster systemd-modules-load[126]: Failed to find module 'ppdev'
Jan  4 20:36:20 toaster systemd-modules-load[126]: Inserted module 'parport_pc'
Jan  4 20:36:20 toaster systemd-modules-load[126]: Inserted module 'fuse'
Jan  4 20:36:20 toaster systemd[1]: Started Create Static Device Nodes in /dev.
Jan  4 20:36:20 toaster systemd[1]: Starting udev Kernel Device Manager...
Jan  4 20:36:20 toaster systemd[1]: Started udev Kernel Device Manager.
Jan  4 20:36:20 toaster systemd[1]: Starting Copy rules generated while the root was ro...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Tune IDE hard disks...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Set preliminary keymap...
Jan  4 20:36:20 toaster systemd[1]: Started Copy rules generated while the root was ro.
Jan  4 20:36:20 toaster hdparm[148]: Setting parameters of disc: (none).
Jan  4 20:36:20 toaster systemd[1]: Mounted FUSE Control File System.
Jan  4 20:36:20 toaster mtp-probe: checking bus 1, device 2: "/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1"
Jan  4 20:36:20 toaster mtp-probe: bus: 1, device: 2 was not an MTP device
Jan  4 20:36:20 toaster systemd-modules-load[126]: Inserted module 'airport'
Jan  4 20:36:20 toaster systemd-modules-load[126]: Failed to find module 'apm_emu'
Jan  4 20:36:20 toaster systemd[1]: systemd-modules-load.service: main process exited, code=exited, status=1/FAILURE
Jan  4 20:36:20 toaster systemd[1]: Failed to start Load Kernel Modules.
Jan  4 20:36:20 toaster systemd[1]: Unit systemd-modules-load.service entered failed state.
Jan  4 20:36:20 toaster systemd[1]: Mounted Configuration File System.
Jan  4 20:36:20 toaster systemd[1]: Starting Apply Kernel Variables...
Jan  4 20:36:20 toaster systemd[1]: Starting system-ifup.slice.
Jan  4 20:36:20 toaster systemd[1]: Created slice system-ifup.slice.
Jan  4 20:36:20 toaster systemd[1]: Started Apply Kernel Variables.
Jan  4 20:36:20 toaster mtp-probe: checking bus 1, device 4: "/sys/devices/pci0001:10/0001:10:18.0/usb1/1-2/1-2.3"
Jan  4 20:36:20 toaster mtp-probe: bus: 1, device: 4 was not an MTP device
Jan  4 20:36:20 toaster mtp-probe: checking bus 2, device 3: "/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1"
Jan  4 20:36:20 toaster mtp-probe: checking bus 2, device 4: "/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.3"
Jan  4 20:36:20 toaster mtp-probe: bus: 2, device: 3 was not an MTP device
Jan  4 20:36:20 toaster mtp-probe: bus: 2, device: 4 was not an MTP device
Jan  4 20:36:20 toaster systemd[1]: Found device OWC_Mercury_Electra_3G_SSD swap.
Jan  4 20:36:20 toaster systemd[1]: Starting Sound Card.
Jan  4 20:36:20 toaster systemd[1]: Reached target Sound Card.
Jan  4 20:36:20 toaster systemd[1]: Activating swap /dev/disk/by-uuid/3e5e50c4-f33d-4fce-81e1-d6d45f990c09...
Jan  4 20:36:20 toaster systemd[1]: Starting system-systemd\x2drfkill.slice.
Jan  4 20:36:20 toaster systemd[1]: Created slice system-systemd\x2drfkill.slice.
Jan  4 20:36:20 toaster systemd[1]: Activated swap /dev/disk/by-uuid/3e5e50c4-f33d-4fce-81e1-d6d45f990c09.
Jan  4 20:36:20 toaster systemd[1]: Starting Swap.
Jan  4 20:36:20 toaster systemd[1]: Reached target Swap.
Jan  4 20:36:20 toaster keyboard-setup[149]: Setting preliminary keymap...done.
Jan  4 20:36:20 toaster systemd[1]: Started LSB: Set preliminary keymap.
Jan  4 20:36:20 toaster systemd[1]: Starting Remount Root and Kernel File Systems...
Jan  4 20:36:20 toaster systemd[1]: Started Remount Root and Kernel File Systems.
Jan  4 20:36:20 toaster systemd[1]: Starting Load/Save RF Kill Switch Status of rfkill0...
Jan  4 20:36:20 toaster systemd[1]: Started Various fixups to make systemd work better on Debian.
Jan  4 20:36:20 toaster systemd[1]: Starting Load/Save Random Seed...
Jan  4 20:36:20 toaster systemd[1]: Starting Local File Systems (Pre).
Jan  4 20:36:20 toaster systemd[1]: Reached target Local File Systems (Pre).
Jan  4 20:36:20 toaster systemd[1]: Starting Local File Systems.
Jan  4 20:36:20 toaster systemd[1]: Reached target Local File Systems.
Jan  4 20:36:20 toaster systemd[1]: Starting Create Volatile Files and Directories...
Jan  4 20:36:20 toaster systemd[1]: Starting Remote File Systems.
Jan  4 20:36:20 toaster systemd[1]: Reached target Remote File Systems.
Jan  4 20:36:20 toaster systemd[1]: Starting Trigger Flushing of Journal to Persistent Storage...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Prepare console...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: start firewall...
Jan  4 20:36:20 toaster systemd[1]: Started Load/Save RF Kill Switch Status of rfkill0.
Jan  4 20:36:20 toaster systemd[1]: Started Load/Save Random Seed.
Jan  4 20:36:20 toaster ufw[307]: Skip starting firewall: ufw (not enabled)...done.
Jan  4 20:36:20 toaster systemd[1]: Started Create Volatile Files and Directories.
Jan  4 20:36:20 toaster systemd[1]: Started LSB: start firewall.
Jan  4 20:36:20 toaster kbd[306]: Setting console screen modes.
Jan  4 20:36:20 toaster systemd[1]: Started Trigger Flushing of Journal to Persistent Storage.
Jan  4 20:36:20 toaster systemd[1]: Starting Update UTMP about System Boot/Shutdown...
Jan  4 20:36:20 toaster kbd[306]: setterm: $TERM is not defined.
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Raise network interfaces....
Jan  4 20:36:20 toaster systemd[1]: Started LSB: Prepare console.
Jan  4 20:36:20 toaster systemd[1]: Started Update UTMP about System Boot/Shutdown.
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Set console font and keymap...
Jan  4 20:36:20 toaster networking[340]: Configuring network interfaces...done.
Jan  4 20:36:20 toaster systemd[1]: Started LSB: Raise network interfaces..
Jan  4 20:36:20 toaster systemd[1]: Starting ifup for eth0...
Jan  4 20:36:20 toaster systemd[1]: Started ifup for eth0.
Jan  4 20:36:20 toaster systemd[1]: Starting Network.
Jan  4 20:36:20 toaster systemd[1]: Reached target Network.
Jan  4 20:36:20 toaster systemd[1]: Starting Network is Online.
Jan  4 20:36:20 toaster systemd[1]: Reached target Network is Online.
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: RPC portmapper replacement...
Jan  4 20:36:20 toaster dhclient: Internet Systems Consortium DHCP Client 4.3.1
Jan  4 20:36:20 toaster ifup[427]: Internet Systems Consortium DHCP Client 4.3.1
Jan  4 20:36:20 toaster dhclient: Copyright 2004-2014 Internet Systems Consortium.
Jan  4 20:36:20 toaster ifup[427]: Copyright 2004-2014 Internet Systems Consortium.
Jan  4 20:36:20 toaster dhclient: All rights reserved.
Jan  4 20:36:20 toaster dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  4 20:36:20 toaster kernel: [    0.000000] Using PowerMac machine description
Jan  4 20:36:20 toaster kernel: [    0.000000] Total memory = 1536MB; using 4096kB for hash table (at cfc00000)
Jan  4 20:36:20 toaster kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  4 20:36:20 toaster kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  4 20:36:20 toaster kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  4 20:36:20 toaster kernel: [    0.000000] Linux version 3.16.0-4-powerpc (debian-kernel@lists.debian.org) (gcc version 4.8.4 (Debian 4.8.4-1) ) #1 Debian 3.16.7-ckt20-1+deb8u1 (2015-12-14)
Jan  4 20:36:20 toaster kernel: [    0.000000] Found initrd at 0xc1600000:0xc2466000
Jan  4 20:36:20 toaster kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x08
Jan  4 20:36:20 toaster kernel: [    0.000000] Mapped at 0xff7c0000
Jan  4 20:36:20 toaster kernel: [    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xff740000
Jan  4 20:36:20 toaster kernel: [    0.000000] Processor NAP mode on idle enabled.
Jan  4 20:36:20 toaster kernel: [    0.000000] PowerMac motherboard: PowerMac G4 Cube
Jan  4 20:36:20 toaster kernel: [    0.000000] bootconsole [udbg0] enabled
Jan  4 20:36:20 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
Jan  4 20:36:20 toaster kernel: [    0.000000] PCI host bridge /pci@f0000000  ranges:
Jan  4 20:36:20 toaster kernel: [    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
Jan  4 20:36:20 toaster kernel: [    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
Jan  4 20:36:20 toaster kernel: [    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
Jan  4 20:36:20 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
Jan  4 20:36:20 toaster kernel: [    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
Jan  4 20:36:20 toaster kernel: [    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
Jan  4 20:36:20 toaster kernel: [    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
Jan  4 20:36:20 toaster kernel: [    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
Jan  4 20:36:20 toaster kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
Jan  4 20:36:20 toaster kernel: [    0.000000] PCI host bridge /pci@f4000000  ranges:
Jan  4 20:36:20 toaster kernel: [    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
Jan  4 20:36:20 toaster kernel: [    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
Jan  4 20:36:20 toaster kernel: [    0.000000] via-pmu: Server Mode is disabled
Jan  4 20:36:20 toaster kernel: [    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: Checking bank 0...
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: gen0=166, gen1=165
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: Active bank is: 0
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: OF partition at 0x210
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: XP partition at 0x1a30
Jan  4 20:36:20 toaster kernel: [    0.000000] nvram: NR partition at 0x1b30
Jan  4 20:36:20 toaster kernel: [    0.000000] Top of RAM: 0x60000000, Total RAM: 0x60000000
Jan  4 20:36:20 toaster kernel: [    0.000000] Memory hole size: 0MB
Jan  4 20:36:20 toaster kernel: [    0.000000] Zone ranges:
Jan  4 20:36:20 toaster kernel: [    0.000000]   DMA      [mem 0x00000000-0x2fffffff]
Jan  4 20:36:20 toaster kernel: [    0.000000]   Normal   empty
Jan  4 20:36:20 toaster kernel: [    0.000000]   HighMem  [mem 0x30000000-0x5fffffff]
Jan  4 20:36:20 toaster kernel: [    0.000000] Movable zone start for each node
Jan  4 20:36:20 toaster kernel: [    0.000000] Early memory node ranges
Jan  4 20:36:20 toaster kernel: [    0.000000]   node   0: [mem 0x00000000-0x5fffffff]
Jan  4 20:36:20 toaster kernel: [    0.000000] On node 0 totalpages: 393216
Jan  4 20:36:20 toaster kernel: [    0.000000] free_area_init_node: node 0, pgdat c072b1ec, node_mem_map c08b3000
Jan  4 20:36:20 toaster kernel: [    0.000000]   DMA zone: 1536 pages used for memmap
Jan  4 20:36:20 toaster kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  4 20:36:20 toaster kernel: [    0.000000]   DMA zone: 196608 pages, LIFO batch:31
Jan  4 20:36:20 toaster kernel: [    0.000000]   HighMem zone: 1536 pages used for memmap
Jan  4 20:36:20 toaster kernel: [    0.000000]   HighMem zone: 196608 pages, LIFO batch:31
Jan  4 20:36:20 toaster kernel: [    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
Jan  4 20:36:20 toaster kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan  4 20:36:20 toaster kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 391680
Jan  4 20:36:20 toaster kernel: [    0.000000] Kernel command line: root=UUID=11758325-78b3-4cc0-9cb2-d0cd860c4e5d ro radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1
Jan  4 20:36:20 toaster kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  4 20:36:20 toaster kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  4 20:36:20 toaster kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  4 20:36:20 toaster kernel: [    0.000000] Sorting __ex_table...
Jan  4 20:36:20 toaster kernel: [    0.000000] Memory: 1531500K/1572864K available (5184K kernel code, 420K rwdata, 1428K rodata, 404K init, 1403K bss, 41364K reserved, 786432K highmem)
Jan  4 20:36:20 toaster kernel: [    0.000000] Kernel virtual memory layout:
Jan  4 20:36:20 toaster kernel: [    0.000000]   * 0xfffcf000..0xfffff000  : fixmap
Jan  4 20:36:20 toaster kernel: [    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
Jan  4 20:36:20 toaster kernel: [    0.000000]   * 0xfdd66000..0xff800000  : early ioremap
Jan  4 20:36:20 toaster kernel: [    0.000000]   * 0xf1000000..0xfdd66000  : vmalloc & ioremap
Jan  4 20:36:20 toaster kernel: [    0.000000] NR_IRQS:512 nr_irqs:512 16
Jan  4 20:36:20 toaster kernel: [    0.000000] mpic: Resetting
Jan  4 20:36:20 toaster kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 1 CPUs
Jan  4 20:36:20 toaster kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Jan  4 20:36:20 toaster kernel: [    0.000000] mpic: Initializing for 64 sources
Jan  4 20:36:20 toaster kernel: [    0.000000] GMT Delta read from XPRAM: -240 minutes, DST: on
Jan  4 20:36:20 toaster kernel: [    0.000000] time_init: decrementer frequency = 24.907667 MHz
Jan  4 20:36:20 toaster kernel: [    0.000000] time_init: processor frequency   = 1000.000000 MHz
Jan  4 20:36:20 toaster kernel: [    0.000015] clocksource: timebase mult[2825f5b5] shift[24] registered
Jan  4 20:36:20 toaster kernel: [    0.000438] clockevent: decrementer mult[660594f] shift[32] cpu[0]
Jan  4 20:36:20 toaster kernel: [    0.000680] Console: colour dummy device 80x25
Jan  4 20:36:20 toaster kernel: [    0.001074] console [tty0] enabled
Jan  4 20:36:20 toaster kernel: [    0.001452] bootconsole [udbg0] disabled
Jan  4 20:36:20 toaster kernel: [    0.001884] pmac_zilog: i2c-modem detected, id: 1
Jan  4 20:36:20 toaster kernel: [    0.002171] pid_max: default: 32768 minimum: 301
Jan  4 20:36:20 toaster kernel: [    0.002270] Security Framework initialized
Jan  4 20:36:20 toaster kernel: [    0.002352] AppArmor: AppArmor disabled by boot time parameter
Jan  4 20:36:20 toaster kernel: [    0.002365] Yama: disabled by default; enable with sysctl kernel.yama.*
Jan  4 20:36:20 toaster kernel: [    0.002430] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  4 20:36:20 toaster kernel: [    0.002446] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  4 20:36:20 toaster kernel: [    0.003191] Initializing cgroup subsys memory
Jan  4 20:36:20 toaster kernel: [    0.003226] Initializing cgroup subsys devices
Jan  4 20:36:20 toaster kernel: [    0.003258] Initializing cgroup subsys freezer
Jan  4 20:36:20 toaster kernel: [    0.003276] Initializing cgroup subsys net_cls
Jan  4 20:36:20 toaster kernel: [    0.003305] Initializing cgroup subsys blkio
Jan  4 20:36:20 toaster kernel: [    0.003327] Initializing cgroup subsys perf_event
Jan  4 20:36:20 toaster kernel: [    0.003341] Initializing cgroup subsys net_prio
Jan  4 20:36:20 toaster kernel: [    0.003397] ftrace: allocating 17986 entries in 53 pages
Jan  4 20:36:20 toaster kernel: [    0.025308] MPC7450 family performance monitor hardware support registered
Jan  4 20:36:20 toaster kernel: [    0.029371] devtmpfs: initialized
Jan  4 20:36:20 toaster kernel: [    0.030778] device-tree: Duplicate name in PowerPC,G4@0, renamed to "l2-cache#1"
Jan  4 20:36:20 toaster kernel: [    0.030838] device-tree: Duplicate name in l2-cache#1, renamed to "l2-cache#1"
Jan  4 20:36:20 toaster kernel: [    0.033691] NET: Registered protocol family 16
Jan  4 20:36:20 toaster kernel: [    0.034881] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Jan  4 20:36:20 toaster kernel: [    0.034912]  channel 0 bus <multibus>
Jan  4 20:36:20 toaster kernel: [    0.034924]  channel 1 bus <multibus>
Jan  4 20:36:20 toaster kernel: [    0.034981] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Jan  4 20:36:20 toaster kernel: [    0.034998]  channel 0 bus <multibus>
Jan  4 20:36:20 toaster kernel: [    0.035033] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
Jan  4 20:36:20 toaster kernel: [    0.035051]  channel 1 bus <multibus>
Jan  4 20:36:20 toaster kernel: [    0.035063]  channel 2 bus <multibus>
Jan  4 20:36:20 toaster kernel: [    0.035491] PCI: Probing PCI hardware
Jan  4 20:36:20 toaster kernel: [    0.035633] PCI host bridge to bus 0000:00
Jan  4 20:36:20 toaster kernel: [    0.035656] pci_bus 0000:00: root bus resource [io  0x802000-0x1001fff] (bus address [0x0000-0x7fffff])
Jan  4 20:36:20 toaster kernel: [    0.035679] pci_bus 0000:00: root bus resource [mem 0xf1000000-0xf1ffffff]
Jan  4 20:36:20 toaster kernel: [    0.035695] pci_bus 0000:00: root bus resource [mem 0x90000000-0x9fffffff]
Jan  4 20:36:20 toaster kernel: [    0.035713] pci_bus 0000:00: root bus resource [bus 00-ff]
Jan  4 20:36:20 toaster kernel: [    0.035731] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to ff
Jan  4 20:36:20 toaster kernel: [    0.035774] pci 0000:00:0b.0: [106b:0020] type 00 class 0x060000
Jan  4 20:36:20 toaster kernel: [    0.036001] pci 0000:00:10.0: [1002:5157] type 00 class 0x030000
Jan  4 20:36:20 toaster kernel: [    0.036025] pci 0000:00:10.0: reg 0x10: [mem 0x98000000-0x9fffffff pref]
Jan  4 20:36:20 toaster kernel: [    0.036037] pci 0000:00:10.0: reg 0x14: [io  0x802400-0x8024ff]
Jan  4 20:36:20 toaster kernel: [    0.036049] pci 0000:00:10.0: reg 0x18: [mem 0x90000000-0x9000ffff]
Jan  4 20:36:20 toaster kernel: [    0.036076] pci 0000:00:10.0: reg 0x30: [mem 0x90020000-0x9003ffff pref]
Jan  4 20:36:20 toaster kernel: [    0.036117] pci 0000:00:10.0: supports D1 D2
Jan  4 20:36:20 toaster kernel: [    0.036294] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 00
Jan  4 20:36:20 toaster kernel: [    0.036424] PCI host bridge to bus 0001:10
Jan  4 20:36:20 toaster kernel: [    0.036440] pci_bus 0001:10: root bus resource [io  0x0000-0x7fffff]
Jan  4 20:36:20 toaster kernel: [    0.036456] pci_bus 0001:10: root bus resource [mem 0xf3000000-0xf3ffffff]
Jan  4 20:36:20 toaster kernel: [    0.036472] pci_bus 0001:10: root bus resource [mem 0x80000000-0x8fffffff]
Jan  4 20:36:20 toaster kernel: [    0.036489] pci_bus 0001:10: root bus resource [bus 10-ff]
Jan  4 20:36:20 toaster kernel: [    0.036504] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to ff
Jan  4 20:36:20 toaster kernel: [    0.036535] pci 0001:10:0b.0: [106b:001f] type 00 class 0x060000
Jan  4 20:36:20 toaster kernel: [    0.036715] pci 0001:10:17.0: [106b:0022] type 00 class 0xff0000
Jan  4 20:36:20 toaster kernel: [    0.036732] pci 0001:10:17.0: reg 0x10: [mem 0x80000000-0x8007ffff]
Jan  4 20:36:20 toaster kernel: [    0.036908] pci 0001:10:18.0: [106b:0019] type 00 class 0x0c0310
Jan  4 20:36:20 toaster kernel: [    0.036924] pci 0001:10:18.0: reg 0x10: [mem 0x80082000-0x80082fff]
Jan  4 20:36:20 toaster kernel: [    0.037111] pci 0001:10:19.0: [106b:0019] type 00 class 0x0c0310
Jan  4 20:36:20 toaster kernel: [    0.037127] pci 0001:10:19.0: reg 0x10: [mem 0x80081000-0x80081fff]
Jan  4 20:36:20 toaster kernel: [    0.037306] pci 0001:10:1a.0: [104c:8020] type 00 class 0x0c0010
Jan  4 20:36:20 toaster kernel: [    0.037326] pci 0001:10:1a.0: reg 0x10: [mem 0x80080000-0x800807ff]
Jan  4 20:36:20 toaster kernel: [    0.037338] pci 0001:10:1a.0: reg 0x14: [mem 0x80084000-0x80087fff]
Jan  4 20:36:20 toaster kernel: [    0.037396] pci 0001:10:1a.0: supports D2
Jan  4 20:36:20 toaster kernel: [    0.037403] pci 0001:10:1a.0: PME# supported from D2 D3hot
Jan  4 20:36:20 toaster kernel: [    0.037614] pci_bus 0001:10: busn_res: [bus 10-ff] end is updated to 10
Jan  4 20:36:20 toaster kernel: [    0.037740] PCI host bridge to bus 0002:20
Jan  4 20:36:20 toaster kernel: [    0.037761] pci_bus 0002:20: root bus resource [io  0xff7fe000-0xffffdfff] (bus address [0x0000-0x7fffff])
Jan  4 20:36:20 toaster kernel: [    0.037784] pci_bus 0002:20: root bus resource [mem 0xf5000000-0xf5ffffff]
Jan  4 20:36:20 toaster kernel: [    0.037801] pci_bus 0002:20: root bus resource [bus 20-ff]
Jan  4 20:36:20 toaster kernel: [    0.037817] pci_bus 0002:20: busn_res: [bus 20-ff] end is updated to ff
Jan  4 20:36:20 toaster kernel: [    0.037843] pci 0002:20:0b.0: [106b:001e] type 00 class 0x060000
Jan  4 20:36:20 toaster kernel: [    0.038009] pci 0002:20:0f.0: [106b:0021] type 00 class 0x020000
Jan  4 20:36:20 toaster kernel: [    0.038026] pci 0002:20:0f.0: reg 0x10: [mem 0xf5200000-0xf53fffff]
Jan  4 20:36:20 toaster kernel: [    0.038062] pci 0002:20:0f.0: reg 0x30: [mem 0xf5000000-0xf50fffff pref]
Jan  4 20:36:20 toaster kernel: [    0.038230] pci_bus 0002:20: busn_res: [bus 20-ff] end is updated to 20
Jan  4 20:36:20 toaster kernel: [    0.038292] PCI 0000:00 Cannot reserve Legacy IO [io  0x802000-0x802fff]
Jan  4 20:36:20 toaster kernel: [    0.038312] pci_bus 0000:00: resource 4 [io  0x802000-0x1001fff]
Jan  4 20:36:20 toaster kernel: [    0.038318] pci_bus 0000:00: resource 5 [mem 0xf1000000-0xf1ffffff]
Jan  4 20:36:20 toaster kernel: [    0.038325] pci_bus 0000:00: resource 6 [mem 0x90000000-0x9fffffff]
Jan  4 20:36:20 toaster kernel: [    0.038333] pci_bus 0001:10: resource 4 [io  0x0000-0x7fffff]
Jan  4 20:36:20 toaster kernel: [    0.038340] pci_bus 0001:10: resource 5 [mem 0xf3000000-0xf3ffffff]
Jan  4 20:36:20 toaster kernel: [    0.038347] pci_bus 0001:10: resource 6 [mem 0x80000000-0x8fffffff]
Jan  4 20:36:20 toaster kernel: [    0.038354] pci_bus 0002:20: resource 4 [io  0xff7fe000-0xffffdfff]
Jan  4 20:36:20 toaster kernel: [    0.038361] pci_bus 0002:20: resource 5 [mem 0xf5000000-0xf5ffffff]
Jan  4 20:36:20 toaster kernel: [    0.041768] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
Jan  4 20:36:20 toaster kernel: [    0.041803] vgaarb: loaded
Jan  4 20:36:20 toaster kernel: [    0.041812] vgaarb: bridge control possible 0000:00:10.0
Jan  4 20:36:20 toaster kernel: [    0.042093] SCSI subsystem initialized
Jan  4 20:36:20 toaster kernel: [    0.042220] libata version 3.00 loaded.
Jan  4 20:36:20 toaster kernel: [    0.042796] Switched to clocksource timebase
Jan  4 20:36:20 toaster kernel: [    0.056071] NET: Registered protocol family 2
Jan  4 20:36:20 toaster kernel: [    0.056802] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jan  4 20:36:20 toaster kernel: [    0.056892] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
Jan  4 20:36:20 toaster kernel: [    0.056972] TCP: Hash tables configured (established 8192 bind 8192)
Jan  4 20:36:20 toaster kernel: [    0.057150] TCP: reno registered
Jan  4 20:36:20 toaster kernel: [    0.057168] UDP hash table entries: 512 (order: 1, 8192 bytes)
Jan  4 20:36:20 toaster kernel: [    0.057199] UDP-Lite hash table entries: 512 (order: 1, 8192 bytes)
Jan  4 20:36:20 toaster kernel: [    0.057364] NET: Registered protocol family 1
Jan  4 20:36:20 toaster kernel: [    0.057476] pci 0001:10:18.0: enabling device (0000 -> 0002)
Jan  4 20:36:20 toaster kernel: [    0.110859] pci 0001:10:19.0: enabling device (0000 -> 0002)
Jan  4 20:36:20 toaster kernel: [    0.166824] PCI: CLS mismatch (32 != 1020), using 32 bytes
Jan  4 20:36:20 toaster kernel: [    0.167031] Unpacking initramfs...
Jan  4 20:36:20 toaster kernel: [    0.861274] Freeing initrd memory: 14744K (c1600000 - c2466000)
Jan  4 20:36:20 toaster kernel: [    0.861793] Thermal assist unit not available
Jan  4 20:36:20 toaster kernel: [    0.862683] futex hash table entries: 256 (order: -1, 3072 bytes)
Jan  4 20:36:20 toaster kernel: [    0.862753] audit: initializing netlink subsys (disabled)
Jan  4 20:36:20 toaster kernel: [    0.862874] audit: type=2000 audit(1451972170.852:1): initialized
Jan  4 20:36:20 toaster kernel: [    0.863735] zbud: loaded
Jan  4 20:36:20 toaster kernel: [    0.863942] VFS: Disk quotas dquot_6.5.2
Jan  4 20:36:20 toaster kernel: [    0.863987] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  4 20:36:20 toaster kernel: [    0.864092] msgmni has been set to 1486
Jan  4 20:36:20 toaster kernel: [    0.865142] alg: No test for stdrng (krng)
Jan  4 20:36:20 toaster kernel: [    0.865233] bounce: pool size: 64 pages
Jan  4 20:36:20 toaster kernel: [    0.865291] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan  4 20:36:20 toaster kernel: [    0.865444] io scheduler noop registered
Jan  4 20:36:20 toaster kernel: [    0.865464] io scheduler deadline registered
Jan  4 20:36:20 toaster kernel: [    0.865563] io scheduler cfq registered (default)
Jan  4 20:36:20 toaster kernel: [    0.866375] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
Jan  4 20:36:20 toaster kernel: [    0.867269] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Jan  4 20:36:20 toaster kernel: [    0.867327] Serial: MPC52xx PSC UART driver
Jan  4 20:36:20 toaster kernel: [    0.867386] Generic non-volatile memory driver v1.1
Jan  4 20:36:20 toaster kernel: [    0.867495] Linux agpgart interface v0.103
Jan  4 20:36:20 toaster kernel: [    0.867547] agpgart-uninorth 0000:00:0b.0: Apple UniNorth chipset
Jan  4 20:36:20 toaster kernel: [    0.869878] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
Jan  4 20:36:20 toaster kernel: [    0.870027] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
Jan  4 20:36:20 toaster kernel: [    0.870229] MacIO PCI driver attached to Keylargo chipset
Jan  4 20:36:20 toaster kernel: [    0.871713] 0.00013020:ch-a: ttyPZ0 at MMIO 0x80013020 (irq = 22, base_baud = 230400) is a Z85c30 ESCC - Internal modem
Jan  4 20:36:20 toaster kernel: [    0.872070] 0.00013000:ch-b: ttyPZ1 at MMIO 0x80013000 (irq = 50, base_baud = 230400) is a Z85c30 ESCC - Serial port
Jan  4 20:36:20 toaster kernel: [    0.872979] adb: starting probe task...
Jan  4 20:36:20 toaster kernel: [    0.873002] adb: finished probe task...
Jan  4 20:36:20 toaster kernel: [    1.890902] pata-macio 0.0001f000:ata-4: Activating pata-macio chipset KeyLargo ATA-4, Apple bus ID 2
Jan  4 20:36:20 toaster kernel: [    1.891551] scsi0 : pata_macio
Jan  4 20:36:20 toaster kernel: [    1.891756] ata1: PATA max UDMA/66 irq 19
Jan  4 20:36:20 toaster kernel: [    2.064654] ata1.00: ATA-8: OWC Mercury Electra 3G SSD, 603ABBF0, max UDMA/133
Jan  4 20:36:20 toaster kernel: [    2.064680] ata1.00: 117231408 sectors, multi 1: LBA48 NCQ (depth 0/32)
Jan  4 20:36:20 toaster kernel: [    2.064705] ata1.01: ATAPI: MATSHITADVD-ROM SR-8186, F113, max UDMA/33
Jan  4 20:36:20 toaster kernel: [    2.072552] ata1.00: configured for UDMA/66
Jan  4 20:36:20 toaster kernel: [    2.087140] ata1.01: configured for UDMA/33
Jan  4 20:36:20 toaster kernel: [    2.088280] scsi 0:0:0:0: Direct-Access     ATA      OWC Mercury Elec BBF0 PQ: 0 ANSI: 5
Jan  4 20:36:20 toaster kernel: [    2.089778] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8186  F113 PQ: 0 ANSI: 5
Jan  4 20:36:20 toaster kernel: [    2.910836] pata-macio 0.00020000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 0
Jan  4 20:36:20 toaster kernel: [    2.911451] scsi1 : pata_macio
Jan  4 20:36:20 toaster kernel: [    2.911626] ata2: PATA max MWDMA2 irq 20
Jan  4 20:36:20 toaster kernel: [    3.931145] pata-macio 0.00021000:ata-3: Activating pata-macio chipset KeyLargo ATA-3, Apple bus ID 1
Jan  4 20:36:20 toaster kernel: [    3.931755] scsi2 : pata_macio
Jan  4 20:36:20 toaster kernel: [    3.931934] ata3: PATA max MWDMA2 irq 21
Jan  4 20:36:20 toaster kernel: [    3.932265] mousedev: PS/2 mouse device common for all mice
Jan  4 20:36:20 toaster kernel: [    3.932694] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
Jan  4 20:36:20 toaster kernel: [    3.932832] PowerMac i2c bus pmu 2 registered
Jan  4 20:36:20 toaster kernel: [    3.932917] PowerMac i2c bus pmu 1 registered
Jan  4 20:36:20 toaster kernel: [    3.933005] PowerMac i2c bus mac-io 0 registered
Jan  4 20:36:20 toaster kernel: [    3.933028] i2c i2c-2: No i2c address for /pci@f2000000/mac-io@17/i2c@18000/i2c-modem
Jan  4 20:36:20 toaster kernel: [    3.933120] PowerMac i2c bus uni-n 1 registered
Jan  4 20:36:20 toaster kernel: [    3.933211] PowerMac i2c bus uni-n 0 registered
Jan  4 20:36:20 toaster kernel: [    3.933271] ledtrig-cpu: registered to indicate activity on CPUs
Jan  4 20:36:20 toaster kernel: [    3.933480] TCP: cubic registered
Jan  4 20:36:20 toaster kernel: [    3.933525] NET: Registered protocol family 10
Jan  4 20:36:20 toaster kernel: [    3.934189] mip6: Mobile IPv6
Jan  4 20:36:20 toaster kernel: [    3.934215] NET: Registered protocol family 17
Jan  4 20:36:20 toaster kernel: [    3.934238] mpls_gso: MPLS GSO support
Jan  4 20:36:20 toaster kernel: [    3.934744] registered taskstats version 1
Jan  4 20:36:20 toaster kernel: [    3.935372] input: PMU as /devices/virtual/input/input0
Jan  4 20:36:20 toaster kernel: [    3.935636] rtc-generic rtc-generic: setting system clock to 2016-01-05 01:36:14 UTC (1451957774)
Jan  4 20:36:20 toaster kernel: [    3.935709] PM: Hibernation image not present or could not be loaded.
Jan  4 20:36:20 toaster kernel: [    4.087872] Freeing unused kernel memory: 404K (c0679000 - c06de000)
Jan  4 20:36:20 toaster kernel: [    4.141494] random: systemd-udevd urandom read with 0 bits of entropy available
Jan  4 20:36:20 toaster kernel: [    4.215730] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
Jan  4 20:36:20 toaster kernel: [    4.215957] sd 0:0:0:0: [sda] Write Protect is off
Jan  4 20:36:20 toaster kernel: [    4.215974] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  4 20:36:20 toaster kernel: [    4.216030] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  4 20:36:20 toaster kernel: [    4.223905]  sda: [mac] sda1 sda2 sda3 sda4 sda5
Jan  4 20:36:20 toaster kernel: [    4.225193] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  4 20:36:20 toaster kernel: [    4.232641] sr0: scsi3-mmc drive: 46x/46x cd/rw xa/form2 cdda tray
Jan  4 20:36:20 toaster kernel: [    4.232677] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  4 20:36:20 toaster kernel: [    4.233154] sr 0:0:1:0: Attached scsi CD-ROM sr0
Jan  4 20:36:20 toaster kernel: [    4.243385] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  4 20:36:20 toaster kernel: [    4.243534] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jan  4 20:36:20 toaster kernel: [    4.257556] sungem.c:v1.0 David S. Miller <davem@redhat.com>
Jan  4 20:36:20 toaster kernel: [    4.258317] gem 0002:20:0f.0 eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:30:65:c1:28:32
Jan  4 20:36:20 toaster kernel: [    4.266045] firewire_ohci 0001:10:1a.0: enabling device (0010 -> 0012)
Jan  4 20:36:20 toaster kernel: [    4.296018] usbcore: registered new interface driver usbfs
Jan  4 20:36:20 toaster kernel: [    4.296096] usbcore: registered new interface driver hub
Jan  4 20:36:20 toaster kernel: [    4.301476] usbcore: registered new device driver usb
Jan  4 20:36:20 toaster kernel: [    4.306676] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  4 20:36:20 toaster kernel: [    4.309973] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  4 20:36:20 toaster kernel: [    4.310655] ehci-pci: EHCI PCI platform driver
Jan  4 20:36:20 toaster kernel: [    4.319153] firewire_ohci 0001:10:1a.0: added OHCI v1.0 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
Jan  4 20:36:20 toaster kernel: [    4.323482] ohci-pci: OHCI PCI platform driver
Jan  4 20:36:20 toaster kernel: [    4.323589] ohci-pci 0001:10:18.0: OHCI PCI host controller
Jan  4 20:36:20 toaster kernel: [    4.323621] ohci-pci 0001:10:18.0: new USB bus registered, assigned bus number 1
Jan  4 20:36:20 toaster kernel: [    4.323714] ohci-pci 0001:10:18.0: irq 27, io mem 0x80082000
Jan  4 20:36:20 toaster kernel: [    4.404229] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
Jan  4 20:36:20 toaster kernel: [    4.404270] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  4 20:36:20 toaster kernel: [    4.404290] usb usb1: Product: OHCI PCI host controller
Jan  4 20:36:20 toaster kernel: [    4.404304] usb usb1: Manufacturer: Linux 3.16.0-4-powerpc ohci_hcd
Jan  4 20:36:20 toaster kernel: [    4.404319] usb usb1: SerialNumber: 0001:10:18.0
Jan  4 20:36:20 toaster kernel: [    4.405108] hub 1-0:1.0: USB hub found
Jan  4 20:36:20 toaster kernel: [    4.405149] hub 1-0:1.0: 2 ports detected
Jan  4 20:36:20 toaster kernel: [    4.405558] ohci-pci 0001:10:19.0: OHCI PCI host controller
Jan  4 20:36:20 toaster kernel: [    4.405588] ohci-pci 0001:10:19.0: new USB bus registered, assigned bus number 2
Jan  4 20:36:20 toaster kernel: [    4.405701] ohci-pci 0001:10:19.0: irq 28, io mem 0x80081000
Jan  4 20:36:20 toaster kernel: [    4.478645] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jan  4 20:36:20 toaster kernel: [    4.478685] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  4 20:36:20 toaster kernel: [    4.478732] usb usb2: Product: OHCI PCI host controller
Jan  4 20:36:20 toaster kernel: [    4.478746] usb usb2: Manufacturer: Linux 3.16.0-4-powerpc ohci_hcd
Jan  4 20:36:20 toaster kernel: [    4.478761] usb usb2: SerialNumber: 0001:10:19.0
Jan  4 20:36:20 toaster kernel: [    4.480868] hub 2-0:1.0: USB hub found
Jan  4 20:36:20 toaster kernel: [    4.480917] hub 2-0:1.0: 2 ports detected
Jan  4 20:36:20 toaster kernel: [    4.581435] PM: Starting manual resume from disk
Jan  4 20:36:20 toaster kernel: [    4.581480] PM: Hibernation image partition 8:4 present
Jan  4 20:36:20 toaster kernel: [    4.581484] PM: Looking for hibernation image.
Jan  4 20:36:20 toaster kernel: [    4.582104] PM: Image not found (code -22)
Jan  4 20:36:20 toaster kernel: [    4.582112] PM: Hibernation image not present or could not be loaded.
Jan  4 20:36:20 toaster kernel: [    4.767098] usb 1-1: new full-speed USB device number 2 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    4.768259] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Jan  4 20:36:20 toaster kernel: [    4.819447] firewire_core 0001:10:1a.0: created device fw0: GUID 003065fffec12832, S400
Jan  4 20:36:20 toaster kernel: [    4.966138] usb 1-1: New USB device found, idVendor=05ac, idProduct=1101
Jan  4 20:36:20 toaster kernel: [    4.966163] usb 1-1: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Jan  4 20:36:20 toaster kernel: [    4.966179] usb 1-1: Product: Speakers
Jan  4 20:36:20 toaster kernel: [    4.966192] usb 1-1: Manufacturer: Apple Computer, Inc.
Jan  4 20:36:20 toaster kernel: [    4.966206] usb 1-1: SerialNumber: p4000
Jan  4 20:36:20 toaster kernel: [    5.143111] usb 1-2: new full-speed USB device number 3 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    5.300634] lp: driver loaded but no devices found
Jan  4 20:36:20 toaster kernel: [    5.323357] fuse init (API version 7.23)
Jan  4 20:36:20 toaster kernel: [    5.345331] usb 1-2: New USB device found, idVendor=05ac, idProduct=9119
Jan  4 20:36:20 toaster kernel: [    5.345377] usb 1-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jan  4 20:36:20 toaster kernel: [    5.346288] hub 1-2:1.0: USB hub found
Jan  4 20:36:20 toaster kernel: [    5.348138] hub 1-2:1.0: 3 ports detected
Jan  4 20:36:20 toaster kernel: [    5.407628] cfg80211: Calling CRDA to update world regulatory domain
Jan  4 20:36:20 toaster kernel: [    5.418467] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
Jan  4 20:36:20 toaster kernel: [    5.423596] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Jan  4 20:36:20 toaster kernel: [    5.423671] airport: Physical address 80030000
Jan  4 20:36:20 toaster kernel: [    5.703119] usb 2-1: new full-speed USB device number 2 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    5.910134] usb 2-1: New USB device found, idVendor=05ac, idProduct=1002
Jan  4 20:36:20 toaster kernel: [    5.910180] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  4 20:36:20 toaster kernel: [    5.910196] usb 2-1: Product: Hub in Apple Extended USB Keyboard
Jan  4 20:36:20 toaster kernel: [    5.910211] usb 2-1: Manufacturer: Alps Electric
Jan  4 20:36:20 toaster kernel: [    5.912293] hub 2-1:1.0: USB hub found
Jan  4 20:36:20 toaster kernel: [    5.914126] hub 2-1:1.0: 3 ports detected
Jan  4 20:36:20 toaster kernel: [    5.999138] usb 1-2.3: new low-speed USB device number 4 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    6.107148] usb 1-2.3: New USB device found, idVendor=05ac, idProduct=9219
Jan  4 20:36:20 toaster kernel: [    6.107197] usb 1-2.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan  4 20:36:20 toaster kernel: [    6.107216] usb 1-2.3: Product: Studio Display
Jan  4 20:36:20 toaster kernel: [    6.203119] usb 2-1.1: new full-speed USB device number 3 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    6.306126] usb 2-1.1: New USB device found, idVendor=05ac, idProduct=0204
Jan  4 20:36:20 toaster kernel: [    6.306174] usb 2-1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan  4 20:36:20 toaster kernel: [    6.306193] usb 2-1.1: Product: Apple Extended USB Keyboard
Jan  4 20:36:20 toaster kernel: [    6.306207] usb 2-1.1: Manufacturer: Alps Electric
Jan  4 20:36:20 toaster kernel: [    6.320820] [drm] Initialized drm 1.1.0 20060810
Jan  4 20:36:20 toaster kernel: [    6.387120] usb 2-1.3: new low-speed USB device number 4 using ohci-pci
Jan  4 20:36:20 toaster kernel: [    6.424463] random: nonblocking pool is initialized
Jan  4 20:36:20 toaster kernel: [    6.491157] usb 2-1.3: New USB device found, idVendor=045e, idProduct=0047
Jan  4 20:36:20 toaster kernel: [    6.491211] usb 2-1.3: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Jan  4 20:36:20 toaster kernel: [    6.491231] usb 2-1.3: Product: Microsoft 5-Button Mouse with IntelliEye(TM)
Jan  4 20:36:20 toaster kernel: [    6.491246] usb 2-1.3: Manufacturer: Microsoft
Jan  4 20:36:20 toaster kernel: [    6.627843] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
Jan  4 20:36:20 toaster kernel: [    6.628002] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
Jan  4 20:36:20 toaster kernel: [    6.628021] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
Jan  4 20:36:20 toaster kernel: [    6.645546] airport 0.00030000:radio: firmware: direct-loading firmware agere_sta_fw.bin
Jan  4 20:36:20 toaster kernel: [    6.725570] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
Jan  4 20:36:20 toaster kernel: [    6.725702] airport 0.00030000:radio: Station identity  001f:0002:0009:0030
Jan  4 20:36:20 toaster kernel: [    6.725721] airport 0.00030000:radio: Firmware determined as Lucent/Agere 9.48
Jan  4 20:36:20 toaster kernel: [    6.725741] airport 0.00030000:radio: Ad-hoc demo mode supported
Jan  4 20:36:20 toaster kernel: [    6.725755] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
Jan  4 20:36:20 toaster kernel: [    6.725774] airport 0.00030000:radio: WEP supported, 104-bit key
Jan  4 20:36:20 toaster kernel: [    6.725788] airport 0.00030000:radio: WPA-PSK supported
Jan  4 20:36:20 toaster kernel: [    6.854812] hidraw: raw HID events driver (C) Jiri Kosina
Jan  4 20:36:20 toaster kernel: [    7.021701] usbcore: registered new interface driver usbhid
Jan  4 20:36:20 toaster kernel: [    7.021744] usbhid: USB HID core driver
Jan  4 20:36:20 toaster kernel: [    7.248332] [drm] radeon kernel modesetting enabled.
Jan  4 20:36:20 toaster kernel: [    7.248612] radeon 0000:00:10.0: enabling device (0086 -> 0087)
Jan  4 20:36:20 toaster kernel: [    7.281107] [drm] initializing kernel modesetting (RV200 0x1002:0x5157 0x1002:0x5157).
Jan  4 20:36:20 toaster kernel: [    7.281163] [drm] Forcing AGP to PCI mode
Jan  4 20:36:20 toaster kernel: [    7.281191] [drm] register mmio base: 0x90000000
Jan  4 20:36:20 toaster kernel: [    7.281202] [drm] register mmio size: 65536
Jan  4 20:36:20 toaster kernel: [    7.281323] radeon 0000:00:10.0: Invalid ROM contents
Jan  4 20:36:20 toaster kernel: [    7.395281] [drm] Not an x86 BIOS ROM, not using.
Jan  4 20:36:20 toaster kernel: [    7.395349] [drm] Using device-tree clock info
Jan  4 20:36:20 toaster kernel: [    7.395380] radeon 0000:00:10.0: VRAM: 128M 0x0000000098000000 - 0x000000009FFFFFFF (32M used)
Jan  4 20:36:20 toaster kernel: [    7.395404] radeon 0000:00:10.0: GTT: 512M 0x0000000078000000 - 0x0000000097FFFFFF
Jan  4 20:36:20 toaster kernel: [    7.395470] [drm] Detected VRAM RAM=128M, BAR=128M
Jan  4 20:36:20 toaster kernel: [    7.395482] [drm] RAM width 128bits DDR
Jan  4 20:36:20 toaster kernel: [    7.403246] [TTM] Zone  kernel: Available graphics memory: 380618 kiB
Jan  4 20:36:20 toaster kernel: [    7.403280] [TTM] Zone highmem: Available graphics memory: 773834 kiB
Jan  4 20:36:20 toaster kernel: [    7.403294] [TTM] Initializing pool allocator
Jan  4 20:36:20 toaster kernel: [    7.403399] [drm] radeon: 32M of VRAM memory ready
Jan  4 20:36:20 toaster kernel: [    7.403413] [drm] radeon: 512M of GTT memory ready.
Jan  4 20:36:20 toaster kernel: [    7.403472] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jan  4 20:36:20 toaster kernel: [    7.412783] [drm] PCI GART of 512M enabled (table at 0x000000002F300000).
Jan  4 20:36:20 toaster kernel: [    7.447145] usb 1-1: Warning! Unlikely big volume range (=768), cval->res is probably wrong.
Jan  4 20:36:20 toaster kernel: [    7.447196] usb 1-1: [2] FU [PCM Playback Volume] ch = 2, val = -12288/0/16
Jan  4 20:36:20 toaster kernel: [    7.495588] input: Apple Computer, Inc. Speakers as /devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1:1.2/0003:05AC:1101.0001/input/input1
Jan  4 20:36:20 toaster kernel: [    7.496187] hid-generic 0003:05AC:1101.0001: input,hidraw0: USB HID v1.00 Device [Apple Computer, Inc. Speakers] on usb-0001:10:18.0-1/input2
Jan  4 20:36:20 toaster kernel: [    7.520139] usbcore: registered new interface driver snd-usb-audio
Jan  4 20:36:20 toaster kernel: [    7.528080] hid-generic 0003:05AC:9219.0002: hiddev0,hidraw1: USB HID v1.00 Device [Studio Display] on usb-0001:10:18.0-2.3/input0
Jan  4 20:36:20 toaster kernel: [    7.529196] input: Alps Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:05AC:0204.0003/input/input2
Jan  4 20:36:20 toaster kernel: [    7.534884] radeon 0000:00:10.0: WB disabled
Jan  4 20:36:20 toaster kernel: [    7.534925] radeon 0000:00:10.0: fence driver on ring 0 use gpu addr 0x0000000078000000 and cpu addr 0xef2ab000
Jan  4 20:36:20 toaster kernel: [    7.535006] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan  4 20:36:20 toaster kernel: [    7.535022] [drm] Driver supports precise vblank timestamp query.
Jan  4 20:36:20 toaster kernel: [    7.535113] [drm] radeon: irq initialized.
Jan  4 20:36:20 toaster kernel: [    7.535158] [drm] Loading R100 Microcode
Jan  4 20:36:20 toaster kernel: [    7.541776] hid-generic 0003:05AC:0204.0003: input,hidraw2: USB HID v1.10 Keyboard [Alps Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input0
Jan  4 20:36:20 toaster kernel: [    7.547098] radeon 0000:00:10.0: firmware: direct-loading firmware radeon/R100_cp.bin
Jan  4 20:36:20 toaster kernel: [    7.547582] [drm] radeon: ring at 0x0000000078001000
Jan  4 20:36:20 toaster kernel: [    7.547628] [drm] ring test succeeded in 0 usecs
Jan  4 20:36:20 toaster kernel: [    7.548007] [drm] ib test succeeded in 0 usecs
Jan  4 20:36:20 toaster kernel: [    7.555879] usbcore: registered new interface driver appledisplay
Jan  4 20:36:20 toaster kernel: [    7.578638] input: Alps Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:05AC:0204.0004/input/input3
Jan  4 20:36:20 toaster kernel: [    7.583767] hid-generic 0003:05AC:0204.0004: input,hidraw3: USB HID v1.10 Device [Alps Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input1
Jan  4 20:36:20 toaster kernel: [    7.588298] [drm] Connector Table: 1 (generic)
Jan  4 20:36:20 toaster kernel: [    7.588347] [drm] No TMDS info found in BIOS
Jan  4 20:36:20 toaster kernel: [    7.588367] [drm] No TV DAC info found in BIOS
Jan  4 20:36:20 toaster kernel: [    7.588789] [drm] Radeon Display Connectors
Jan  4 20:36:20 toaster kernel: [    7.588809] [drm] Connector 0:
Jan  4 20:36:20 toaster kernel: [    7.588818] [drm]   DVI-I-1
Jan  4 20:36:20 toaster kernel: [    7.588828] [drm]   HPD1
Jan  4 20:36:20 toaster kernel: [    7.588840] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jan  4 20:36:20 toaster kernel: [    7.588852] [drm]   Encoders:
Jan  4 20:36:20 toaster kernel: [    7.588862] [drm]     DFP1: INTERNAL_TMDS1
Jan  4 20:36:20 toaster kernel: [    7.588873] [drm]     CRT2: INTERNAL_DAC2
Jan  4 20:36:20 toaster kernel: [    7.588884] [drm] Connector 1:
Jan  4 20:36:20 toaster kernel: [    7.588893] [drm]   VGA-1
Jan  4 20:36:20 toaster kernel: [    7.588904] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Jan  4 20:36:20 toaster kernel: [    7.588916] [drm]   Encoders:
Jan  4 20:36:20 toaster kernel: [    7.588925] [drm]     CRT1: INTERNAL_DAC1
Jan  4 20:36:20 toaster kernel: [    7.588935] [drm] Connector 2:
Jan  4 20:36:20 toaster kernel: [    7.588944] [drm]   SVIDEO-1
Jan  4 20:36:20 toaster kernel: [    7.588953] [drm]   Encoders:
Jan  4 20:36:20 toaster kernel: [    7.588962] [drm]     TV1: INTERNAL_DAC2
Jan  4 20:36:20 toaster kernel: [    7.599173] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:045E:0047.0005/input/input4
Jan  4 20:36:20 toaster kernel: [    7.603544] hid-generic 0003:045E:0047.0005: input,hidraw4: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0001:10:19.0-1.3/input0
Jan  4 20:36:20 toaster kernel: [    7.744644] Adding 2439860k swap on /dev/sda4.  Priority:-1 extents:1 across:2439860k SSFS
Jan  4 20:36:20 toaster kernel: [    7.901413] [drm] fb mappable at 0x98040000
Jan  4 20:36:20 toaster kernel: [    7.901454] [drm] vram apper at 0x98000000
Jan  4 20:36:20 toaster kernel: [    7.901464] [drm] size 1884160
Jan  4 20:36:20 toaster kernel: [    7.901474] [drm] fb depth is 8
Jan  4 20:36:20 toaster kernel: [    7.901484] [drm]    pitch is 1792
Jan  4 20:36:20 toaster kernel: [    7.952926] Console: switching to colour frame buffer device 210x65
Jan  4 20:36:20 toaster kernel: [    7.974067] radeon 0000:00:10.0: fb0: radeondrmfb frame buffer device
Jan  4 20:36:20 toaster kernel: [    7.974191] radeon 0000:00:10.0: registered panic notifier
Jan  4 20:36:20 toaster kernel: [    7.974327] [drm] Initialized radeon 2.39.0 20080528 for 0000:00:10.0 on minor 0
Jan  4 20:36:20 toaster kernel: [    8.040380] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
Jan  4 20:36:20 toaster kernel: [    8.779627] sungem_phy: PHY ID: 1378e1, addr: 0
Jan  4 20:36:20 toaster kernel: [    8.779655] gem 0002:20:0f.0 eth0: Found Generic MII PHY
Jan  4 20:36:20 toaster kernel: [    8.780054] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  4 20:36:20 toaster kernel: [    9.337767] RPC: Registered named UNIX socket transport module.
Jan  4 20:36:20 toaster kernel: [    9.343297] RPC: Registered udp transport module.
Jan  4 20:36:20 toaster kernel: [    9.348640] RPC: Registered tcp transport module.
Jan  4 20:36:20 toaster kernel: [    9.353966] RPC: Registered tcp NFSv4.1 backchannel transport module.
Jan  4 20:36:20 toaster kernel: [    9.375969] FS-Cache: Loaded
Jan  4 20:36:20 toaster kernel: [    9.415476] FS-Cache: Netfs 'nfs' registered for caching
Jan  4 20:36:20 toaster kernel: [    9.461546] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jan  4 20:36:20 toaster dhclient: 
Jan  4 20:36:20 toaster ifup[427]: All rights reserved.
Jan  4 20:36:20 toaster ifup[427]: For info, please visit https://www.isc.org/software/dhcp/
Jan  4 20:36:20 toaster rpcbind[430]: Starting rpcbind daemon....
Jan  4 20:36:20 toaster systemd[1]: Started LSB: RPC portmapper replacement.
Jan  4 20:36:20 toaster systemd[1]: Starting RPC Port Mapper.
Jan  4 20:36:20 toaster systemd[1]: Reached target RPC Port Mapper.
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: NFS support files common to client and server...
Jan  4 20:36:20 toaster dhclient: Listening on LPF/eth0/00:30:65:c1:28:32
Jan  4 20:36:20 toaster dhclient: Sending on   LPF/eth0/00:30:65:c1:28:32
Jan  4 20:36:20 toaster dhclient: Sending on   Socket/fallback
Jan  4 20:36:20 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan  4 20:36:20 toaster ifup[427]: Listening on LPF/eth0/00:30:65:c1:28:32
Jan  4 20:36:20 toaster ifup[427]: Sending on   LPF/eth0/00:30:65:c1:28:32
Jan  4 20:36:20 toaster ifup[427]: Sending on   Socket/fallback
Jan  4 20:36:20 toaster ifup[427]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan  4 20:36:20 toaster console-setup[348]: Setting up console font and keymap...done.
Jan  4 20:36:20 toaster systemd[1]: Started LSB: Set console font and keymap.
Jan  4 20:36:20 toaster rpc.statd[461]: Version 1.2.8 starting
Jan  4 20:36:20 toaster sm-notify[462]: Version 1.2.8 starting
Jan  4 20:36:20 toaster nfs-common[453]: Starting NFS common utilities: statd idmapd.
Jan  4 20:36:20 toaster systemd[1]: Started LSB: NFS support files common to client and server.
Jan  4 20:36:20 toaster systemd[1]: Starting System Initialization.
Jan  4 20:36:20 toaster systemd[1]: Reached target System Initialization.
Jan  4 20:36:20 toaster systemd[1]: Starting Avahi mDNS/DNS-SD Stack Activation Socket.
Jan  4 20:36:20 toaster systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Jan  4 20:36:20 toaster systemd[1]: Starting D-Bus System Message Bus Socket.
Jan  4 20:36:20 toaster systemd[1]: Listening on D-Bus System Message Bus Socket.
Jan  4 20:36:20 toaster systemd[1]: Starting Daily Cleanup of Temporary Directories.
Jan  4 20:36:20 toaster systemd[1]: Started Daily Cleanup of Temporary Directories.
Jan  4 20:36:20 toaster systemd[1]: Starting Timers.
Jan  4 20:36:20 toaster systemd[1]: Reached target Timers.
Jan  4 20:36:20 toaster systemd[1]: Starting CUPS Printing Service Sockets.
Jan  4 20:36:20 toaster systemd[1]: Listening on CUPS Printing Service Sockets.
Jan  4 20:36:20 toaster systemd[1]: Starting Sockets.
Jan  4 20:36:20 toaster systemd[1]: Reached target Sockets.
Jan  4 20:36:20 toaster systemd[1]: Starting CUPS Printer Service Spool.
Jan  4 20:36:20 toaster systemd[1]: Started CUPS Printer Service Spool.
Jan  4 20:36:20 toaster systemd[1]: Starting Paths.
Jan  4 20:36:20 toaster systemd[1]: Reached target Paths.
Jan  4 20:36:20 toaster systemd[1]: Starting Basic System.
Jan  4 20:36:20 toaster systemd[1]: Reached target Basic System.
Jan  4 20:36:20 toaster systemd[1]: Starting Deferred execution scheduler...
Jan  4 20:36:20 toaster systemd[1]: Started Deferred execution scheduler.
Jan  4 20:36:20 toaster systemd[1]: Starting OpenBSD Secure Shell server...
Jan  4 20:36:20 toaster systemd[1]: Started OpenBSD Secure Shell server.
Jan  4 20:36:20 toaster systemd[1]: Starting Regular background program processing daemon...
Jan  4 20:36:20 toaster systemd[1]: Started Regular background program processing daemon.
Jan  4 20:36:20 toaster systemd[1]: Starting /etc/rc.local Compatibility...
Jan  4 20:36:20 toaster cron[478]: (CRON) INFO (pidfile fd = 3)
Jan  4 20:36:20 toaster systemd[1]: Started getty on tty2-tty6 if dbus and logind are not available.
Jan  4 20:36:20 toaster cron[478]: (CRON) INFO (Running @reboot jobs)
Jan  4 20:36:20 toaster systemd[1]: Starting Login Service...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: handle special hotkeys of Apple computers...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: exim Mail Transport Agent...
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: Emulate mouse buttons and mouse wheel...
Jan  4 20:36:20 toaster systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Jan  4 20:36:20 toaster systemd[1]: Starting D-Bus System Message Bus...
Jan  4 20:36:20 toaster pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration.
Jan  4 20:36:20 toaster systemd[1]: Started D-Bus System Message Bus.
Jan  4 20:36:20 toaster avahi-daemon[490]: Found user 'avahi' (UID 105) and group 'avahi' (GID 112).
Jan  4 20:36:20 toaster avahi-daemon[490]: Successfully dropped root privileges.
Jan  4 20:36:20 toaster avahi-daemon[490]: avahi-daemon 0.6.31 starting up.
Jan  4 20:36:20 toaster pbbuttonsd[482]: Starting pbbuttonsd:ERROR: Can't attach card 'default': No such file or directory
Jan  4 20:36:20 toaster pbbuttonsd: ERROR: Can't attach card 'default': No such file or directory
Jan  4 20:36:20 toaster pbbuttonsd: ERROR: Can't open mixer device [/dev/mixer]. No such file or directory
Jan  4 20:36:20 toaster pbbuttonsd: INFO: Soundsystem requested: auto, detected: ALSA and at least activated: none.
Jan  4 20:36:20 toaster pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf.
Jan  4 20:36:20 toaster pbbuttonsd[482]: ERROR: Can't open mixer device [/dev/mixer]. No such file or directory
Jan  4 20:36:20 toaster pbbuttonsd[482]: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 20:36:20 toaster pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 20:36:20 toaster pbbuttonsd[482]: .
Jan  4 20:36:20 toaster pbbuttonsd[482]: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12
Jan  4 20:36:20 toaster avahi-daemon[490]: Successfully called chroot().
Jan  4 20:36:20 toaster avahi-daemon[490]: Successfully dropped remaining capabilities.
Jan  4 20:36:20 toaster avahi-daemon[490]: No service file found in /etc/avahi/services.
Jan  4 20:36:20 toaster avahi-daemon[490]: Network interface enumeration completed.
Jan  4 20:36:20 toaster avahi-daemon[490]: Registering HINFO record with values 'PPC'/'LINUX'.
Jan  4 20:36:20 toaster avahi-daemon[490]: Server startup complete. Host name is toaster.local. Local service cookie is 3078308702.
Jan  4 20:36:20 toaster systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Jan  4 20:36:20 toaster systemd[1]: Starting LSB: SANE network scanner server...
Jan  4 20:36:20 toaster systemd[1]: Starting System Logging Service...
Jan  4 20:36:20 toaster systemd[1]: Starting CUPS Printing Service...
Jan  4 20:36:20 toaster saned[537]: saned disabled; edit /etc/default/saned.
Jan  4 20:36:20 toaster systemd[1]: Started CUPS Printing Service.
Jan  4 20:36:20 toaster systemd[1]: Starting Make remote CUPS printers available locally...
Jan  4 20:36:20 toaster pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' lauched but exitcode is not null
Jan  4 20:36:20 toaster systemd[1]: Started Make remote CUPS printers available locally.
Jan  4 20:36:20 toaster systemd[1]: Starting Permit User Sessions...
Jan  4 20:36:20 toaster rsyslogd-2007: action 'action 18' suspended, next retry is Mon Jan  4 20:36:50 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:36:21 toaster systemd[1]: Started System Logging Service.
Jan  4 20:36:21 toaster systemd[1]: Started /etc/rc.local Compatibility.
Jan  4 20:36:21 toaster systemd[1]: Started LSB: handle special hotkeys of Apple computers.
Jan  4 20:36:21 toaster systemd[1]: Started LSB: SANE network scanner server.
Jan  4 20:36:21 toaster systemd[1]: Started Permit User Sessions.
Jan  4 20:36:21 toaster systemd[1]: Started Login Service.
Jan  4 20:36:21 toaster systemd[1]: Starting SLiM Simple Login Manager...
Jan  4 20:36:21 toaster systemd[1]: Starting Getty on tty1...
Jan  4 20:36:21 toaster systemd[1]: Started Getty on tty1.
Jan  4 20:36:21 toaster systemd[1]: Starting Login Prompts.
Jan  4 20:36:21 toaster systemd[1]: Reached target Login Prompts.
Jan  4 20:36:21 toaster systemd[1]: Started SLiM Simple Login Manager.
Jan  4 20:36:21 toaster slim[646]: /usr/bin/X11/xauth:  file /var/run/slim.auth does not exist
Jan  4 20:36:21 toaster mouseemu[706]: mouseemu 0.15 (C) Colin Leroy <colin@colino.net>
Jan  4 20:36:21 toaster mouseemu[706]: using (0+68) as middle button, (0+87) as right button, (56) as scroll.
Jan  4 20:36:21 toaster mouseemu[487]: Starting mouse emulation daemon: mouseemu.
Jan  4 20:36:21 toaster systemd[1]: Started LSB: Emulate mouse buttons and mouse wheel.
Jan  4 20:36:21 toaster slim[646]: X.Org X Server 1.16.4
Jan  4 20:36:21 toaster slim[646]: Release Date: 2014-12-20
Jan  4 20:36:21 toaster slim[646]: X Protocol Version 11, Revision 0
Jan  4 20:36:21 toaster slim[646]: Build Operating System: Linux 3.2.0-4-powerpc64 ppc Debian
Jan  4 20:36:21 toaster slim[646]: Current Operating System: Linux toaster 3.16.0-4-powerpc #1 Debian 3.16.7-ckt20-1+deb8u1 (2015-12-14) ppc
Jan  4 20:36:21 toaster slim[646]: Kernel command line: root=UUID=11758325-78b3-4cc0-9cb2-d0cd860c4e5d ro radeon.modeset=1 video=radeonfb:off video=offb:off radeon.agpmode=-1
Jan  4 20:36:21 toaster slim[646]: Build Date: 11 February 2015  01:13:01AM
Jan  4 20:36:21 toaster slim[646]: xorg-server 2:1.16.4-1 (http://www.debian.org/support)
Jan  4 20:36:21 toaster slim[646]: Current version of pixman: 0.32.6
Jan  4 20:36:21 toaster slim[646]: Before reporting problems, check http://wiki.x.org
Jan  4 20:36:21 toaster slim[646]: to make sure that you have the latest version.
Jan  4 20:36:21 toaster slim[646]: Markers: (--) probed, (**) from config file, (==) default setting,
Jan  4 20:36:21 toaster slim[646]: (++) from command line, (!!) notice, (II) informational,
Jan  4 20:36:21 toaster slim[646]: (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Jan  4 20:36:21 toaster slim[646]: (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  4 20:36:21 2016
Jan  4 20:36:21 toaster slim[646]: (==) Using system config directory "/usr/share/X11/xorg.conf.d"
Jan  4 20:36:21 toaster slim[646]: (II) [KMS] Kernel modesetting enabled.
Jan  4 20:36:21 toaster kernel: [   11.187221] gem 0002:20:0f.0 eth0: Link is up at 100 Mbps, full-duplex
Jan  4 20:36:21 toaster kernel: [   11.187343] gem 0002:20:0f.0 eth0: Pause is disabled
Jan  4 20:36:21 toaster kernel: [   11.251529] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan  4 20:36:22 toaster exim4[484]: Starting MTA: exim4.
Jan  4 20:36:22 toaster systemd[1]: Started LSB: exim Mail Transport Agent.
Jan  4 20:36:22 toaster systemd[1]: Starting Multi-User System.
Jan  4 20:36:22 toaster systemd[1]: Reached target Multi-User System.
Jan  4 20:36:22 toaster systemd[1]: Starting Graphical Interface.
Jan  4 20:36:22 toaster systemd[1]: Reached target Graphical Interface.
Jan  4 20:36:22 toaster systemd[1]: Starting Update UTMP about System Runlevel Changes...
Jan  4 20:36:22 toaster systemd[1]: Started Update UTMP about System Runlevel Changes.
Jan  4 20:36:22 toaster systemd[1]: Startup finished in 4.928s (kernel) + 6.805s (userspace) = 11.734s.
Jan  4 20:36:22 toaster mouseemu[715]: Trying to open /dev/uinput...
Jan  4 20:36:22 toaster mouseemu[715]:  ok.
Jan  4 20:36:22 toaster kernel: [   11.995441] input: Mouseemu virtual keyboard as /devices/virtual/input/input5
Jan  4 20:36:22 toaster kernel: [   11.995963] input: Mouseemu virtual mouse as /devices/virtual/input/input6
Jan  4 20:36:22 toaster mouseemu[715]: Trying to open /dev/uinput...
Jan  4 20:36:22 toaster mouseemu[715]:  ok.
Jan  4 20:36:23 toaster avahi-daemon[490]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:65ff:fec1:2832.
Jan  4 20:36:23 toaster avahi-daemon[490]: New relevant interface eth0.IPv6 for mDNS.
Jan  4 20:36:23 toaster avahi-daemon[490]: Registering new address record for fe80::230:65ff:fec1:2832 on eth0.*.
Jan  4 20:36:25 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  4 20:36:25 toaster ifup[427]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  4 20:36:26 toaster dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  4 20:36:26 toaster dhclient: DHCPOFFER from 192.168.0.1
Jan  4 20:36:26 toaster ifup[427]: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  4 20:36:26 toaster ifup[427]: DHCPOFFER from 192.168.0.1
Jan  4 20:36:27 toaster dhclient: DHCPACK from 192.168.0.1
Jan  4 20:36:27 toaster ifup[427]: DHCPACK from 192.168.0.1
Jan  4 20:36:27 toaster avahi-daemon[490]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.113.
Jan  4 20:36:27 toaster avahi-daemon[490]: New relevant interface eth0.IPv4 for mDNS.
Jan  4 20:36:27 toaster avahi-daemon[490]: Registering new address record for 192.168.0.113 on eth0.IPv4.
Jan  4 20:36:27 toaster dhclient: bound to 192.168.0.113 -- renewal in 20550 seconds.
Jan  4 20:36:27 toaster ifup[427]: bound to 192.168.0.113 -- renewal in 20550 seconds.
Jan  4 20:36:36 toaster systemd[1]: Starting user-1000.slice.
Jan  4 20:36:36 toaster systemd[1]: Created slice user-1000.slice.
Jan  4 20:36:36 toaster systemd[1]: Starting Session 1 of user kyle.
Jan  4 20:36:36 toaster systemd[1]: Started Session 1 of user kyle.
Jan  4 20:36:36 toaster systemd[1]: Starting User Manager for UID 1000...
Jan  4 20:36:36 toaster systemd[870]: Starting Paths.
Jan  4 20:36:36 toaster systemd[870]: Reached target Paths.
Jan  4 20:36:36 toaster systemd[870]: Starting Timers.
Jan  4 20:36:36 toaster systemd[870]: Reached target Timers.
Jan  4 20:36:36 toaster systemd[870]: Starting Sockets.
Jan  4 20:36:36 toaster systemd[870]: Reached target Sockets.
Jan  4 20:36:36 toaster systemd[870]: Starting Basic System.
Jan  4 20:36:36 toaster systemd[870]: Reached target Basic System.
Jan  4 20:36:36 toaster systemd[870]: Starting Default.
Jan  4 20:36:36 toaster systemd[870]: Reached target Default.
Jan  4 20:36:36 toaster systemd[870]: Startup finished in 35ms.
Jan  4 20:36:36 toaster systemd[1]: Started User Manager for UID 1000.
Jan  4 20:36:36 toaster slim[646]: /usr/bin/X11/xauth:  file /home/kyle/.Xauthority does not exist
Jan  4 20:36:38 toaster org.a11y.Bus[910]: Activating service name='org.a11y.atspi.Registry'
Jan  4 20:36:39 toaster org.a11y.Bus[910]: Successfully activated service 'org.a11y.atspi.Registry'
Jan  4 20:36:39 toaster org.a11y.atspi.Registry[939]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jan  4 20:41:20 toaster rsyslogd-2007: action 'action 18' suspended, next retry is Mon Jan  4 20:41:50 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:46:44 toaster slim[646]: (EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
Jan  4 20:46:44 toaster rsyslogd-2007: action 'action 18' suspended, next retry is Mon Jan  4 20:47:14 2016 [try http://www.rsyslog.com/e/2007 ]
Jan  4 20:46:44 toaster slim[646]: (EE)
Jan  4 20:46:44 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:44 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:44 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x2a0) [0x2095dc00]
Jan  4 20:46:44 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:44 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:44 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:44 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:44 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:44 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:44 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:44 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:44 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:44 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:44 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:44 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:44 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:44 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:44 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:44 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:44 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:44 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:44 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:44 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:44 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:44 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:44 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:44 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:44 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:44 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:44 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:44 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:44 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:44 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:44 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:44 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:44 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:44 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:44 toaster slim[646]: (EE)
Jan  4 20:46:44 toaster slim[646]: (EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
Jan  4 20:46:44 toaster slim[646]: (EE) [mi] mieq is *NOT* the cause.  It is a victim.
Jan  4 20:46:45 toaster slim[646]: (EE) [mi] EQ overflow continuing.  100 events have been dropped.
Jan  4 20:46:45 toaster slim[646]: (EE)
Jan  4 20:46:45 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:45 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:45 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:45 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:45 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:45 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:45 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:45 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:45 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:45 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:45 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:45 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:45 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:45 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:45 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:45 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:45 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:45 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:45 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:45 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:45 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:45 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:45 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:45 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:45 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:45 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:45 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:45 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:45 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:45 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:45 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:45 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:45 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:45 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:45 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:45 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:45 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:45 toaster slim[646]: (EE)
Jan  4 20:46:46 toaster slim[646]: (EE) [mi] EQ overflow continuing.  200 events have been dropped.
Jan  4 20:46:46 toaster slim[646]: (EE)
Jan  4 20:46:46 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:46 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:46 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:46 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:46 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:46 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:46 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:46 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:46 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:46 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:46 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:46 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:47 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:47 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:47 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:47 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:47 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:47 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:47 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:47 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:47 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:47 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:47 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:47 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:47 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:47 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:47 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:47 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:47 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:47 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:47 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:47 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:47 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:47 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:47 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:47 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:47 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:47 toaster slim[646]: (EE)
Jan  4 20:46:47 toaster slim[646]: (EE) [mi] EQ overflow continuing.  300 events have been dropped.
Jan  4 20:46:47 toaster slim[646]: (EE)
Jan  4 20:46:47 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:47 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:47 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:47 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:47 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:47 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:47 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:47 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:47 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:47 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:47 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:47 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:47 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:47 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:47 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:47 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:47 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:47 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:47 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:47 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:47 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:47 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:47 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:47 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:47 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:47 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:47 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:47 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:47 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:47 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:47 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:47 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:47 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:47 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:47 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:47 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:47 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:47 toaster slim[646]: (EE)
Jan  4 20:46:48 toaster slim[646]: (EE) [mi] EQ overflow continuing.  400 events have been dropped.
Jan  4 20:46:48 toaster slim[646]: (EE)
Jan  4 20:46:48 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:48 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:48 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:48 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:48 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:48 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:48 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:48 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:48 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:48 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:48 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:48 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:48 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:48 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:48 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:48 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:48 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:48 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:48 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:48 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:48 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:48 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:48 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:48 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:48 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:48 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:48 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:48 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:48 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:48 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:48 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:48 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:48 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:48 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:48 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:48 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:48 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:48 toaster slim[646]: (EE)
Jan  4 20:46:50 toaster slim[646]: (EE) [mi] EQ overflow continuing.  500 events have been dropped.
Jan  4 20:46:50 toaster slim[646]: (EE)
Jan  4 20:46:50 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:50 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:50 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:50 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:50 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:50 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:50 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:50 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:50 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:50 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:50 toaster slim[646]: (EE) 9: /usr/bin/X11/X (0x20776000+0x210920) [0x20986920]
Jan  4 20:46:50 toaster slim[646]: (EE) 10: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:50 toaster slim[646]: (EE) 11: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:50 toaster slim[646]: (EE) 12: ?? [0x77]
Jan  4 20:46:50 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:50 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:50 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:50 toaster slim[646]: (EE) 16: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:50 toaster slim[646]: (EE) 17: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:50 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:50 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:50 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:50 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:50 toaster slim[646]: (EE) 22: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:50 toaster slim[646]: (EE) 23: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:50 toaster slim[646]: (EE) 24: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:50 toaster slim[646]: (EE) 25: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:50 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:50 toaster slim[646]: (EE) 27: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:50 toaster slim[646]: (EE) 28: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:50 toaster slim[646]: (EE) 29: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:50 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:50 toaster slim[646]: (EE) 31: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:50 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:50 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:50 toaster slim[646]: (EE) 34: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:50 toaster slim[646]: (EE) 35: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:50 toaster slim[646]: (EE) 36: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:50 toaster slim[646]: (EE) 37: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:50 toaster slim[646]: (EE)
Jan  4 20:46:51 toaster slim[646]: (EE) [mi] EQ overflow continuing.  600 events have been dropped.
Jan  4 20:46:51 toaster slim[646]: (EE)
Jan  4 20:46:51 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:51 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:51 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:51 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:51 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:51 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:51 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:51 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:51 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:51 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:51 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:51 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:51 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:51 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:51 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:51 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:51 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:51 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:51 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:51 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:51 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:51 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:51 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:51 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:51 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:51 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:51 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:51 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:51 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:51 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:51 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:51 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:51 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:51 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:51 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:51 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:51 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:51 toaster slim[646]: (EE)
Jan  4 20:46:56 toaster slim[646]: (EE) [mi] EQ overflow continuing.  700 events have been dropped.
Jan  4 20:46:56 toaster slim[646]: (EE)
Jan  4 20:46:56 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:56 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:56 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:56 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:56 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostMotionEventM+0x408) [0x20832838]
Jan  4 20:46:56 toaster slim[646]: (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x59d0) [0x1f1a69d0]
Jan  4 20:46:56 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:56 toaster slim[646]: (EE) 6: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:56 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:56 toaster slim[646]: (EE) 8: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:56 toaster slim[646]: (EE) 9: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:56 toaster slim[646]: (EE) 10: ?? [0x77]
Jan  4 20:46:56 toaster slim[646]: (EE) 11: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:56 toaster slim[646]: (EE) 12: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:56 toaster slim[646]: (EE) 13: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:56 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:56 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:56 toaster slim[646]: (EE) 16: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:56 toaster slim[646]: (EE) 17: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:56 toaster slim[646]: (EE) 18: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:56 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:56 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:56 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:56 toaster slim[646]: (EE) 22: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:56 toaster slim[646]: (EE) 23: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:56 toaster slim[646]: (EE) 24: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:56 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:56 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:56 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:56 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:56 toaster slim[646]: (EE) 29: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:56 toaster slim[646]: (EE) 30: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:56 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:56 toaster slim[646]: (EE) 32: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:56 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:56 toaster slim[646]: (EE) 34: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:56 toaster slim[646]: (EE) 35: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:56 toaster slim[646]: (EE)
Jan  4 20:46:57 toaster slim[646]: (EE) [mi] EQ overflow continuing.  800 events have been dropped.
Jan  4 20:46:57 toaster slim[646]: (EE)
Jan  4 20:46:57 toaster slim[646]: (EE) Backtrace:
Jan  4 20:46:57 toaster slim[646]: (EE) 0: /usr/bin/X11/X (xorg_backtrace+0x6c) [0x20980ebc]
Jan  4 20:46:57 toaster slim[646]: (EE) 1: /usr/bin/X11/X (mieqEnqueue+0x100) [0x2095da60]
Jan  4 20:46:57 toaster slim[646]: (EE) 2: /usr/bin/X11/X (QueuePointerEvents+0x90) [0x207ecc90]
Jan  4 20:46:57 toaster slim[646]: (EE) 3: /usr/bin/X11/X (xf86PostButtonEventM+0xc0) [0x20832df0]
Jan  4 20:46:57 toaster slim[646]: (EE) 4: /usr/bin/X11/X (xf86PostButtonEvent+0x12c) [0x20832f6c]
Jan  4 20:46:57 toaster slim[646]: (EE) 5: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x576c) [0x1f1a676c]
Jan  4 20:46:57 toaster slim[646]: (EE) 6: /usr/lib/xorg/modules/input/evdev_drv.so (0x1f1a1000+0x5fd4) [0x1f1a6fd4]
Jan  4 20:46:57 toaster slim[646]: (EE) 7: /usr/bin/X11/X (0x20776000+0xa7e08) [0x2081de08]
Jan  4 20:46:57 toaster slim[646]: (EE) 8: /usr/bin/X11/X (0x20776000+0xdc1bc) [0x208521bc]
Jan  4 20:46:57 toaster slim[646]: (EE) 9: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:57 toaster slim[646]: (EE) 10: /usr/bin/X11/X (0x20776000+0x210920) [0x20986920]
Jan  4 20:46:57 toaster slim[646]: (EE) 11: linux-vdso32.so.1 (__kernel_sigtramp32+0x0) [0x100394]
Jan  4 20:46:57 toaster slim[646]: (EE) 12: /lib/powerpc-linux-gnu/libc.so.6 (ioctl+0xec) [0x2029125c]
Jan  4 20:46:57 toaster slim[646]: (EE) 13: ?? [0x77]
Jan  4 20:46:57 toaster slim[646]: (EE) 14: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmIoctl+0x54) [0x205b9fa4]
Jan  4 20:46:57 toaster slim[646]: (EE) 15: /usr/lib/powerpc-linux-gnu/libdrm.so.2 (drmCommandWrite+0x38) [0x205bdd58]
Jan  4 20:46:57 toaster slim[646]: (EE) 16: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x19d8) [0x1f8f59d8]
Jan  4 20:46:57 toaster slim[646]: (EE) 17: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x1f8f4000+0x1c98) [0x1f8f5c98]
Jan  4 20:46:57 toaster slim[646]: (EE) 18: /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (radeon_bo_map+0x20) [0x1f8f78f0]
Jan  4 20:46:57 toaster slim[646]: (EE) 19: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x1f922000+0x2d4d0) [0x1f94f4d0]
Jan  4 20:46:57 toaster slim[646]: (EE) 20: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x6070) [0x1f84e070]
Jan  4 20:46:57 toaster slim[646]: (EE) 21: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x8e48) [0x1f850e48]
Jan  4 20:46:57 toaster slim[646]: (EE) 22: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x4d80) [0x1f84cd80]
Jan  4 20:46:57 toaster slim[646]: (EE) 23: /usr/lib/xorg/modules/libexa.so (0x1f848000+0x12818) [0x1f85a818]
Jan  4 20:46:57 toaster slim[646]: (EE) 24: /usr/lib/xorg/modules/libexa.so (0x1f848000+0xbe74) [0x1f853e74]
Jan  4 20:46:57 toaster slim[646]: (EE) 25: /usr/bin/X11/X (0x20776000+0x17f0ac) [0x208f50ac]
Jan  4 20:46:57 toaster slim[646]: (EE) 26: /usr/bin/X11/X (miPaintWindow+0x264) [0x2095ebd4]
Jan  4 20:46:57 toaster slim[646]: (EE) 27: /usr/bin/X11/X (miWindowExposures+0x25c) [0x2095f5cc]
Jan  4 20:46:57 toaster slim[646]: (EE) 28: /usr/bin/X11/X (0x20776000+0xc90ec) [0x2083f0ec]
Jan  4 20:46:57 toaster slim[646]: (EE) 29: /usr/bin/X11/X (miHandleValidateExposures+0xb0) [0x20977900]
Jan  4 20:46:57 toaster slim[646]: (EE) 30: /usr/bin/X11/X (miMoveWindow+0x240) [0x20977bf0]
Jan  4 20:46:57 toaster slim[646]: (EE) 31: /usr/bin/X11/X (0x20776000+0x10d580) [0x20883580]
Jan  4 20:46:57 toaster slim[646]: (EE) 32: /usr/bin/X11/X (ConfigureWindow+0x5f0) [0x20808c90]
Jan  4 20:46:57 toaster slim[646]: (EE) 33: /usr/bin/X11/X (0x20776000+0x5185c) [0x207c785c]
Jan  4 20:46:57 toaster slim[646]: (EE) 34: /usr/bin/X11/X (0x20776000+0x58b8c) [0x207ceb8c]
Jan  4 20:46:57 toaster slim[646]: (EE) 35: /usr/bin/X11/X (0x20776000+0x5da08) [0x207d3a08]
Jan  4 20:46:57 toaster slim[646]: (EE) 36: /usr/bin/X11/X (0x20776000+0x42bb4) [0x207b8bb4]
Jan  4 20:46:57 toaster slim[646]: (EE) 37: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23274) [0x201c7274]
Jan  4 20:46:57 toaster slim[646]: (EE) 38: /lib/powerpc-linux-gnu/libc.so.6 (0x201a4000+0x23434) [0x201c7434]
Jan  4 20:46:57 toaster slim[646]: (EE)



```


I was wondering about the "firmware: failed to load radeon" on line 553-ish. The "overflow" stuff is when the desktop goes south.

---

### Post by kyle69 on 2016-01-07
I ended up trying a default debian/xfce from the install disk and seems to be working like a champ. I didn't install the linux nonfree firmware after the install. Also no yaboot parameters. I don't think that I'm getting 3d accel but I don't want games, so perhaps this is not an issue. I think I'm getting KMS by default but not sure, still trying to decipher the logs. I am much more content with the overall cpu activity, seems reasonably stable- I attached a screenshot-

-kyle

---

### Post by este.el.paz on 2016-01-07
@kyle:

That's great, main thing is finding what works for your system . . . and then go with that . . . good work.

e...

---

### Post by abtabt on 2016-01-07
> **kyle69 said:**
> I ended up trying a default debian/xfce from the install disk and seems to be working like a champ. I didn't install the linux nonfree firmware after the install. Also no yaboot parameters. I don't think that I'm getting 3d accel but I don't want games, so perhaps this is not an issue. I think I'm getting KMS by default but not sure, still trying to decipher the logs. I am much more content with the overall cpu activity, seems reasonably stable- I attached a screenshot-

-kyle

your install of  Lubuntu 14.04 ,have you add or change (i think i see Slim manager in the log ???)

version DEBIAN ??  

you can see it in Xorg.0.log ( maybe you use fbdev in debian ) 

have you any splash i debian ???

glxinfo     ( show some info )

a tip
htop is like top but more useful

if you have a spare disk like Firewire disk , usb works too but Cube have 1.1 or is it 2.0 ,you can try the system before you install 

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

Persistent Live USB 

 (but you can use FW too, i use this before install everyting, i download ,install,change files try out and the fine thing 
it stays on the FW disk shutdown and boot up next day and the work is there , cd/dvd is slow ,usb is slow 1.1, firewire is fast like hd 

have a nice day with Debian

---

### Post by kyle69 on 2016-01-07
@abtabt- I switched from lubu to the debian/jessie setup at post #7 because I wanted test it with something different, and to try the ppc luddite's setup. However, I got the exact same crashes. I'm now pretty sure it has something to do with the nonfree radeon driver but could be wrong. 

I checked out the xfce desktop and it looked nice to me, so I started going down that path, but I totally hosed it with some unnecessary packages. So I started fresh with another debian install and checked the xfce option. When I booted to the desktop I realized I had forgot the yaboot parameters, but the desktop worked fine. I then decided to leave out the nonfree drivers and see how it worked. 2 hours later it still hadn't crashed.

It now runs the glxgears although it doesn't appear to be using 3d acceleration. I was a little confused by what driver it's using but it was late and too much wine... :wink:
 
It wasn't recognizing the airport card either, not sure about sound. I'll take another crack at it later tonight. Thanks for the htop trick, will check it out-

---

