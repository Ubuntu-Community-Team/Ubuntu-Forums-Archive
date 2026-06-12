---
title: "[amdgpu-pro] Apple Mac Pro 6,1 running Ubuntu 16.04 (purple blank screen on boot)"
date: 2017-02-16
forum: Apple Hardware Users
---

### Post by iredden on 2017-02-16
Hi,

I installed and am successfully dual booting Ubuntu 16.04 on my Apple Mac Pro 6,1 (note, NOT MAC BOOK PRO, but mac pro -> [http://www.apple.com/ca/mac-pro/](http://www.apple.com/ca/mac-pro/))

After installing, I have the purple screen of death but unlike a Windows BSOD, the system is working (just no video).  I am able to SSH into my ubuntu box.

I installed the official AMDGPU PRO 16.60-379184 as well as the non-beta 16.40.  I still have a purple screen on boot.  My chipset appears to be Tahiti but not 100% sure.  My MacPro has the Dual AMD FirePro D700 with 3GB.  Can't seem to find what chipset that is to confirm whether I'm in the list of supported chipsets for the proprietary AMDGPU-PRO drivers.

If I boot with a 'nomodeset' I can see Unity.

Here is my lspci:
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]

Xinit:
root@MacPro-Ubuntu:~# xinit


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-59-generic x86_64 Ubuntu
Current Operating System: Linux MacPro-Ubuntu 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-36-generic.efi.signed root=UUID=6135cc29-0651-496f-a5b3-0ff688cf7f50 ro quiet splash vt.handoff=7
Build Date: 26 January 2017  12:26:18AM
xorg-server 2:1.18.4-1ubuntu6.1~16.04.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.33.6
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 16 22:15:24 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
(II) [KMS] drm report modesetting isn't supported.
(II) [KMS] drm report modesetting isn't supported.
(EE)
Fatal server error:
(EE) no screens found(EE)
(EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.

/usr/share/X11/xorg.conf.d/10-amdgpu-pro.conf:
Section "OutputClass"
        Identifier "amdgpu-pro"
        MatchDriver "amdgpu"
        Driver "amdgpu"
EndSection

Section "Files"
        ModulePath "/opt/amdgpu-pro/lib/xorg/modules"
        ModulePath "/usr/lib/xorg/modules"
EndSection
```

Any help greatly appreciated!

Ian.

---

### Post by QIII on 2017-02-17
Hello!

I'm unfamiliar with Apple products, but I can say this with regard to your R9 280X:

At present, the AMDGPU driver supports only Graphics Core Next (GCN) 1.2 and later GPUs.  While support is coming for GCN 1.0 and later, I do not believe it is released yet.  Your GPU is First Generation GCN, or GCN 1.0.  Discounting your Apple machine, the card is most likely not yet supported by AMDGPU.

If you forced installation of AMDGPU, I am not surprised that you have problems.  Can you uninstall it (also remove or rename 10-amdgpu-pro.conf) and see if the machine runs with the open source Radeon driver?
.

---

### Post by wildmanne39 on 2017-02-17
*Thread moved to **Apple Hardware Users**.*

---

### Post by luigiburdo on 2017-02-17
try use radeon where   Driver "amdgpu"
if not use fbdev

---

### Post by iredden on 2017-02-17
Neither works.  FBDEV just gives a purple screen.  The xorg reports 'no screens found'.

I have confirmed the chipset of my video card is infact the Tahiti XT.  Apple brands the card as a FirePro D700 which is a upgraded full-blown Tahiti XT chip unlike the D500 or D300.  The card is very similar to the W9000 workstation class card.  I tried the W9000 legacy driver from AMD's site.  It installed fine but failed to show any video (other than the purple screen of death).

Also, I tried installing the mainline 4.9.10 kernel from ubuntu.  This is because there is support for GCN 1.0 but you need to flip the flag in the Kconfig.  

I did that, still no luck.  There must be someone out there that has gotten this to work (accelerated video or not).

Ian.

---

### Post by luigiburdo on 2017-02-19
Hi Ian, 
probably is not supported or need the firmware in kernel. 
the best i can suggest right now is use on your mac virtualbox :P

---

### Post by elproducto on 2017-06-01
Just wanted to add to this post.  I got my Macpro 6,1 Quad Core working with Dual screen monitors output with the latest FGLRX graphic drivers.  I did need to to add nomodeset in GRUB for station to boot to X, without it it will boot to a black screen. Intermittently post install of FGLRX drivers, my MAC Pro boots to a black screen with blinking cursor in the top left. This can be fixed by doing another reboot.  I have to do some more troubleshooting to get to the bottom of the intermittent boot issues.

---

