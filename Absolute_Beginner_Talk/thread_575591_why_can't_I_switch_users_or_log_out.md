---
title: "why can't I switch users or log out"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by tambidude on 2007-10-14
I want to log in as different user and when I do switch users, the monitor goes
black. It looks the system is on, but monitor goes blank. why?

---

### Post by jwissick on 2007-10-21
I have the exact same problem...  any solutions?

---

### Post by mikeize on 2007-10-21
I have the same problem.  If I switch users, and then switch back...  black screen, and hard power off.  No problems if I actually log each user out before logging another in.  Annoying.

-mike

---

### Post by LilYoda on 2007-10-23
Same issue here.  This is happening since I switched to Gutsy.  What about you guys?

Also, I noticed something weird.  X usually runs on VTY 7.  If you start your system, it will be on VTY7.  But if I logout a user, then I briefly see the text console before gdm re-displays the login window.  And surprise, now X is running on VTY 9...  VTY 7 shows a text mode with nothing but a cursor in the upper left corner....

Very strange.

---

### Post by garren on 2007-10-29
I also am having this problem.  I have a Dell D400 with an intel 855 graphics card.  Nearly every time I try to log out, switch users, or shut down my monitor just turns black and the computer remains running albiet unusable.  I noticed in the driver settings that I was using some driver labeled as experimental.  I switched to a driver that had worked for me in past versions of Ubuntu--i810--but the problem persists.  

Any ideas?

---

### Post by d_yat on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: ([https://bugs.launchpad.net/ubuntu/+bug/157194](https://bugs.launchpad.net/ubuntu/+bug/157194) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey People. I think I have the same problem as you all. I made a bug report about it a week ago (look at bug link) but had no reply yet.
I've too noticed the whole x on tty7, and then tty9 after logging out.
I reckon it's just that it can't start a second x-server, As I tried that aswell (look at bug report), and the same black screen appears. Is this true with everyone else?

Anyway, if this is a bug, post a bug report to tell the bug people! we'll get a fix to the bug then! (did I write the word bug enough yet? =P )

---

### Post by d_yat on 2007-10-31
Just a question to you all, when does the Black screen appear?
For me, it only happens when I try to switch users, or when I try to start a second X-Server with
sudo X :2.0
or
xinit -- :2
from either the terminal in the desktop, or via one of the virtual terminals (ctrl-alt-F1..->6).
Which is why I think, it's just a problem with starting that second X-Server, which has to be done when starting a second user, doesn't it?

---

### Post by LilYoda on 2007-11-03
> **d_yat said:**
> Just a question to you all, when does the Black screen appear?
For me, it only happens when I try to switch users, or when I try to start a second X-Server with
sudo X :2.0
or
xinit -- :2
from either the terminal in the desktop, or via one of the virtual terminals (ctrl-alt-F1..->6).
Which is why I think, it's just a problem with starting that second X-Server, which has to be done when starting a second user, doesn't it?
I haven't tried starting a secodn X Server, but will do.  For me it happens only when I try to switch user, and I did notice that the new X runs on VT9.  Weird:confused:

---

### Post by jken146 on 2007-11-08
I have the same problem too, although user switching had been working ok for me since the Gutsy release in October until a couple of days ago.   I've no idea why it developed the problem, I didn't mess with any X server settings or anything like that.

---

### Post by evilregis on 2007-11-08
When you get your black screen is your keyboard still responsive?  Can you restart X with CTRL+ALT+BACKSPACE?  If not, can you bring up a terminal (CTRL+ALT+F[1-6])?

If X restarts you'll be presented with the login screen again.  If you can get to terminal you can try restarting X:

```
/etc/init.d/gdm restart
```

They're not ideal solutions as you will lose everything you were working on, but it will at least save you having to do a hard power down.

---

### Post by SunnyRabbiera on 2007-11-08
yeh there appears to be a hang...
I think this is related to compositing and memory, especially if you have lower specs.
I can suggest turning off desktop effects to see what happens.

---

### Post by garren on 2007-11-08
No, I can't get to a terminal, and restarting x doesn't work.  

