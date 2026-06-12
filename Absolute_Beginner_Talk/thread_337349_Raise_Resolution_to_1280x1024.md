---
title: "Raise Resolution to 1280x1024"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-12
Background:  I have diligently searched the forums for information on raising the resolution in xorg.conf from 1024x768 to 1280x1024.  I have edited xorg.conf and changed the HorizSync and VertRefresh rates to those of my monitor (Dell 1704 FPV).  I have added the following modeline information after Option   "DPMS" in the Section Monitor 

 # V-freq: 56.00 Hz  // h-freq: 59.34 KHz
 Modeline "1280x1024" 99.69  1280 1336 1456 1680  1024 1024 1026 1059

Even after all of this -- I am still stuck with the 1024x768 as the maximum resolution I can choose.  

What ideas do you you have out there?
Below is the Section on Monitor, Device and Screen from xorg.conf

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
 # V-freq: 56.00 Hz  // h-freq: 59.34 KHz
Modeline "1280x1024" 99.69  1280 1336 1456 1680  1024 1024 1026 1059
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

](*,)

---

### Post by rai4shu2 on 2007-01-12
Looks like you missed a spot:

> **chaplanger said:**
> 
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

](*,)

---

### Post by Albi on 2007-01-12
The easiest way I find is to run sudo dpkg-reconfigure xserver-xorg
And when it asks what video modes you want it to use, check what you need.  After it's done that, and it asks about your monitor, select medium, and make 1280x1024 the default resolution

---

### Post by chaplanger on 2007-01-12
Sure did miss that entry.  Now it is corrected to include 1280x1024 -- but still no joy. 

I still have 1024x768 listed as max resolution in System>Preferences?Screen Resolution.

Does the modeline under Section Monitor look right?   This is what the modeline  tool in another thread came up with for the modeline solution when I input the requested numbers.

---

### Post by chaplanger on 2007-01-12
> **Albi said:**
> The easiest way I find is to run sudo dpkg-reconfigure xserver-xorg
And when it asks what video modes you want it to use, check what you need.  After it's done that, and it asks about your monitor, select medium, and make 1280x1024 the default resolution

Albi,
Tried your suggestion and it came up empty -- got the following errors

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070112215157
dexconf: error: cannot generate configuration file; shared/default-x-server not 
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct 
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
david@david-desktop:~$

---

### Post by chaplanger on 2007-01-13
Hmmmmm. . . 

Ubuntu now boots into 1280x1024 resolution.

This time during start-up:  Ubuntu went from its normal (6.10) loading screen and momentarily brought up an NVidea screen before brining me to the login page.  It waws at this point that the resolution was changed!

Why now?  and Not previously even though the system had been rebooted after other changes?
I'm just "newbie" hoping that everything is now in order and that I won't be experiencing a future message of cannot load x.

Obviously it is working and I am happy with that, just wish I knew why it was working now. . .  Situation Resolved!

---

