---
title: "ATI Mobile HD 4850 not used by LTS 14.04 on iMac10.1"
date: 2016-03-12
forum: Apple Hardware Users
---

### Post by Tobbel on 2016-03-12
Hello Guys!


i got an imac 10.1 (late 2009) and the Ubuntu installation worked pretty fine. 
Afterwards i checked the used drivers/modules and was confused that "lshw -c video" returned:
```

  *-display UNCLAIMED            description: VGA compatible controller
       product: RV770/M98L [Mobility Radeon HD 4850]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       [...]
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d0220000-d022ffff ioport:1000(size=256) memory:d0200000-d021ffff
 
```


So i went to investigate and in lspci the vga module is not loaded, but the HDMI Audio is:
```

  02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770/M98L [Mobility Radeon HD 4850] (prog-if 00 [VGA controller])        Subsystem: Apple Inc. Device 00b5
        [...]
        Capabilities: <access denied>




02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
        Subsystem: Apple Inc. Device aa30
        [...]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

```


ALso in /var/log/Xorg.0.log i can see my system begins with loading different Modules for the ATI Card. Its loading the "fglrx", "vesa", "ati" and "radeon" but all of them get Unloaded/deleted
```

[     7.255] (EE) Screen 0 deleted because of no matching config section.
[     7.255] (II) UnloadModule: "radeon"

```


I Tried to add a xorg.conf, but nothing changed.
```

Section "Device"
  Identifier  "Configured Video Device"
  Driver              "radeon"
EndSection

```

I have no Idea where to look next...
Anyone got a suggestion, idea or a hint?
Thanks!


Regards, Tobbel!

---

### Post by howefield on 2016-03-12
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ajgreeny on 2016-03-12
AMD has stopped sup[porting the 3xxx and 4xxx series of graphics cards with the fglrx proprietary driver so you should remove that as it may be causing confusion in the system.

Normally you want the radeon driver for the card you have; I assume this will all be the same in an apple hardware system as it is in other PCs.

---

### Post by Tobbel on 2016-03-12
hi, 
would love to do it , but its not even installed.
```

[     7.247] (II) LoadModule: "fglrx"
[     7.247] (WW) Warning, couldn't open module fglrx
[     7.247] (II) UnloadModule: "fglrx"
[     7.247] (II) Unloading fglrx
[     7.247] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     7.247] (II) LoadModule: "ati"
... and so on ...

```
Via dpkg i can see the open drivers should be installed via the xorg package:
```

tweber@tobis-iMac ~ $ dpkg -l \*fglrx\*
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
un  fglrx-glx           
tweber@tobis-iMac ~ $ dpkg -l \*radeon\*
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
ii  libdrm-radeon1:amd64                         2.4.64-1~ubuntu14.04.1      amd64                       Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                          2.4.64-1~ubuntu14.04.1      i386                        Userspace interface to radeon-specific kernel DRM services -- runtime
un  radeontool                                   <none>                      <none>                      (no description available)
un  xserver-xorg-video-radeon                    <none>                      <none>                      (no description available)
ii  xserver-xorg-video-radeon-lts-vivid          1:7.5.0-1ubuntu2~trusty1    amd64                       X.Org X server -- AMD/ATI Radeon display driver

```

Any ideas?

Regards

---

