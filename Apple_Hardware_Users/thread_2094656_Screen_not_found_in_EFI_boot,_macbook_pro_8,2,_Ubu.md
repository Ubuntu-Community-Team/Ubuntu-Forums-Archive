---
title: "Screen not found in EFI boot, macbook pro 8,2, Ubuntu 12.10"
date: 2012-12-14
forum: Apple Hardware Users
---

### Post by sunpho on 2012-12-14
Hi all,

I installed ubuntu 12.10 on my mac book pro 8,2 using the normal installer of the amd64+mac release (ubuntu-12.10-desktop-amd64+mac.iso). The installation works pefectly, but in order to be able to use the intel graphic card in place of the RADEON, I have to make the EFI boot. Using "boot-repair" I installed Grub-efi, and using rEFInd I managed to get to the grub-efi menu.

The problem is that during X initialzation I get a message saying that X cannot be start.
I attach here the fundamental part of Xorg log: 

> 
[    13.417] (II) intel(G0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    13.417] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    13.417] (==) intel(G0): RGB weight 888
[    13.417] (==) intel(G0): Default visual is TrueColor
[    13.417] (--) intel(G0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    13.417] (**) intel(G0): Relaxed fencing enabled
[    13.417] (**) intel(G0): Wait on SwapBuffers? enabled
[    13.417] (**) intel(G0): Triple buffering? enabled
[    13.417] (**) intel(G0): Framebuffer tiled
[    13.417] (**) intel(G0): Pixmaps tiled
[    13.417] (**) intel(G0): 3D buffers tiled
[    13.417] (**) intel(G0): SwapBuffers wait enabled
[    13.417] (==) intel(G0): video overlay key set to 0x101fe
[    13.417] (II) intel(G0): Output VGA1 has no monitor section
[    13.418] (II) intel(G0): Output HDMI1 has no monitor section
[    13.468] (II) intel(G0): Output DP1 has no monitor section
[    13.468] (II) intel(G0): EDID for output VGA1
[    13.468] (II) intel(G0): EDID for output HDMI1
[    13.516] (II) intel(G0): EDID for output DP1
[    13.516] (II) intel(G0): Output VGA1 disconnected
[    13.516] (II) intel(G0): Output HDMI1 disconnected
[    13.516] (II) intel(G0): Output DP1 disconnected
[    13.516] (WW) intel(G0): No outputs definitely connected, trying again...
[    13.516] (II) intel(G0): Output VGA1 disconnected
[    13.516] (II) intel(G0): Output HDMI1 disconnected
[    13.516] (II) intel(G0): Output DP1 disconnected
[    13.516] (WW) intel(G0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    13.516] (II) intel(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.516] (II) intel(G0): Kernel page flipping support detected, enabling
[    13.516] (EE) intel(G0): No modes.
[    13.516] (II) UnloadModule: "intel"
[    13.516] (EE) Screen(s) found, but none have a usable configuration.
[    13.516] 
Fatal server error:
[    13.516] no screens found
[    13.516] (EE) 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    13.516] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    13.516] (EE) 
[    13.519] Server terminated with error (1). Closing log file.
Looking at dmesg, I found this error:

> 
[   12.741598] i915 0000:00:02.0: >irq 47 for MSI/MSI-X
[   12.741610] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.741611] [drm] Driver supports precise vblank timestamp query.
[   12.741620] i915 0000:00:02.0: >Invalid ROM contents
[   12.741622] [drm] failed to find VBIOS tables
Googling around I noticed various suggestions about adding lines such as "i915.modeset=0" "radeon.modeset=0" etc to the kernel line in grub, but they seems not to have any effect. By the way, the relevant part of grub.cfg goes like this:

> 
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt5'
                if [ x$feature_platform_search_hint = xy ]; then
                     search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  22f63917-22e5-41e0-a525-26a42c30a77f
                else
                     search --no-floppy --fs-uuid --set=root 22f63917-22e5-41e0-a525-26a42c30a77f
                fi
                echo    'Loading Linux 3.5.0-17-generic ...'
                linux   /boot/vmlinuz-3.5.0-17-generic root=UUID=22f63917-22e5-41e0-a525-26a42c30a77f ro   no-splash  $vt_handoff
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.5.0-17-generic
from where you can also infer the kernel version that I'm using (that I got from ubuntu repository).
What do I need to do in order to make X initialize?

Thank you!

---

### Post by Sidolin on 2012-12-14
It's strange that X tries to start using the intel card without you explicitly switching it. Can you post a full dmesg and a cat /sys/kernel/debug/vgaswitcheroo/switch?

Also, try shutting down X and pulseaudio and echo IGD > /sys/kernel/debug/vgaswitcheroo/switch as root.

---

### Post by sunpho on 2012-12-14
Hi Sidolin, thank you very much for your reply. Indeed I realize that I made confusion between the two cases, that is, when I put radeon.modeset=0 in the kernel options, and when I don't. I re-checked, and the situation is slightly different:

-if I put the radeon.modeset=0, I get an error when initializing the intel card, saying that no ROM is found (see previous message), but the initialization continues, up to reaching X start. Not finding any video, X drop to text console, from which I've been able to extrac the info that I sent in the previous message. Vgaswitcheroo is never initialized, since only the intel graphic card is found.
-if I do not put radeon.modeset=0, the situation seems to stuck after that root partition is remounted (at 12.199630 in the attached kern.log), but actually the boot goes on, vgaswithcheroo is enabled, etc, although the system hangs. Unfortunately I do not get any console working (the screen completely stuck) so I cannot test what happens echoing to the /sys/blabla/switch. For the same reason I cannot take the dmesg and /sys/blabla/switch, but I extracted from kern.log the relevant part, that I attach together with Xorg.0.log.

