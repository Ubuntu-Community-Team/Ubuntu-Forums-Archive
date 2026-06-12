---
title: "no audio after install"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Caton420 on 2007-08-29
hey im a newb, but i have no sound after a 7.04fiesty install
```
caton420@caton420-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
***_00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)_***
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
caton420@caton420-laptop:~$ 

```

---

### Post by viciouslime on 2007-08-29
Try going to the Applications/Accessories/Terminal and entering "alsamixer" play around with all the bars (you'll be able to scroll to the right and see more bars too. Use the arrow keys on your keyboard to move around.

Once you're certain it isn't just a volume settings issue, try posting a bug on launchpad.

---

### Post by Caton420 on 2007-08-29
```
caton420@caton420-laptop:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument

```
this sucks

---

### Post by Caton420 on 2007-08-29
it worked in a previous install from the same disk...

---

### Post by viciouslime on 2007-08-29
Hmmmm i'm afraid you might need someone with more sound-card-technical-know-how sounds like there is some sort of fundamental bug here. Can you get it to play sound on the live cd? Maybe your install is just corrupt in some way...

---

### Post by Caton420 on 2007-08-29
iv gone through far to much to reinstall, idk if audio works on live cd, but when i do sound test with it, it makes no sound, but i did that last time but it worked after install
im sure this is somthing stupid so someones gotta have at least an idea other than reinstall

---

### Post by siralphred on 2007-08-29
> **Caton420 said:**
> iv gone through far to much to reinstall, idk if audio works on live cd, but when i do sound test with it, it makes no sound, but i did that last time but it worked after install
im sure this is somthing stupid so someones gotta have at least an idea other than reinstall

double click the volume icon and play with the mixer or go Preference and Sound....

---

### Post by Caton420 on 2007-08-29
thats a no-go

---

### Post by xxhaloownerxx on 2007-08-29
Same thing happend to me, v 7.04 apperantly supports little to no sound cards/drivers. irratiting. if it still dosnt work, go to v6.01. that one works for me.

---

### Post by Caton420 on 2007-08-29
really... how can i backup my settings?

---

### Post by viciouslime on 2007-08-30
> **Caton420 said:**
> really... how can i backup my settings?

Just back up everything in your home folder. If you press ctrl+h in nautilus you will see lots of folders that start with a "." these are hidden folders. In these folders, all your settings are stored. A good idea is to creat a separate partition on your hard drive for your home directory, then you can reinstall ubuntu as often as you want and never loose any of your settings.

Since you probably haven't done this though, just copy your entire home directory elsewhere, a cd, another computer, etc. reinstall, then copy it back. Make sure you copy the folders starting with a "." too!

---

