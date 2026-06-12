---
title: "[SOLVED] Huge Title Bar/Log--In Window"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by lucakins on 2007-10-20
Hey everyone. I'm a brand new (When I mean new, I mean brand-spaking-new, as in, I know almost nothing about it) Ubuntu user and I'm having an issue. I wasn't able to find this in the search and I apologize if it's been answered before.

So, here's my problem:
I've installed Ubuntu and having it running on my laptop and everything seems to be working okay. I'm running Gutsy Gibbon 7.10 but my title bars for applications and my log-in window are simply massive. I can't even see what I'm typing in for my login window. I have my resolution set to 1280x800 which is what my laptop has, but no matter how I play with the appearance settings, I can't fix this.
Any help would be GREATLY appreciated, please and thanks.

---

### Post by lucakins on 2007-10-20
Well, nevermind. I figured it out on my own.
Thanks anyway.

---

### Post by Maestro23 on 2007-10-20
Good deal.  Please mark this thread SOLVED.

---

### Post by KCMOStealthRT on 2007-10-20
I seem to be having the same problem and was wondering what you did to get this fixed.

---

### Post by smyrna112 on 2007-10-25
yes please reply with the fix, i have the same issue!!

---

### Post by smyrna112 on 2007-10-25
> **Maestro23 said:**
> Good deal.  Please mark this thread SOLVED.

Why would you tell someone to mark it solved if there was no solve posted? Is this so we waist more time posting more New Messages on the main board or is it so when people search they get a post with no resolution to the the issue?? Good idea this post is has really helped the others having the same problem!!!!

---

### Post by por100pre1 on 2007-10-25
Check your fonts settings in **System> Preferences> Appearance**. A font there is too big.

---

### Post by zippytex on 2007-10-25
> **lucakins said:**
> Well, nevermind. I figured it out on my own.
Thanks anyway.

I am having the same problem.  i went to system, preference,font and reduced the font to size 6.  The title bar is still one inch high, which is smaller, but still to large.  Could you help please?  Thanks, Mary:confused:

---

### Post by smyrna112 on 2007-10-26
same!

---

### Post by darco on 2007-10-26
For me it was a matter of disabling/renabling Desktop effects...I boot up from the Live CD on my laptop and each time I have that huge bar but once I run the fix, its all good....

darco

---

### Post by f03el on 2007-10-29
I installed Xubuntu 7.10 today, first on a PII 400 MHz, and then on my laptop with Intel 945GM chipset. On the old computer there were no problems, I just thought that the fonts looked somewhat small. As I then should log on to the laptop the text in the fields was HUGE. Inside XFCE it was totally impossible to do something, because all text took up most of the screen. There were menus and title bars everywhere. Temporarily  I could set most of the used fonts to size 1.0 which gives quite normal looking sizes. I have tested some of the solutions around which have help a couple, but nothing works. Is it really so few having this problem?

---

### Post by ashughes on 2007-10-30
FYI. The fix of disabling and enabling desktop effects worked for me.  I have an Intel Integrated graphics card.

Steps to Fix:
1. Click System>Preferences>Appearance
2. Click Visual Effects tab
3. Select the None radio button
You should see everything return to normal at this point
4. Select the radio button for either of the visual effect settings at this point (if you choose)
Everything should look ok after a few seconds of the system enabling the effects.

Hope this helps.

Cheers!

**UPDATE**
This only fixed the problem until I restarted, at which point it returned.   I have managed to fix it permanently however.  This is what I did:
1. sudo gedit /etc/gdm/gdm.conf
2. find the section [server-Standard] in that file
3. You should see a line that says "-command=/usr/bin/X -br -audit 0".  Change it to read "-command=/usr/bin/X -br -audit 0 -dpi 96".
4. Save, quit, and restart

You should be good to go now.

Cheers

---

### Post by smyrna112 on 2007-10-31
Great the line in gdm.conf worked great for once I login but before that on the login screen the font where i type my username and password it also huge!

---

### Post by f03el on 2007-10-31
ashughes: Thank you for helping.

The method of disabling/enabling desktop effects isn't possible for me though I use XFCE. I tried editing /etc/gdm/gdm.conf and rebooting, but that changed nothing.
Btw, X seems to have the right dpi settings:
```
erik@fox:~$ cat /var/log/Xorg.0.log |grep DPI
(==) intel(0): DPI set to (100, 100)
```

