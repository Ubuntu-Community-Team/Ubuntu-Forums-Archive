---
title: "no sound lspci included"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Caton420 on 2007-08-27
hello im not sure where to begin this process but i have zero sound
lspci brings up nothing that looks like audio hardware but idk
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
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
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

### Post by ddrichardson on 2007-08-27
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=415821&page=3"), let us know how you got on.

---

### Post by Caton420 on 2007-08-27
im confused, i get that same error, i use the code and it just says that error at the top of the page > ERROR: Module snd_hda_intel is in use

---

### Post by ddrichardson on 2007-08-27
Is that when you enter the first command (the rmmod)? If so then you probably need to shut down alsa first.```
[SIZE=-1]sudo /etc/init.d/**alsa**-utils **stop
```**[/SIZE]

---

### Post by Caton420 on 2007-08-27
```
caton420@caton420-laptop:~$ sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: get_control:209: Cannot read control info '2,0,0,Capture Mux Volume,0': Invalid argument'...                                                                                    amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
                                                                         [fail]
caton420@caton420-laptop:~$ 

```
i take it this is bad

---

### Post by Caton420 on 2007-08-27
and it still gives same error for the rmmod

---

### Post by Caton420 on 2007-08-27
bump, bump, bump, thats the sound of my post bouncin to the top

---

