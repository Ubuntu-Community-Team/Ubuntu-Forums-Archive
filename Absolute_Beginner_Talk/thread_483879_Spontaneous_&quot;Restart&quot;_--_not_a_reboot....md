---
title: "Spontaneous &quot;Restart&quot; -- not a reboot..."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by shields on 2007-06-25
I am getting a "spontaneous restart", for lack of a better term.  

Without evident cause as I am working, Ubuntu 7.04 gives me a three second black screen followed by the login screen.  It's not a reboot because I never see any bios stuff -- just the login screen. Logging in takes me to the desktop environment with nothing open, except Gaim, which auto-loads on startup.

This problem has just developed in the past few days.

My machine is a Pentium 3 at 866 MHz.
My install is Ubuntu 7.04 -- pretty generic.

Any thoughts?

Thanks!

---

### Post by brigux on 2007-06-25
Just a quick thought: might be an issue with your Video drivers. Lots of HOWTO on the forum for the proper method depending of your Hardware. Apart from that I would test my memory module.

---

### Post by Seisen on 2007-06-25
That sounds like something to do with X. Do you receive any errors when this happens?

---

### Post by shields on 2007-06-29
> **Seisen said:**
> That sounds like something to do with X. Do you receive any errors when this happens?

No errors.  Just a login screen :|

It's a new phenomenon.

---

### Post by srt4play on 2007-06-29
> **shields said:**
> No errors.  Just a login screen :|

It's a new phenomenon.

Did you check the Xorg log file in /var/log ?

---

### Post by Cauda_Draconis on 2007-09-22
I'm having the same problem. I just fixed a no-serving-host problem, so I can actually use gnome, but it keeps logging out after about 3 minutes, as soon as it tries to open things...

It says a bunch of times in my Xorg.0.log file that 
```

(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 289 x 21
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
AUDIT: Sat Sep 22 19:10:15 2007: 5307 X: client 1 rejected from local host (uid 1000)
AUDIT: Sat Sep 22 19:10:15 2007: 5307 X: client 2 rejected from local host (uid 1000)
AUDIT: Sat Sep 22 19:10:15 2007: 5307 X: client 1 rejected from local host (uid 1000)
AUDIT: Sat Sep 22 19:10:15 2007: 5307 X: client 4 rejected from local host (uid 1000)

```
It then says several times over that client 2 was rejected from local host.
then ```
(II) intel(0): EDID vendor "LPL", prod id 0
ProcXCloseDevice to close or not ?
```

And my Xorg.1.log file says, 
```
Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
```
and at the end, 
```

(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```

And Xorg.20.log says
```
(OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] DRM interface version 1.0
(II) intel(0): [drm] drmSetBusid failed (8, pci:0000:00:02.0), Permission denied
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.

``````
(EE) AIGLX: Screen 0 is not DRI capable

``````
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"

``` a bunch of times...


I'm wondering if it's a problem with which console xerver's running on, cuz after I fixed my no-host problem, I tried to restart gdm, and after a few commands not working, one of those grey boxes surrounded by blue came up with "a server's already running on that console" or something, and then it asked me to try another one, so I said no, and it came back to the same thing, so I said "yes" and now my linux keeps logging me out. :\

Anyone have any ideas on how to fix it?

---

### Post by Cauda_Draconis on 2007-09-22
Anyone?

---

### Post by Cauda_Draconis on 2007-09-23
My computer seems to have fixed itself. I left it alone for a day or so, then rebooted a couple times, and it works now... Dunno what I did... but *shrugs*

---

### Post by Dr Small on 2007-09-23
My other pc does this exact same thing. It has a Intel Processor, and I think the processor has some defect, as it does similar things on Windows also.

Dr Small

---

### Post by killaray on 2007-09-23
yea this has happened to me before.. happens randomly and my screen flashes like 3 times then goes to login screen

---

### Post by adhamox on 2008-01-26
the same with me !
nobody had a solution ??

---

### Post by shields on 2008-04-13
> **adhamox said:**
> the same with me !
nobody had a solution ??

This went away all by itself on mine.  Weird.

---

