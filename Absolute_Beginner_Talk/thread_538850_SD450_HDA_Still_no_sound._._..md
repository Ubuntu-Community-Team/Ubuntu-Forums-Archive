---
title: "SD450 HDA Still no sound. . ."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by -=WaLrUs=- on 2007-08-30
Ok, I have  updated my Alsa drivers and libs to 1.0.14.rc4.

I now have lots of sliders to play with and options,  however no matter what combinations I try still no sound!

lspci returns:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
08:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:07.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
08:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)


Any ideas?

---

### Post by -=WaLrUs=- on 2007-08-30
should reqad SB450.

---

### Post by apparle on 2007-09-05
I have the same south bridge IC SB450.
I am unable to hear any sound I get
alsamixer: function snd_ctl_open failed for default: No such device
Please tell me how to update alsa drivers

---

