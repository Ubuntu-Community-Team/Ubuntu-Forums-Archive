---
title: "I need help with WINE performance"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-12-26
How can I allow WINE to use more memory? If I run one program it's fine, but 2 and the first gets sketchy. It becomes hard to click things and such. Some programs randomly close windows. 

I think memory is the problem, so what can I do. I tried making the .exe process +2 but it only helped a little.

Any idears?

---

### Post by spiderbatdad on 2007-12-26
what drivers are you using, nvidia-glx?

---

### Post by tdrusk on 2007-12-26
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

I don't think I am using anything special... The graphics worked out of the box.

---

### Post by spiderbatdad on 2007-12-26
looks like xgl is supposed to provide support for your card.[https://secure-support.novell.com/KanisaPlatform/Publishing/838/3665840_f.SAL_Public.html](https://secure-support.novell.com/KanisaPlatform/Publishing/838/3665840_f.SAL_Public.html)

but I'm not sure xserver-xgl is what your looking for to run games like wow. It might be. is that what your after? if it is, isnt there a selection for rendering oh the start up page?

---

### Post by spiderbatdad on 2007-12-26
sorry. updated link above.

---

### Post by tdrusk on 2007-12-26
> **spiderbatdad said:**
> looks like xgl is supossed to provide support for your card.[https://secure-support.novell.com/KanisaPlatform/Publishing/838/3665840_f.SAL_Public.html](https://secure-support.novell.com/KanisaPlatform/Publishing/838/3665840_f.SAL_Public.html)

but I'm not sure xserver-xgl is what your looking for to run games like wow. is that what your after? if it is, isnt there a selection for rendering oh the start up page?

ok I installed xserver-xgl

I am using it to play on carbon poker. It's not supported but it runs the way I describe.

what should I do now?

---

### Post by spiderbatdad on 2007-12-26
I may have steered you wrong. I assumed you were having trouble rendering 3-D graphics, when  you may be getting slow response from the server. xserver-xgl is just another server from xorg and may not do anything good for you. it is useful for rendering effect for compiz.
 Sorry for the confusion, and most of the drivers i see are related to xserver.

---

### Post by tdrusk on 2007-12-26
> **spiderbatdad said:**
> I may have steered you wrong. I assumed you were having trouble rendering 3-D graphics, when  you may be getting slow response from the server. xserver-xgl is just another server from xorg and may not do anything good for you. it is useful for rendering effect for compiz.
 Sorry for the confusion, and most of the drivers i see are related to xserver.

okay. I'll remove it then.

Thanks for your help.

Any more ideas?

---

### Post by spiderbatdad on 2007-12-26
buy another 512!

---

### Post by tdrusk on 2007-12-26
Is that guaranteed to help?

If so I'm game.

---

### Post by spiderbatdad on 2007-12-26
you might at least try xgl by rebooting and enabling "custom" visual effects before removing it.

---

### Post by spiderbatdad on 2007-12-26
> **tdrusk said:**
> Is that guaranteed to help?

If so I'm game.


I'm not smart enough to make any guarantees.

---

### Post by tdrusk on 2007-12-26
> **spiderbatdad said:**
> you might at least try xgl by rebooting and enabling "custom" visual effects before removing it.
how do I do this?

---

### Post by spiderbatdad on 2007-12-26
System>>Administration>>Preferences>>Appearances>>Visual Effects>>Custom. After reboot.  You mean to tell me you have not been caught up in all the compiz rage?   Maybe get gnome-compiz-manger from synaptic. it allows you to put a launcher in the tray and turn gl effects on and off. I think I've gotten you in deep. when all you wanted to do was speed up your poker game in wine.:confused:

---

