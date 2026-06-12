---
title: "Crashing X-Server"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-10-22
After every few days my xserver goes crazy. After boot up the screen goes blank(monitor goes into standby) or all white. Then I run recovery mode and in command line try

sudo dpkg-reconfigure xserver-xorg command.Follow the instructions and exit

Sometimes it comes back, other times it still has the same problem. Sometimes xserver takes a vacation and I can't use it for 2-3 days.

What's going on??  Is there a programing bug in it?? what file you developers need to see to correct it?? What commands ( Step by step please) I type to view that file and send it to you for correction.

---

### Post by po0f on 2006-10-22
maneesh77,

Is there anything suspicious-looking in /var/log/Xorg.0.log?

---

### Post by maneesh77 on 2006-10-22
/var/log/Xorg.0.log 

how do I check that file, please tell me the exact commands to look at that file and what sort of problem am i looking for

---

### Post by maneesh77 on 2006-10-22
Is it this one




X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux maneesh-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 22 18:00:25 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux

---

### Post by po0f on 2006-10-22
maneesh77,

Yes, please post to output of the following command:
```
$ grep EE /var/log/Xorg.0.log
```

---

### Post by maneesh77 on 2006-10-22
Current Operating System: Linux maneesh-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
maneesh@maneesh-desktop:~$

---

### Post by po0f on 2006-10-22
maneesh77,

Nothing out of the ordinary.  Are you sure your hardware is stable?  This might be an issue with bad memory.

Boot the live CD and run memtest for an hour or two.

---

### Post by maneesh77 on 2006-10-22
hello?? is this the output you need??

---

### Post by maneesh77 on 2006-10-22
The hardware seems to be fine. I have windows Xp on second harddrive and it runs fine. But will run mem test from CD

thanks

---

### Post by Perfect Storm on 2006-10-22
I agree with po0f, it could be bad hardware somewhere, properly the memory.

---

### Post by po0f on 2006-10-22
maneesh77,

An hour or two should be enough time for any problems to crop up.  BTW, what hardware are you using (mobo chipset, video card)?

---

### Post by Perfect Storm on 2006-10-22
Changed the title to something more helpful.

---

