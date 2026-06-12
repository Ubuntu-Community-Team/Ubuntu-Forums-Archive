---
title: "Low Display on G3 running Ubuntu 10.04"
date: 2010-07-09
forum: Apple Hardware Users
---

### Post by mathieub on 2010-07-09
Hi This is First Post   :o    but I may as well make it a good one, I have been reading others experiences of similar Low-Display 800x600 minimal color issues on G4 and other PPC computers,  Thought I had it close but still can't get it really gworking as it should, I believe it is all to do with the framebuffers (that don't exist and I don't know how to make these files and keep them on reboot. mine is a really old G3 with the Slot Load R128 Rage ATI graphics, 40 GB HDD, 256 MB RAM,740/750 processor. this is the result of  *[FONT=Arial][SIZE=4][COLOR=Red]my lspci -vv  query on the graphics:[/COLOR][/SIZE][/FONT]*

0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS
    Subsystem: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 255 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 48
    Region 0: Memory at 94000000 (32-bit, prefetchable) [size=64M]
    Region 1: I/O ports at 0400 [disabled] [size=256]
    Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
    Expansion ROM at 90020000 [disabled] [size=128K]
    Capabilities: <access denied>

*[FONT=Arial][SIZE=3][COLOR=Red]this is my xorg.conf file[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=4][COLOR=Red] attached[/COLOR][/SIZE][/FONT]*
:



Attached Log below in next post thanks.....:confused:
So does anyone want to help sort this for me please:D

---

### Post by mathieub on 2010-07-10
found out how to attach the log, here is a new one, it doesn't have the errors in it but it still runs in Low Display mode...

---

### Post by linuxopjemac on 2010-07-10
I think this machine only handles 800x600 and 640x480 right, or also 1024x768?

give me the output of:
```
cvt 1024 768
cvt 800 600
cvt 640 480
```

please You have to add them to your xorg.conf file in the Monitor Section.

PS which iMac G3 do you have ? Can you give me the link in everymac.com pls ?

---

### Post by mathieub on 2010-07-10
[SIZE=2]It is all working now, found a site with a whole bunch of parameters which seemed to improve almost everything  not 100% sure how but I have managed to get it to run at 1024 x 768 24 bit depth
I did add the video parameters into the append line in the image section of the [/SIZE][SIZE=2] yaboot.conf in the bootstrap disk

[/SIZE][SIZE=2]append="quiet nosplash  video=VGA-1:e"

 which may have fixed it too

I have attached my xorg.conf file for anyone else wanting to get one of these old girls working with a current version of Ubuntu PPC running the Linux  2.6.32-22-powerpc [/SIZE][SIZE=2]Kernel

[/SIZE][SIZE=2]I must admit it could do with some more RAM but apart from that it goes well.

Here is the CVT results it may help someone else

:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

 cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

cvt 600 400
# 600x400 59.63 Hz (CVT) hsync: 24.87 kHz; pclk: 18.50 MHz
Modeline "600x400_60.00"   18.50  600 616 672 744  400 403 413 417 -hsync +vsync



[/SIZE]

---

### Post by mathieub on 2010-07-13
Unbelieveable,  I need help again 
HDD failure and a rebuild and a start from scratch but back to Low graphics again
I have fitted a 40 GB HDD and 512 MB RAM whilst the e a fitted a new BIOS battery as I think a few of the issues were as a result of that battery being flat.
[COLOR=Red]
this is the model of the G3[/COLOR]

[http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html](http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html)
[COLOR=Red]
my cvt results are as follows[/COLOR] 

imac@imac-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
imac@imac-desktop:~$ 
imac@imac-desktop:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
imac@imac-desktop:~$ 
imac@imac-desktop:~$ cvt 600 480
# 600x480 59.81 Hz (CVT 0.29M4) hsync: 29.91 kHz; pclk: 22.25 MHz
Modeline "600x480_60.00"   22.25  600 616 672 744  480 483 490 500 -hsync +vsync


  and xorg.0.[ATTACH]163284[/ATTACH]log is attached

---

### Post by linuxopjemac on 2010-07-13
give me the output of:
```
cvt 1024 768 75
cvt 800 600 95
cvt 640 480 117
```

---

### Post by mathieub on 2010-07-14
Here you go

 cvt 1024 768 75
# 1024x768 74.90 Hz (CVT 0.79M3) hsync: 60.29 kHz; pclk: 82.00 MHz
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync

cvt 800 600 95
# 800x600 94.77 Hz (CVT) hsync: 60.37 kHz; pclk: 63.75 MHz
Modeline "800x600_95.00"   63.75  800 848 928 1056  600 603 607 637 -hsync +vsync

cvt 640 480 117
# 640x480 116.33 Hz (CVT) hsync: 60.14 kHz; pclk: 51.00 MHz
Modeline "640x480_117.00"   51.00  640 680 744 848  480 483 487 517 -hsync +vsync

