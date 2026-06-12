---
title: "[PPC] HOWTO - Get X running on a 2nd graphics card (radeon, x86-BIOS)"
date: 2017-06-16
forum: Apple Hardware Users
---

### Post by ernsteiswuerfel on 2017-06-16
It really took me a while to get this going... But with help from #gentoo-powerpc IRC, information from various forums and [https://bugs.freedesktop.org](https://bugs.freedesktop.org) I finally made it! :guitar: Some things were not very obvious for me, and I suppose other users may have a hard time too, getting their 2nd graphics card to work, especially on Apple PPC hardware. So I thougt it would be a good idea to share this information.

One very unfortunate thingy about Apples PPC-era is, that you are more or less nailed to a card with a special Mac-BIOS. Linux or other OSes like MorphOS do not require these special Mac-cards by themselves. But no Mac-BIOS means no OpenFirmware-bootprompt, means you loose the ability for a bootmenu, means your Mac will boot up blindly (that is, if it boots at all after you have changed something in your setup). In my case the G5 11,2 I am using won't boot up at all, if it does not find a Mac-card connected to a monitor... :mad: There are of course 2nd hand Mac-cards available, but the powerful ones have gotten REALLY expensive lately... So the idea is to use an el-cheapo Mac-BIOS-card for booting up your Mac and getting the OpenFirmware bootmenu AND use a common x86-BIOS one as second graphics card for the console and X. The good thing is, common x86-BIOS cards are cheaper AND more powerful than the (old) Mac-cards! Working Radeon cards are in the r300-r600 range, cards requiring radeonsi or amdgpu driver will not work at the moment ([klick]("https://bugs.freedesktop.org/show_bug.cgi?id=99859")). These cards may work with the modesetting driver, or fbdev driver (resorting to fbdev does not make much sense for a 2nd card, as you only get an unaccelerated desktop).

My setup is a PowerMac G5 11,2 with a Nvidia GeForce 6600 (Mac-BIOS) in the first x16-PCIe slot and an AMD Radeon 5450 (x86-BIOS) in the second x8-PCIe slot. I use both cards on the same monitor, which has two HDMI-in.
I use yaboot as boot-manager for booting Gentoo and Ubuntu Linux. **If you want to make use of both cards, this HOWTO is not for you - you should look into Xorg PRIME** ([klick]("https://wiki.archlinux.org/index.php/PRIME")). I need the first card only for the OF bootmenu or for booting into  OpenFirmware itself. Afterwards I have no use for it, I want to drive  the console and X exclusively on the 2nd card.

**First step** is to learn about the graphic cards in your system:
```
# sudo lspci | grep -i vga
0000:0a:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600] (rev a2)
0001:06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
```
Yep, the GeForce is the 1st card in my G5, Radeon is the 2nd one. The numbers at the start of the line are the **BusIDs**. You need to know the BusID for the card you want to run X on later. In my case this is 0001:06:00.0.

**Second step** is to get get the kernel boot parameters right - in a way that only the card you want to use for X and console gets a framebuffer. In my case it looks like this:
```
video=offb:off video=nouveaufb:off video=radeonfb:off nouveau.modeset=0 radeon.modeset=1
```
Which translates to: Don't use the OpenFirwmare-Framebuffer, don't use the (legacy) Nvidia-Frambuffer, don't use the (legacy) Radeon-Framebuffer, don't load the Nvidia DRM-module, but _do_ load the Radeon DRM-module. To actually use this kernel boot parameters, you have to write them in your **/etc/yaboot.conf **first. Look out for the lines where your kernel is actually booted, which may look like this:
```
image=/vmlinux
    label=ubuntu
    read-only
    initrd=/initrd.img
    append="root=/dev/sda5"
```
The *append=* line is what you are looking for. Add your boot parameters like this:
```
image=/vmlinux
    label=ubuntu
    read-only
    initrd=/initrd.img
    append="root=/dev/sda5 video=offb:off video=nouveaufb:off video=radeonfb:off nouveau.modeset=0 radeon.modeset=1"
```
Save your yaboot.conf, and write it to disk:
```
# sudo ybin -vybin: Finding OpenFirmware device path to `/dev/sda2'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda2...
ybin: Installing /etc/yaboot.conf onto /dev/sda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
```
After that your setup is configured in a way, that it should still boot up with the OpenFirmware bootmenu shown on your 1st card. When the Linux kernel is loaded succesfully, it will switch the console output to your 2nd graphics card (and to the monitor whereever your 2nd card is connected to). [B]But don't reboot now, you need an xorg.conf first to get X properly started!

Third step[/B] is, to get yer **/etc/X11/xorg.conf** now. This was a bit a pain in the ass for me to get it right, but once you got it, it looks pretty simple. ;)
```
Section "ServerFlags"
     Option "AutoAddGPU" "false"    