/var/log/Xorg.0.log:
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux fox 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 31 10:36:16 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Allmän skärm"
(**) |   |-->Device "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30bb rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 103c,30bb rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 103c,30bb rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30bb rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30bb rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30bb rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30bb rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30bb rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30bb rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30bb rev 02 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4222 card 8086,1001 rev 02 class 02,80,00 hdr 00
(II) PCI: 05:08:0: chip 8086,1092 card 103c,30bb rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x00002000 - 0x000020ff (0x100) IX[B]
        [1] -1  0       0x00002400 - 0x000024ff (0x100) IX[B]
        [2] -1  0       0x00002800 - 0x000028ff (0x100) IX[B]
        [3] -1  0       0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
        [0] -1  0       0x00003000 - 0x000030ff (0x100) IX[B]
        [1] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [2] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
        [3] -1  0       0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
        [0] -1  0       0x00004000 - 0x00004fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xd80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd8100000/19, 0xc0000000/28, 0xd8200000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd8180000/19
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [1] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [2] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [3] -1  0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [4] -1  0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [5] -1  0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [6] -1  0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [7] -1  0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [8] -1  0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [9] -1  0       0x00004000 - 0x0000403f (0x40) IX[B]
        [10] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [11] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [12] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [13] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [14] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [15] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [16] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [20] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [21] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [22] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [23] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [24] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [25] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [1] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [2] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [3] -1  0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [4] -1  0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [5] -1  0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [6] -1  0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [7] -1  0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [8] -1  0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [9] -1  0       0x00004000 - 0x0000403f (0x40) IX[B]
        [10] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [11] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [12] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [13] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [14] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [15] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [16] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [20] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [21] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [22] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [23] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [24] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [25] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [5] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [6] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [7] -1  0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [8] -1  0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [9] -1  0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [10] -1 0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [11] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000403f (0x40) IX[B]
        [16] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [17] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [18] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [19] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [20] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [21] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [22] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [28] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [29] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [30] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [31] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 2.1.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
        compiled for 4.2.0, module version = 1.0.0
        Module class: XFree86 XInput Driver
        ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [5] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [6] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [7] -1  0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [8] -1  0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [9] -1  0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [10] -1 0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [11] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00004000 - 0x0000403f (0x40) IX[B]
        [16] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [17] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [18] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [19] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [20] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [21] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [22] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [28] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [29] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [30] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [31] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [5] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [6] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [7] -1  0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [8] -1  0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [9] -1  0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [10] -1 0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [11] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x00004000 - 0x0000403f (0x40) IX[B]
        [19] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [20] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [21] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [22] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [23] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [24] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [25] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [28] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [30] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [31] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [32] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [33] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [34] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
        [35] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [36] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD8100000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
        for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section Allmän skärm
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: 2a00  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.2
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) intel(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP154W01-TLAE
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c002a00000000
(II) intel(0):  000f0102802115780a0f109758528828
(II) intel(0):  23505400000001010101010101010101
(II) intel(0):  010101010101d51b00a0502017303020
(II) intel(0):  26002115100000190000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503135345730312d544c414500cb
(II) intel(0): EDID vendor "LPL", prod id 10752
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: 2a00  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.2
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) intel(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP154W01-TLAE
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c002a00000000
(II) intel(0):  000f0102802115780a0f109758528828
(II) intel(0):  23505400000001010101010101010101
(II) intel(0):  010101010101d51b00a0502017303020
(II) intel(0):  26002115100000190000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503135345730312d544c414500cb
(II) intel(0): EDID vendor "LPL", prod id 10752
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.1   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(**) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000000 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x10606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd8200000 - 0xd823ffff (0x40000) MS[B]
        [1] 0   0       0xc0000000 - 0xcfffffff (0x10000000) MS[B]
        [2] 0   0       0xd8100000 - 0xd817ffff (0x80000) MS[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xd8000000 - 0xd8000fff (0x1000) MX[B]
        [8] -1  0       0xd6000000 - 0xd6000fff (0x1000) MX[B]
        [9] -1  0       0xd8444400 - 0xd84447ff (0x400) MX[B]
        [10] -1 0       0xd8444000 - 0xd84443ff (0x400) MX[B]
        [11] -1 0       0xd8240000 - 0xd8243fff (0x4000) MX[B]
        [12] -1 0       0xd8180000 - 0xd81fffff (0x80000) MX[B](B)
        [13] -1 0       0xd8200000 - 0xd823ffff (0x40000) MX[B](B)
        [14] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [15] -1 0       0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] 0  0       0x00001800 - 0x00001807 (0x8) IS[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x00004000 - 0x0000403f (0x40) IX[B]
        [23] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [24] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [25] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [26] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [27] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [28] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [29] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [31] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [33] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [34] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [35] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [36] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [37] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [38] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
        [39] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [40] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 363776 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1455100 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 3420 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x        5f820000 physical)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x        5f832000 physical)
