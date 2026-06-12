---
title: "PowerMac G4 graphical interface problems"
date: 2008-04-17
forum: Apple PPC Users
---

### Post by Siborg888 on 2008-04-17
Hello to you all in Ubuntu land.

I recently got hold of a PowerMac G4 (Digital Audio) that I thought would be a good project for learning about Ubunutu Linux and weaning myself off the evil MS empire! 

After various troubles getting the install to go all the way through the process I had success with Ubuntu 7.04 ppc alternate disk.  Installation went all the way through and happily hooked up to the web but when I booted up in Ubuntu for the first time I got a bad blue screen and the following error message...

"Failed to start X server (your graphical interface). It is likely that it is not set up correctly..."

When I look at X server output I get a lot of esoteric text...

"X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mediamac 2.6.20-15-powerpc #3 Sun Apr 15 06:45:49 UTC 2007 ppc

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 16 17:59:03 2008
(WW) ****INVALID IO ALLOCATION**** b:0xf0000400 e: 0xf00004ff correcting^G
(EE) end of block range 0xefffffff < begin 0xf0000000
(**) RADEON(0): RADEONPreInit

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x94) [0x10090c04]
1: [0x100344]
2: /usr/lib/xorg/modules//libint10.so(LockLegacyVGA+0x50) [0xf8caa50]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x300) [0xf8cd690]
4: /usr/lib/xorg/modules//libvbe.so(VBEExtendedInit +0x2eo) [0xf89ea70]
5: /usr/lib/xorg/modules//libvbe.so(VBEInit +0x28) [0xf89ec281]
6: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONProbeDDC +0x48) [0xf791558]
7: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xf79b9c8]
8: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xf79c584]
9: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONPreInit +0xf20) [oxf79d530]                      "  

I've not been able to find anyone having similar problems on the forum so I'd appreciate any help that anyone could provide because I'm not sure where to go from here and I'd really love to get this sucka up and running!  

Much thanks

---

### Post by phalacee on 2008-04-18
I've experienced this same problem with every version of Ubuntu after Dapper. I have two different G4 Macs, an older blue-cased one (400Mhz) and a silver-cased one (800Mhz). Both of them suffer from this fault. I have installed Ubuntu 5.10 and upgraded to 6.06 on one, and the other I installed 6.06 cleanly, and they work fine, but there is no way for me to install 7.04 or 7.10. I've tried Alternate CDs, Install CDs, LiveCDs. I haven't tried 6.10 yet, because I didn't want to install an OS that wouldn't be supported by the end of this month when I could have one that is supported for another 2-3 months still, but I would love to be able to install a newer more recent version on both these Mac's before 6.06 support is dropped.

If anyone could help it would be greatly appreciated, otherwise I'll attempt installing Debian for PPC, and if that fails, Fedora or Gentoo... 

Please, please don't make me use a non-Debian-based Linux.

---

### Post by stream303 on 2008-04-18
Is there anything in the ppc faq that might help the ati / radeon owners:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

I know OswaldKelso has run into this situation before on his mac mini, I'd have to dig up the threads for his nice xorg.conf's...

---

### Post by Siborg888 on 2008-04-18
I found this thread where they seem to be suffering similar problem...[http://ubuntuforums.org/showthread.php?t=531002](http://ubuntuforums.org/showthread.php?t=531002)

which led on to the radeon open source driver page...
[https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1](https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1)

Both offer some heavy weight info, a little hard going for a newbie like me, but they suggest that 7.10 supports the ati radeon 7500. I've given that a try with the alternate ppc install disc which seemed to go ok but when I first booted it up it's dropped me into the BusyBox shell without saying anything about graphical interface problems.  

Damn, fi it's not one thing it's t'other!

---

### Post by Siborg888 on 2008-04-18
Sweet sweet success!!

Entered this code into the BusyBox

```
modprobe ide_core
exit
```

And now it is up and running.

---

### Post by stream303 on 2008-04-18
To make that permanent with ide-core, be sure to:
```
sudo update-initramfs  -u
```

---

### Post by Siborg888 on 2008-04-20
Thanks! I was wondering how to make the change so I didn't have to type it in every time the machine boots.

---