EndSection

Section "Device"
    Identifier             "card_x86"
    Driver                 "radeon"
#    Driver                 "modesetting"
#    Option                 "AccelMethod" "glamor"
    BusID                  "PCI:6@1:0:0"
EndSection
```
That's all.
[I]
"AutoAddGPU" "false"[/I] _tells X to not set up cards automatically_, but as you specify in the "Device" section. The "Device" section tells X which card to actually use. You need to know the **BusID** you got from *lspci | grep -i vga*. Normally I would use "PCI:6:0:0" as suitable BusID for my Radeon - which works fine with the modesetting driver. However the radeon driver wants the BusID in the more strict format "bus[@domain]:device[:func]", which in my case is "PCI:6@1:0:0". Nexct you need to know the **Driver** for your card, which in my case is "radeon" (for all Radeons starting from r100 up to radeonsi). If the proper driver for your card does not work at all or has flaws you can try "modesetting" as driver, which is a generic OpenGL-based driver, included in (recent) xorg-server itself.

The two lines with a **#** at the beginning means they are commented out. I used them for testing. My Radeon HD 5450 works with both "radeon" and "modesetting" driver. Within the radeon driver I can choose between "glamor" and "exa" acceleration methods. My card runs just fine with default options, which is glamor acceleration. If you want to learn more about your driver and the options it provides use **man radeon** (or man modesetting, man nouveau, etc.).

**Fourth step** is to reboot:
Ok, so if you got your /etx/X11/xorg.conf, modified your /etc/yaboot.conf and have written it to disk via ybin -v **double check it**! And then reboot. If you are lucky you will boot straight into your desktop to the monitor connected to your card of choice. ;)

You can then proudly check the more modern (compared to your Mac-BIOS card) features of your card:
```
$ glxinfo | grep -i opengl
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CEDAR (DRM 2.49.0 / 4.10.17-gentoo)
OpenGL core profile version string: 3.2 (Core Profile) Mesa 17.1.2
OpenGL core profile shading language version string: 1.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.1.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.1.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```

**If something goes wrong:**
Don't panic. There are three possible outcomes, where only one is really bad.
1.) You got the kernel parameters wrong. This means the fb0 framebuffer is handed over to the wrong card. Your xorg.conf probably will neither work in this case. BUT there is a working framebuffer somewhere, most probably on the other card. So just check the monitor where the other card is connected and use the console there for further diagnosis.
2.) You got the kernel parameters right, but X won't start. The display should switch to the monitor connected to your 2nd card and you should get to a console prompt there. Start here for further diagnosis. Most probably X does not like something about your card. Check /var/log/Xorg.0.log to find out what. You could change your xorg.conf to use the "modesetting" driver and see if that works after restarting X.
3.) You got the kernel parameters right, X starts but completely freezes the machine shortly afterwards. This is rather bad. You could check if the machine is still usable via ssh from another machine. If so, it's not that bad - you can do diagnosis and change settings via ssh from the other machine.
4.) You got the kernel parameters technically right, but the machine freezes anyway. This is really bad. It most probably means that the Linux kernel you run does not like your card at all. You can only bypass this by trying a more recent kernel. But to get at that stage, you have to boot your machine from some other medium (USB, DVD) and do the rescue work from there.

**Diagnosis:**
You can do diagnosis via console of the machine itself (**CTRL-ALT-F1**, if you got a working console) or via ssh-login from another machine.

Check if the framebuffer of your card gets activated and wether there are other framebuffers.
```
# dmesg | grep -i frame
[   13.190295] Console: switching to colour frame buffer device 240x67
[   13.202694] radeon 0001:06:00.0: fb0: radeondrmfb frame buffer device
```
Looks good to me - only one framebuffer loaded, and it's fb0 as I want it to. If there are others, e.g. fb1 you need to modify your kernel boot parameters. If there is no fb0 at all, there is something wrong with the kernel module of your card.

Check if the kernel module (drm) of your card gets properly loaded:
```
# dmesg | grep -i drm
[    9.830063] [drm] Initialized
[   11.314970] [drm] radeon kernel modesetting enabled.
[   11.315347] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68F9 0x1787:0x2291 0x00).
[   11.315391] [drm] register mmio base: 0x80140000
[   11.315394] [drm] register mmio size: 131072
[   11.433393] [drm] GPU not posted. posting now...
[   11.436996] [drm] Detected VRAM RAM=512M, BAR=256M
[   11.436999] [drm] RAM width 64bits DDR
[   11.437212] [drm] radeon: 512M of VRAM memory ready
[   11.437216] [drm] radeon: 1024M of GTT memory ready.
[   11.437229] [drm] Loading CEDAR Microcode
[   12.592410] [drm] Internal thermal controller with fan control
[   12.601957] [drm] radeon: dpm initialized
[   12.611899] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   12.692922] [drm] PCIE GART of 1024M enabled (table at 0x000000000014C000).
[   12.694290] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   12.694293] [drm] Driver supports precise vblank timestamp query.
[   12.694431] [drm] radeon: irq initialized.
[   12.711728] [drm] ring test on 0 succeeded in 0 usecs
[   12.711746] [drm] ring test on 3 succeeded in 3 usecs
[   12.887255] [drm] ring test on 5 succeeded in 1 usecs
[   12.887352] [drm] UVD initialized successfully.
[   12.888474] [drm] ib test on ring 0 succeeded in 0 usecs
[   12.888673] [drm] ib test on ring 3 succeeded in 0 usecs
[   13.038489] [drm] ib test on ring 5 succeeded
[   13.040956] [drm] Radeon Display Connectors
[   13.040964] [drm] Connector 0:
[   13.040967] [drm]   HDMI-A-1
[   13.040970] [drm]   HPD2
[   13.040978] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   13.040981] [drm]   Encoders:
[   13.040984] [drm]     DFP1: INTERNAL_UNIPHY1
[   13.040987] [drm] Connector 1:
[   13.040990] [drm]   DVI-I-1
[   13.040992] [drm]   HPD4
[   13.040996] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   13.040999] [drm]   Encoders:
[   13.041002] [drm]     DFP2: INTERNAL_UNIPHY
[   13.041005] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.041008] [drm] Connector 2:
[   13.041010] [drm]   VGA-1
[   13.041013] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   13.041017] [drm]   Encoders:
[   13.041019] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   13.162100] [drm] fb mappable at 0x9034D000
[   13.162117] [drm] vram apper at 0x90000000
[   13.162124] [drm] size 8294400
[   13.162129] [drm] fb depth is 24
[   13.162134] [drm]    pitch is 7680
[   13.202694] radeon 0001:06:00.0: fb0: radeondrmfb frame buffer device
[   13.203077] [drm] Initialized radeon 2.49.0 20080528 for 0001:06:00.0 on minor 0
```
Looks good to me. If there the [drm] of the other card gets loaded you have to modify your kernel boot parameters.

If you got the console working on fb0 on the card you want, the only place where there are some problems left is your /etc/xorg.conf. Check what X tells you when starting up:
```
sudo less /var/log/Xorg.0.log
```

---