(II) intel(0): 0x00040000-0x024f7fff: front buffer (37600 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x024f8000-0x02507fff: xaa scratch (64 kB)
(II) intel(0): 0x02800000-0x02ffffff: back buffer (6400 kB)
(II) intel(0): 0x03000000-0x037fffff: depth buffer (6400 kB)
(II) intel(0): 0x03800000-0x057fffff: DRI memory manager (32768 kB)
(II) intel(0): 0x05800000-0x077fffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf8b86000
(II) intel(0): [drm] mapped SAREA 0xf8b86000 to 0xb7aec000
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xd8100000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 800 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x28008000
(II) intel(0): [drm] Back Buffer = 0xc2800000
(II) intel(0): [drm] Depth Buffer = 0xc3000000
(II) intel(0): [drm] textures = 0xc5800000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x024f8000 (pgoffset 9464)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02800000 (pgoffset 10240)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x03000000 (pgoffset 12288)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x05800000 (pgoffset 22528)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(EE) AIGLX error: dlopen of /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) intel(0): Setting screen physical size to 289 x 21
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: 2a00  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.2
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) intel(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP154W01-TLAE
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c002a00000000
(II) intel(0):  000f0102802115780a0f109758528828
(II) intel(0):  23505400000001010101010101010101
(II) intel(0):  010101010101d51b00a0502017303020
(II) intel(0):  26002115100000190000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503135345730312d544c414500cb
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync
(II) intel(0): EDID vendor "LPL", prod id 10752
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.1   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: 2a00  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.2
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) intel(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP154W01-TLAE
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c002a00000000
(II) intel(0):  000f0102802115780a0f109758528828
(II) intel(0):  23505400000001010101010101010101
(II) intel(0):  010101010101d51b00a0502017303020
(II) intel(0):  26002115100000190000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503135345730312d544c414500cb
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync
(II) intel(0): EDID vendor "LPL", prod id 10752
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.1   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV

```

// Erik

---

### Post by ashughes on 2007-10-31
I suspect gdm.conf is GNOME specific.  Not sure about XFCE, sorry.

---

### Post by f03el on 2007-11-01
I just tested to login to another tty, stop gdm and run startx. Now the fonts seem to be normal sized. Something wrong with gdm?

---

### Post by smyrna112 on 2007-11-01
Seems to be fixed in Pre-Released Updates. mine is fine now. At  least for GDM i don't know bout X or K

---

### Post by f03el on 2007-11-01
Since even Xubuntu uses GDM it sounds great.

---

### Post by wigg on 2007-11-01
I know that your issue is probably making you upset.  I know when I want linux to do something and I just can quite get my head around it, it can be quite frustrating.  However, the screenshot posted with the huge titlebars was just the laugh I needed today.

---

### Post by smyrna112 on 2007-11-01
> **wigg said:**
> I know that your issue is probably making you upset.  I know when I want linux to do something and I just can quite get my head around it, it can be quite frustrating.  However, the screenshot posted with the huge titlebars was just the laugh I needed today.

Made me laugh too. Even though it was happening to me!

---

### Post by NTITech on 2007-11-13
I have Kubuntu, and yes, my login screen text is huge.  But after logging in, the text is normal sized.  How do I fix this in Kubuntu?

---

### Post by livinjean on 2007-11-21
i have kubuntu 7.10 and stuck with huge text at login window (after login evrythign is ok), any ideas on how to solve this

---

### Post by lidko on 2007-12-02
I have the same exact problem --in fact, I switched to Kubuntu 1 hour after trying Ubuntu with the impossible-to-navigate giant text for the entire OS! (Then I noticed a Gnome error while booting, so I figured I'd try KDE instead)

I'll need help too because I'm a NOOBuntu.

---

### Post by NaplesBill on 2007-12-18
I was having this same problem on my work laptop.  It's an HP DV5000 with the Intel GPU.  I added the "-dpi 96" to all three server types and it solved this issue for me.  The login and all title bars are now functioning with normal size text.

---

### Post by mohansoundar on 2008-01-03
Is this problem really SOLVED for everybody ??  :confused:
I have hp dv6000t and ubuntu installed.
Right from the first day of ubuntu Feisty and now Gutsy, I have the huge login font and the huge title bar.

Few things i noted were

1.  After making -dpi 96 change in gdm.conf, only the title bar problem is solved ONLY in the administrator account (may be something else would have solved the problem and I coincidentally think to be this :confused::confused: !! )

2.  Even without having the desktop effects, the title bar is huge :(

3.  If I logoff and login, ie., restart X, then the problem is solved :D, but on every boot, I need to restart X

---

### Post by f03el on 2008-01-17
Nope. None of the suggested solutions around has worked for me, so until something appears I go with xdm.

---

### Post by beameup on 2008-02-16
OK, about to try this. Wish me luck LOL

---

### Post by doctorbighands on 2008-02-16
Okay, here's a weird situation for all of you:

I tried the "-dpi 96" solution. It worked when I was running Hardy, and it worked immediately after a fresh Gutsy install (which I'm currently running). As soon as I installed an upgrade to Ubuntu Studio (which I JUST did about an hour ago), my login font went huge again, and about half the time when I start X, the fonts and panels on my desktop get enormous and wonky, and an error message appears that says something like "there was an error starting Gnome..." (that's all I can read, because the huge font pushes the rest of the text off the screen).

?????

---

### Post by beameup on 2008-02-21
When I tried the "-96DPI" edit, I lost the whole login screen. Would have to log in and run "startx" from a prompt.  So as of now, I have the desktop effects turned off, and i set the account to auto-login.

 Is everyone having this issue on the Intel 945 onboard graphics chip?


I'm using my wife's Toshiba A105-4324 with the Intel Core Duo.

---

### Post by beameup on 2008-02-21
OK, I just read this little bit of info which might explain why the -96dpi change wasn't working for me:

[```
# GDM System Defaults Configuration file.
#
# This file should not be updated by hand.  Since GDM 2.13.0.4, configuration
# choices in the GDM System Configuration file (/etc/gdm/gdm.conf) will
# override the default values specified in this file.
#
# If you were using an older version of GDM, your system may have the the older
# gdm.conf configuration file on the system.  If so, then this file is used
# instead of the GDM Custom Configuration file for backwards support.  If you
# make changes to the GDM Custom Configuration file and they seem to not be
# taking effect, this is likely the problem.  Consider migrating your
# configuration to the new configuration file and removing the gdm.conf file.
#
# You can use the gdmsetup program to graphically edit the gdm.conf-custom
# file.  Note that gdmsetup does not support every option in this file, just
# the most common ones that users want to change.  If you feel that gdmsetup
# should support additional configuration options, please file a bug report at
# http://bugzilla.gnome.org/.
#
# If you hand-edit the GDM configuration, you should run the following command
# to get the GDM daemon to recognize the change.  Any running GDM GUI programs
# will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run invoke-rc.d gdm reload or invoke-rc.d gdm restart
# to cause GDM to restart and re-read the new configuration settings. 
# You can also restart GDM by sending a HUP or USR1 signal to the
# daemon.  HUP behaves like restart and causes any user session
# started by GDM to exit immediately while USR1 behaves like
# reload and will wait until all users log out before
# restarting GDM.
#
# For full reference documentation see the GNOME help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Some values are commented out, but show their default values.  Lines
# that begin with "#" are considered comments.
#
# Have fun!
  
```

I'll look for that gdmsetup program and see what I can do with that.     (Edit) Nothing! LOL

---

