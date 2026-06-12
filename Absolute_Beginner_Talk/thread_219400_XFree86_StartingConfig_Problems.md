---
title: "XFree86 Starting/Config Problems"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by willmcgregor on 2006-07-19
I am having a problem getting a new install of XFree86 to start. The grey desktop thing come up with no icons just the X for the cursor with can be moved by the mouse.

The end of my /var/log/XFree86.0.log file looks like

(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/input/mouse0"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/input/mouse0"
(==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(==) Mouse0: Buttons: 3
(II) Keyboard "Keyboard0" handled by legacy driver
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!

When i do:
will@ubuntu:/usr$ ls -l /usr/X11R6/lib/X11/fonts/
total 112
drwxr-xr-x 2 root root 65536 2005-03-17 02:05 75dpi
drwxr-xr-x 2 root root  4096 2005-03-17 02:08 CID
drwxr-xr-x 3 root root  4096 2005-03-17 02:02 encodings
drwxr-xr-x 2 root root  4096 2006-07-20 02:37 local
drwxr-xr-x 2 root root 12288 2006-07-20 02:37 misc
drwxr-xr-x 2 root root  4096 2005-03-17 02:08 OTF
drwxr-xr-x 2 root root  4096 2005-03-17 02:07 Speedo
drwxr-xr-x 2 root root  4096 2005-03-17 02:08 TTF
drwxr-xr-x 2 root root  4096 2005-03-17 02:08 Type1
drwxr-xr-x 2 root root  4096 2005-03-17 02:02 util
So it seems the files are there?

Any idea whats goin on here? Being a newb I've been enjoying problem solving for myself but I cant figure this one out ](*,)

Thanks for any help!

Will.

---

### Post by TheOtherShoe on 2006-08-18
I don't think the font warnings are the source of the problem: my log shows the same thing.

Have you tried using Xorg instead of XFree86? Unless you are using Warty Warthog, Xorg is probably what you want.

```
sudo apt-get install xserver-xorg
```

---