It seems like (I can't speak for everyone, but this is the case for me) the monitor doesn't merely turn black, it turns *off*.  There seems to be no way to turn the monitor back on short of forcing the computer to shutdown (by holding down the power button.  I tried pressing the buttons necessary to bring up a terminal and effect a shutdown, but this didn't work, assuming I even did it properly) and turning it on again.  

For me, I don't think it has anything to do with desktop effects, because I just don't see why that would cause my monitor to turn off.  I think it's a driver issue--when I switched from the Intel experimental driver (which was chosen by default when I installed) to the i810 driver used in prior releases of Ubuntu, the problem got worse.  When I switched back to the experiemental driver, the problem abated to a degree--instead of happening every log off/switch user/shutdown, it only happens every 3rd or 4th time).  

Perhaps I just need to wait for a better driver to come out??? If that will ever happen???

---

### Post by LilYoda on 2007-11-09
I tried already to switch to console, and whereas the keyboard seems to work, the display is completely "out" (very similar to the poster above me)

So even if I switch to a console, I still have a black screen.  When that happens I usually try to do ctrl+alt+f1, then ctrl+alt+suppr.  Even that doesn't always work...  Most of the time, I end up doing a shutdown by pressing the power button on the case...

---

### Post by LilYoda on 2007-11-17
I tried with xinit, and bingo, the PC totally locks up...

Even a scheduled shutdown doesn't shut the box down

Here is the error log of the xinit
```
doudou@Camembert:~$ cat X.errlog 


Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Camembert 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sat Nov 17 20:29:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) Module already built-in
(II) Module already built-in

```

And here is the normal log.

Does anyone have any clue what is going on???

```
doudou@Camembert:~$ cat /var/log/Xorg.2.log

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Camembert 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sat Nov 17 20:29:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "BenQ FP931-D"
(**) |   |-->Device "ATI Technologies Inc Radeon R350 [Radeon 9800]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Extension "Composite" is disabled
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
(--) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 147b,1c08 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0080 card 147b,1c08 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0084 card 147b,1c08 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0087 card 147b,1c08 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0087 card 147b,1c08 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0088 card 147b,1c08 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,008a card 147b,1c08 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,008b card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0085 card 147b,1c08 rev a3 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,008e card 147b,1c08 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 1002,4e49 card 174b,0470 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e69 card 174b,0471 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:0b:0: chip 1106,3119 card 147b,1c08 rev 11 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:8:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [1] -1  0       0x0000a400 - 0x0000a4ff (0x100) IX[B]
        [2] -1  0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [3] -1  0       0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800] rev 0, Mem @ 0xd0000000/27, 0xe9030000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary) rev 0, Mem @ 0xd8000000/27, 0xe9020000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [1] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [2] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [3] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [4] -1  0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [7] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [8] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [9] -1  0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [10] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [11] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [12] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [13] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [14] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [15] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [16] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [18] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [19] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
        [0] -1  0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [1] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [1] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [2] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [3] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [4] -1  0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [7] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [8] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [9] -1  0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [10] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [11] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [12] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [13] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [14] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [15] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [16] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [18] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [19] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
        [0] -1  0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [1] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
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
        [4] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [5] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [6] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [7] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [8] -1  0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [17] -1 0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [19] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [20] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [21] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [22] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [25] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [26] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [27] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.37.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E49) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [5] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [6] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [7] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [8] -1  0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [17] -1 0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [19] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [20] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [21] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [22] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [25] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [26] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [27] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82068e8
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [5] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [6] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [7] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [8] -1  0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [21] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [22] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [23] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [24] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [25] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [26] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [27] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [28] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [29] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [30] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
        [31] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [32] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800" (Chipset = 0x4e49)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0470)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe9030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmGetBusid returned 'PCI:1:0:0'
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.37.6
        ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: BNQ  Model: 7670  Serial#: 3613
(II) fglrx(0): Year: 2004  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.614
(II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: BenQ FP931-D
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff0009d170761d0e0000
(II) fglrx(0):  2c0e01036c261e78eaa150a3574c9d25
(II) fglrx(0):  115054bdef80714f81908180818c0101
(II) fglrx(0):  010101010101302a009851002a403070
(II) fglrx(0):  1300782d1100001ed50980a0205e6310
(II) fglrx(0):  10605208782d1100001a000000fd0038
(II) fglrx(0):  4c1f530e000a202020202020000000fc
(II) fglrx(0):  0042656e512046503933312d440a0052
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 33 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0): *Mode "640x350": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "640x350"   25.17  640 656 752 800  350 387 389 449 +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0): *Mode "640x350": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "640x350"   25.17  640 656 752 800  350 387 389 449 +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
        compiled for 7.1.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xe9030000 - 0xe903ffff (0x10000) MX[B]
        [1] 0   0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [7] -1  0       0xea005000 - 0xea005fff (0x1000) MX[B]
        [8] -1  0       0xea004000 - 0xea0040ff (0x100) MX[B]
        [9] -1  0       0xea003000 - 0xea003fff (0x1000) MX[B]
        [10] -1 0       0xea002000 - 0xea002fff (0x1000) MX[B]
        [11] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [12] -1 0       0xe9030000 - 0xe903ffff (0x10000) MX[B](B)
        [13] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [14] -1 0       0xe9020000 - 0xe902ffff (0x10000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [19] 0  0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [23] -1 0       0x0000d000 - 0x0000d07f (0x80) IX[B]
        [24] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [25] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [26] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [27] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [28] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [29] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [30] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [31] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [32] -1 0       0x0000ec00 - 0x0000ec1f (0x20) IX[B]
        [33] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
        [34] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [35] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x18000
(II) fglrx(0): [drm] mapped SAREA 0x18000 to 0xb7fc1000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f00421b bridge: 0x10de/0x01e0
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00431a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0c0a000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): GLESX enableFlags = 0
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x2
(II) fglrx(0): [DRI] installation complete
d
```

---

### Post by marquivon on 2007-11-20
I fought with this problem for more than a year, installed Gutsy hoping that the problem would be taken care of. Unfortunately it didn't. Then I bought a nVidia 7300 GT to experiment whether its a driver issue, and now I don't have this problem any more. Endless logoffs, logins, switch users, console to X, X to console - everything works EVERY time.

So, probably the issue is with the "intel" and "i810" drivers that ship with Ubuntu. An nVidia or ati card maybe a solution for you all.

-
Vivek Kapoor

---

### Post by d_yat on 2007-11-21
> **marquivon said:**
> I fought with this problem for more than a year, installed Gutsy hoping that the problem would be taken care of. Unfortunately it didn't. Then I bought a nVidia 7300 GT to experiment whether its a driver issue, and now I don't have this problem any more. Endless logoffs, logins, switch users, console to X, X to console - everything works EVERY time.

So, probably the issue is with the "intel" and "i810" drivers that ship with Ubuntu. An nVidia or ati card maybe a solution for you all.

-
Vivek Kapoor

I am using the ATI Radeon 9550 (fglrx driver), but still have the problem =(

---

### Post by LilYoda on 2007-11-21
> **d_yat said:**
> I am using the ATI Radeon 9550 (fglrx driver), but still have the problem =(

I also have the fglxr driver with an ATI 9800 Pro.  So the problem isn't limited to intel graphic cards.

---

### Post by LilYoda on 2008-01-06
Well, today I installed a Nvidia 7600GT instead of my ATI 9800Pro.  After one reboot, the problem is gone, and I can now switch users again...

So it seems it's a bug in the accelerated servers for ATI cards, and possibly other hardware

---

### Post by markoloka on 2008-01-10
Usually when i start my pc i have black screen. I restart x again w/ ctrl+alt+bckspce.
If i try to switch user... screen goes black so reset button is only way to survive this.
There's several bugs for this... but so far no help.
2 users on same pc... it really sucks that only way to work this to either log out or hard reset (which is not recommeneded but what can you do... switch to workable distro)

---

### Post by LilYoda on 2008-01-11
What video card are you using and which driver?
You could switch back to Ubuntu Feisty.  It did not show this problem, I think it appeared with Gutsy.

---

### Post by harrychana on 2008-01-11
> **tambidude said:**
> I want to log in as different user and when I do switch users, the monitor goes
black. It looks the system is on, but monitor goes blank. why?
What are you using in terms of uduntu?

---

### Post by markoloka on 2008-01-15
> **LilYoda said:**
> What video card are you using and which driver?
You could switch back to Ubuntu Feisty.  It did not show this problem, I think it appeared with Gutsy.

I had same problem in feisty so no use. Now i'm using gutsy w/ latest updates.
I have ati 2400 Pro w/ latest fglrx aka 7.12.

---

### Post by LilYoda on 2008-01-16
> **markoloka said:**
> I had same problem in feisty so no use. Now i'm using gutsy w/ latest updates.
I have ati 2400 Pro w/ latest fglrx aka 7.12.

For me it appeared with gutsy, but maybe I had missed a fglrx driver update in feisty...  Or maybe I was using a nVidia card at the time.

Anyway, see if you can get your hands on a old card that is not ATI (or apparently Intel as well, judging by this thread).  Borrow it from a buddy, maybe?  This way you can at least isolate your problem and be sure it's related to your driver+card combo...

---

### Post by mister_pink on 2008-01-16
If you're using the ati drivers, this is a known issue and there's nothing anyone, except ati, can do about it. If you're not, then I don't have a clue whats wrong.

---

### Post by garren on 2008-01-16
I'm having the same problem with an Intel 855 using the "Experimental driver" that X.org chose by defualt for my system (it's worse when I try to choose the i810 driver), and I'm noticing that the degree of the problem has been fluctuating.  

For about a week I end up having to do a reset after nearly every attempt at switching users, logging out, or shutting down; then I'll go a week in which I only have the problem a couple times (still annoying even then, of course).  

I have also noticed that I seem to have the problem less, though it still happens, when I turn off all programs before shutdown and give the computer a few seconds after bringing up the shutdown screen before actually hitting the shutdown button (or perhaps that's in my mind; the idea is that I'm letting all processing finish prior to introducing a new command).  

I also have the problem less often it seems (though, again, it still happens) when using KDE4 rather than Gnome.

---

### Post by De Baimbo on 2008-01-23
Same problem here with Ati Radeon X1300, either using the Ati drivers or the ones supplied with Ubuntu. That seems a serious bug, in these days I am trying to make my dad and my sister move from Windows to Linux Ubuntu and that problem is the only reason why they are still doubtful. Can you guys tell me how to report this to the  Ubuntu programming team?

---

### Post by d_yat on 2008-01-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157194](https://bugs.launchpad.net/ubuntu/+bug/157194) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **De Baimbo said:**
> Same problem here with Ati Radeon X1300, either using the Ati drivers or the ones supplied with Ubuntu. That seems a serious bug, in these days I am trying to make my dad and my sister move from Windows to Linux Ubuntu and that problem is the only reason why they are still doubtful. Can you guys tell me how to report this to the  Ubuntu programming team?

you could mention it in my bug report.

there's also another similar bug linked to mine, but i'm not sure if it's the same.

---

### Post by LilYoda on 2008-01-24
Done

---