By the way, I notice also that in kern.log at 13.001907 I get: "fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver".
Since this error comes after "BIOS not found", I do not understand what is the cause and what should I try to solve first (and how! :))

Let me know any additional info you need!

---

### Post by Sidolin on 2012-12-15
If you just want to boot with the intel card active and don't really care about switcheroo you could try adding the outb stuff from [http://tech.ivkin.net/wiki/Ubuntu_on_MacBook_Pro_Notes]("http://tech.ivkin.net/wiki/Ubuntu_on_MacBook_Pro_Notes") to your grub config. That switches the ati card off and connects the displays to intel, but might cause problems with suspend/resume.

The BIOS not found errors shouldn't matter, I get those as well. The BIOS is really missing but the card works anyways.

If you want full switching, the first thing to try would be to switch to a recent mainline kernel and see if that changes anything. After that, configure networking to start automatically at boot and try to ssh into your laptop when the screen doesn't work.

---

### Post by sunpho on 2012-12-15
> **Sidolin said:**
> If you just want to boot with the intel card active and don't really care about switcheroo you could try adding the outb stuff from [http://tech.ivkin.net/wiki/Ubuntu_on_MacBook_Pro_Notes](http://tech.ivkin.net/wiki/Ubuntu_on_MacBook_Pro_Notes) to your grub config. That switches the ati card off and connects the displays to intel, but might cause problems with suspend/resume.


Yes!, this worked! Actually I had to adapt a little the suggested commands, indeed the parameter "lvds_channels" after version 3.5.0 of the kernel has been renamed into "lvds_channel_mode". So this is the exact line that I'm using:

```

        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        outb 0x750 0
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=22f63917-22e5-41e0-a525-26a42c30a77f ro nosplash i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 $vt_handoff

```The display goes completely dark, but after ~30 sec ubuntu appears!

I will consider this already a great success, since now I'm writing you from the so-obtained working configuration. I have to investigate which of the kernel lines are truly needed, and whether the suspend/resume functionality works, of course. But, it worked!!! And the battery is expected to discharge within more than 3 hours and a half...

>  The BIOS not found errors shouldn't matter, I get those as well. The BIOS is really missing but the card works anyways.This is an important piece of info, reading around I thought I had to dump the bios and have it loaded...

>  If you want full switching, the first thing to try would be to switch to a recent mainline kernel and see if that changes anything. After that, configure networking to start automatically at boot and try to ssh into your laptop when the screen doesn't work.Yes, in the while I have tried 3.7.0 rc 8 from official ubuntu repository ([http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)), without passing any additional parameter, but this does not seem to work better. What do you suggest to do? Do you expect some patch missing and/or parameters in the kernel to be passed?

In the while: thank you very much!

UPDATE: actually it seems that only the parameters "i915.lvds_channel_mode=2" and "i915.lvds_use_ssc=0" are needed. The parameter "i915.modeset=1 " has no effect, likely because we already passed the mode via "outb". On the contrary googling around I found that "i915.i915_enable_rc6=1" should affect only the power usage of the card, reducing it. I have to investigate on it.
The suspend/resume seems to work, although sometimes when I resume, a program crash is reported, but this does not seem to affect the stability of the machine nor the video. 

Anyway I'm still interested to understand what is needed to make a hybrid graphic card switch. For daily work this integrated-only setup seems the best, but it seems not to perform very well (as expected) when watching video and similars.

What to you suggest to do?

---

### Post by Sidolin on 2012-12-16
A start for getting real switching to work would be to boot just with ```
i915.lvds_channel_mode=2 i915.lvds_use_ssc=0
```, no modeset changes or outbs. These two i915 are necessary to get the display working properly and shouldn't influence switching stuff.

And then check if switcheroo is activated and if you can use it. If the screen goes blank try to get remote access to your laptop. It might be that you have a console but on the wrong card or something similar. But it's hard to debug without more debug output.

---

### Post by sunpho on 2012-12-16
Hi Sidolin, I tried booting using only the two i915 parameters that you suggested, that is:

```

i915.lvds_channel_mode=2 i915.lvds_use_ssc=0

```using the last kernel available on the ubuntu repository, the 3.70-rc8:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/)

By using "nosplash" and removing "quiet" parameters on linux line, I see that the screen freezes just after root remounting. I managed to log in using my old laptop through ssh, and extracted dmesg output, that you find in the attachment. 

As you can see from the log, vgaswithcheeroo get enabled and disabled immediately afterwards, because of some error. It is not clear to me what is the source of panicing. Unfortunately, since vgaswitcheero is not enabled, no dir is present in /sys/kernel so I cannot check what you suggested.

By the way: I checked also with kernel version 3.50-21, and the output is almost the same, in particular there is only one relevant line different more, 

```
radeon 0000:01:00.0: no bo for sa manager
```just after the "[TTM] Memory type 2 has not been initialized" line.

I wonder whether the error can be caused by some wrong initialization command in the graphic part of grub-efi, such as gfxpayload or similar.

---

### Post by ksatta1 on 2012-12-26
I'm also trying to do the same on Macbook Pro 15" Retina (10,1). Haven't tried the kernel patch yet, or i915.x kernel parameters.

I've gotten so far that I get a blank screen when I do switcheroo as in the other thread: [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)

And now the testing continues :) ->

---

### Post by Bakuda on 2012-12-29
Every time i try to run the boot loader install it doesnt detect it at all, and when i try to use the Rockbox utility, it keeps saying error reading partition table possibly not an ipod. I really need help.

---

