---
title: "intel MUX info called failed on Optimus laptop"
date: 2011-09-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ongchinonn on 2011-09-14
My laptop is a optimus laptop. i installed ironhide and do some upgrade, and disable nvidia card on reboot.     
On next boot, then i can't log in using Unity, i saw there is Error on Intel MUX info, below is my /var/log/dmesg.0. Anybody have any clue on this?
Thanks.

I try to do ironhide-bugreport but it said can't connect to internet. 

> 
[    2.998144] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.998148] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.998149] [drm] Driver supports precise vblank timestamp query.
[    3.024953] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    3.024998] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    3.088270] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    3.088279] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    3.111077] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.167787] fbcon: inteldrmfb (fb0) is primary device
[    3.167821] Console: switching to colour frame buffer device 170x48
[    3.167837] fb0: inteldrmfb frame buffer device
[    3.167838] drm: registered panic notifier


in Xorg.log - the final line is this  
> 
[    65.914]  ddxSigGiveUp: Closing log


---

### Post by get2gether on 2011-10-17
Could i suggest maybe your problem is the nouveau driver (open source nividia driver) still installed? You have disabled your nividia card, so i presume your trying to run on the intel chip?

---

