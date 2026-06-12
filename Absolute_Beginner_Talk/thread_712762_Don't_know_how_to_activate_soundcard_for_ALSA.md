---
title: "Don't know how to activate soundcard for ALSA"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-02
I was going through the ALSA troubleshooting page making sure everything was checking out okay until I got to the part about making sure that the drivers for my card were active.

[http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting)

"Make sure that /proc/asound/cards lists your card"
I checked the file and it is completely blank. So my question is, how exactly do I go about activating it.

I just compiled the newest versions of the ALSA drivers, utlities, and libraries.

---

### Post by Shazaam on 2008-03-02
Desktop? Laptop? On-board or add-in card?
Open terminal (Applications>Accessories>Terminal), type this in and post the output here.....
```
lspci
```
This code will ouput your hardware list.

---

### Post by elchico04 on 2008-03-02
```
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:0a.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
```


00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
^thats the sound card im trying to install.

---

### Post by arimaniac on 2008-03-03
Hi there

"C-Media Electronics Inc CM8738 (rev 10)"
is also my card BUT (rev 07) 

[SIZE="4"]DRIVERS FOUND BUT LOTS OF PROBLEMS TOO[/SIZE]

I installed a PCI one and got rid of this

MINE IS ON BOARD, IF YOURS IS TOO SEE THIS:

Complete HOWTO on disabling your on-board card

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

Please reply with your
comments to improve the HOW TO...

Hope it helps....

---