Thanks (sorry About the time difference, BTW I have relatives in Limburg Holland)

---

### Post by linuxopjemac on 2010-07-14
I am from Limburg originally :)

Try this xorg.conf file (replace it in /etc/X11/xorg.conf)

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
Option "NoInt10" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 30-80
VertRefresh 75-117
# 1024x768 74.90 Hz (CVT 0.79M3) hsync: 60.29 kHz; pclk: 82.00 MHz
Modeline "1024x768_75.00" 82.00 1024 1088 1192 1360 768 771 775 805 -hsync +vsync
# 800x600 94.77 Hz (CVT) hsync: 60.37 kHz; pclk: 63.75 MHz
Modeline "800x600_95.00" 63.75 800 848 928 1056 600 603 607 637 -hsync +vsync
# 640x480 116.33 Hz (CVT) hsync: 60.14 kHz; pclk: 51.00 MHz
Modeline "640x480_117.00" 51.00 640 680 744 848 480 483 487 517 -hsync +vsync
Option "PreferredMode" "800x600_95.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection

```

---

### Post by mathieub on 2010-07-14
Thanks I will give that a go now, I will be back shortly or maybe a while....depending on boot method....
My family are originally in Neer and Buggenum mainly.. small world huh!:D

---

### Post by linuxopjemac on 2010-07-14
If it does not work give me the output of:

```
sudo cat /var/log/Xorg.0.log
```

PS I have an aunt in Neer

---

### Post by mathieub on 2010-07-14
It is better but still very limited colour range 8 bit maybe and the issue looks to relate to the fact there just aren't any fb devices except for fb0 it is either that or the  

BIOS @ 0x????????/131072


sudo cat /var/log/Xorg.0.log


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux imac-desktop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly nofb 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 14 08:11:41 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "iMac"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:16:0) 1002:5052:1002:5052 ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "true"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
    (you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

PS 
[SIZE=2][COLOR=Lime]I hope she is not related to us Boonen's (your aunt I mean.. which I suppose means you too.)[/COLOR][/SIZE]

---

### Post by linuxopjemac on 2010-07-14
ok, I have heard other people having trouble too with early iMacs. I never knew why, maybe because the framebuffer device is no longer supported by the new Xorg, maybe someone else can shed a light on that. Let's try to let ati do its work automatically, without forcing it to use a framebuffer device. Change the device section into:

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "NoInt10" "true"
EndSection
```

---

### Post by linuxopjemac on 2010-07-14
If that does not solve the problem, try this:

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "false"
Option "NoInt10" "true"
EndSection
```

---

### Post by mathieub on 2010-07-14
Nothing seems to have changed, maybe if I change the color depth default to 16 instead of 24 it may behave better, can you tell me if that is possible here is the latest log, it doesn't look any different...
sudo cat /var/log/Xorg.0.log
[sudo] password for imac: 

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux imac-desktop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly nofb 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 14 08:43:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "iMac"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:16:0) 1002:5052:1002:5052 ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
    (you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log, 
[SIZE=4][COLOR=Red]


and here is the current xorg.con[/COLOR][/SIZE][SIZE=4][COLOR=Red]f[/COLOR][/SIZE]

sudo cat xorg.conf
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "NoInt10" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 30-80
VertRefresh 75-117
# 1024x768 74.90 Hz (CVT 0.79M3) hsync: 60.29 kHz; pclk: 82.00 MHz
Modeline "1024x768_75.00" 82.00 1024 1088 1192 1360 768 771 775 805 -hsync +vsync
# 800x600 94.77 Hz (CVT) hsync: 60.37 kHz; pclk: 63.75 MHz
Modeline "800x600_95.00" 63.75 800 848 928 1056 600 603 607 637 -hsync +vsync
# 640x480 116.33 Hz (CVT) hsync: 60.14 kHz; pclk: 51.00 MHz
Modeline "640x480_117.00" 51.00 640 680 744 848 480 483 487 517 -hsync +vsync
Option "PreferredMode" "800x600_95.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by linuxopjemac on 2010-07-14
try first with:
```

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "false"
Option "NoInt10" "true"
EndSection
```

---

### Post by mathieub on 2010-07-14
That didn't work at all, it loaded the OS but no X, I assume it uses fb0 and if you tell it not to use framebuffers even that fb0  one is not available....

Running it off live cd again ATM just to send you the message and replace the xorg.conf with the original 
 I should use two pcs but too lazy to fire another one up....
 is there a way I can test X without having to reboot,

or even make these device files with makedev or mknod or something, 
 
Thanks

Mat:)

---

### Post by linuxopjemac on 2010-07-14
you don't need to reboot
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
If you are xubuntu it might be xdm instead of gdm, not sure.

---

### Post by linuxopjemac on 2010-07-14
What I can suggest then is to go back one step and take 16 or 15 bit color as default, and delete the 24 bit section.

---

