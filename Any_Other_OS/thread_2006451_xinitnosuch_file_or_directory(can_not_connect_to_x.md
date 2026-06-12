---
title: "xinit:nosuch file or directory(can not connect to x server)"
date: 2012-06-19
forum: Any Other OS
---

### Post by vykuntamsrinivas on 2012-06-19
hi,i hav e been using  backtrack5r2 for 1 month.As my system is old or  not good, drivers were not installed by default...yesterday i installed  s3g graphics driver from [http://drivers.s3graphics.com/en/dow...nux/Readme.txt](http://drivers.s3graphics.com/en/dow...nux/Readme.txt)   site and after reboot i was logged in to tty but when i typed startx i   ddn get my desktop insted showing an error: Fatal server error:no  screens found... Here i am pasting the "/var/log/Xorg.0.log" file info:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.6 root=UUID=cc082daa-e797-48b6-8dee-f7ff1419a222 ro text splash vga=791
Build Date: 25 February 2012  06:59:39AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 19 10:44:49 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen1" (0)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "VideoCard1"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) Option "IgnoreABI" "True"
(**) Ignoring ABI Version
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
(**) Extension "Composite" is enabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse1
(WW) Disabling Keyboard1
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 1106:3344:3344:1122 VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] rev 1, Mem @ 0xf4000000/67108864, 0xfa000000/16777216, BIOS @ 0x????????/65536
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="S3 Graphics Co., Ltd."
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
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
(II) LoadModule: "s3g"
(II) Loading /usr/lib/xorg/modules/drivers/s3g_drv.so
(II) Module s3g: vendor="S3 Graphics Co., Ltd."
    compiled for 1.7.6, module version = 14.5.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) Current driver version 14.5.2
(II) Driver build on 09/06/2011
(II) Build environment lists:
        os version: 
        gcc version: 
        ld version: 
(II) s3g: Driver for S3 Graphics chipsets: DeltaChromeMX,SDR(DC),
    DeltaChromeMX,DDR(DC), DeltaChromeMX,SDR,C(DC),
    DeltaChromeMX,DDR,C(DC), DeltaChromeIX,SDR(CMS),
    DeltaChromeIX,DDR(CMS), DeltaChromeIX,SDR,C(Unknow),
    DeltaChromeIX,DDR,C(Unknow), GammaChromeMT,SDR(Metro),
    GammaChromeMX,DDR,XM18(Metro), GammaChromeMX,DDR,MPM32(Metro),
    GammaChromeMX,DDR,MPM64(Metro), ChromeMA,SDR(Matrix),
    Chrome S20 Series, ChromeMA,DDR3,S25(Matrix),
    ChromeMA,DDR3,S23D(Matrix), Chrome 23D, ChromeXM27C,DDR3(Matrix),
    ChromeXM27A,DDR3(Matrix), ChromeXM23,DDR3,MPM32(Matrix),
    ChromeXM23,DDR3,MPM64(Matrix), DeltaChromeMA,SDR(Manhattan),
    Chrome460,Engineering35SV(D2), Chrome460,Engineering35MV(D2),
    Chrome460,Engineering33MV(D2), Chrome460_450,33MV(D2),
    Chrome460,Engineering33SV(D2), Chrome460_450,33SV(D2),
    Chrome440,Engineering23MV(D3), Chrome440_430,23MV(D3),
    Chrome440,Engineering23SV(D3), Chrome440_430,23SV(D3),
    Chrome460_450,33MV(D2Mobile), Chrome460_450,33SV(D2Mobile),
    Chrome440_430,23MV(D3Mobile), Chrome440_430,23SV(D3Mobile),
    Chrome440_430, D4, Chrome4300E, Chrome5400E, ChromeEUMA, ChromeE2UMA
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for s3g
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```now i am:mad: booting from my live usbstick..please any one help me out........^^

---

### Post by afixane on 2012-06-19
Can you tell me , what package management that blacktrack use?? :D

---

### Post by vykuntamsrinivas on 2012-06-19
thank you, sry i  have a confusion that it uses ubuntu11.04 or  ubuntu 10.*  versions..but i exactly know that its built on 3.2.6 linux kernel..can you please gimme any command which makes  u clear about  this problem?:(

---

### Post by vykuntamsrinivas on 2012-06-19
hi afixane, BACKTRACK5 supports  ubuntu 11.04 version.....^^;)

---

### Post by oldos2er on 2012-06-19
Moved to Other OS/Distro Talk.

---

### Post by vykuntamsrinivas on 2012-06-20
hi oldos2er,thanks for your help friend,but i want  solution to my problem.I am doing CEH(certified ethical hacker) certification ..got struck  in the middle ...i want my desktop back..cz i  did a lot of work in that...any way i'll wait for one day and reinstall my BACKTRACK5.....hope  any friend helps me........^^

---

### Post by chamber on 2012-06-20
Just reinstall it.  BackTrack is not meant to be used as a day to day system.  Using as a live USB and only bootinh into it when you need it is the preffered way of doing things.

Also,

[http://www.backtrack-linux.org/forums/forum.php?](http://www.backtrack-linux.org/forums/forum.php?)

---

### Post by oldos2er on 2012-06-20
> **vykuntamsrinivas said:**
> hi oldos2er,thanks for your help friend,but i want  solution to my problem.

I suggest you ask for help here: [http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

---

### Post by vykuntamsrinivas on 2012-06-21
> **oldos2er said:**
> I suggest you ask for help here: [http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

i already posted 2 threads in backtrack-linux forums,but didnt get reply so i posted  it here and by the way thanks to all friends who helped me in this forum.........i reinstalled BT5..see you again.....^^
):P

---

