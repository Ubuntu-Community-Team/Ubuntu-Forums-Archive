---
title: "Xubuntu 14.04 on iMac G3?"
date: 2014-05-02
forum: Apple Hardware Users
---

### Post by chris-interim on 2014-05-02
Greetings - the latest references I've seen here to iMac G3s are 2011, so I was wondering if anyone had had any luck with 14.04 on one of these beasties?

I got the server distribution to install on it without any problem.  I then app-get installed the xubuntu-desktop and rebooted to a blank screen.

I then copied in several of the Xorg.conf's in a thread regarding the 12.X distribution ending with:
```
[INDENT]Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0 
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "extmod"
Load "record"
Load "dbe"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection
Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync 58-62
VertRefresh 75-117
ModeLine "1024x768" 78.5 1024 1045 1141 1312 768 769 772 796 +hsync +vsync
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
Option "NoAccel" "True"
#Option "SWcursor" # [<bool>]
#Option "Dac6Bit" # [<bool>]
#Option "Dac8Bit" # [<bool>]
#Option "DMAForXv" # [<bool>]
#Option "ForcePCIMode" # [<bool>]
#Option "CCEPIOMode" # [<bool>]
#Option "CCENoSecurity" # [<bool>]
#Option "CCEusecTimeout" # <i>
#Option "AGPMode" # <i>
#Option "AGPSize" # <i>
#Option "RingSize" # <i>
#Option "BufferSize" # <i>
#Option "EnablePageFlip" # [<bool>]
#Option "Display" # <str>
#Option "PanelWidth" # <i>
#Option "PanelHeight" # <i>
#Option "ProgramFPRegs" # [<bool>]
Option "UseFBDev" "True"
#Option "VideoKey" # <i>
#Option "ShowCache" # [<bool>]
#Option "VGAAccess" # [<bool>]
Identifier "Rage 128"
Driver "ati"
EndSection
Section "Screen"
Identifier "Screen0"
Device "Card0"
DefaultDepth 16
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
[/INDENT]

```

which **might** have worked with version 13.

So my question is the obvious -- has anybody gotten one of these old iMac G3s working with the latest release or should I drop back to version 12?

--Chris

---

### Post by este.el.paz on 2014-05-04
@Chris:

From what I'm seeing here and on the Lu mailing list, it seems like you'd have to recompile the kernel to get 14.04 to work in several areas . . . on a G4, so I don't know whether it would be easier or harder for a G3 . . . ??  If it means nothing to you to fiddle with many items to get it going, then you might do it, otherwise 12 is probably the better choice for the ppc units . . . I was looking at it for my G4 iMac, but don't have the time or the chops for that mission . . . then I was thinking that I might try it on my G4 iBook, but still looks like either upgrading the system, but downgrading the kernel would have to take place . . . ???  Up to you . . . .

e.e.p.

---

### Post by chris-interim on 2014-05-05
I just got this to work!

OK, first off, let me say that Xubuntu 14.04 desktop on a 256MB iMac G3 is ... uh ... not fast.  The disk will basically melt down with all the paging.

To make it work, I got the legacy Mesa drivers but ended up setting the driver the "fbdev" instead of "ati" and that gets me through the door.

However, to make it workable, I've been basically going back to the old fashion X environment of my dim youth:  "xdm" & "twm" instead of anything having to do with Gnome.

I did this by installing xdm, making it the normal login window manager, and then repointing the symbolic link in /etc/alternatives/x-window-manager from metacity or something gnome to /usr/bin/twm.

You then need to create a $HOME/.xsession (and I created a symbolic link to it $HOME/.xinitrc because I'm REALLY OLD).

For now $HOME/.xsession consists of:

```

#!/bin/bash
twm&
xterm -sb

```

Yes, I feel like I've stepped back to the late 90s, but I _**liked**_ the late 90s.world of X.

Note, I did not DE-install anything from the regular Desktop stuff.  I can still run abiword etc - but most of that stuff is INCREDIBLY slow.

But yes, this system is doing what I wanted:  It is running the latest software.  Pretty damn cool!

I suppose at some point I'll try to get the R128 driver working, but since I'm not ever going to be doing anything graphically intensive on this machine, I don't see it as a huge win.  People should let me know if they disagree.

---

### Post by este.el.paz on 2014-05-05
@Chris:

OK, good for you, obviously you've got skilz . . . I think there was some discussion of the r128 driver in the "Testers wanted for 12.04" thread . . . .

e.e.p.

---

