---
title: "Garbled sound from microphone."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by RobMunda on 2007-07-29
Hiya,

  First let me thank everyone here for volunteering your time. I know it's hard work sometimes and I, for one, appreciate what you do. Once I learn more about Unbuntu, I will try to help out when I can. For now, however, I was wondering if anyone could help me sort out a problem I'm having with my microphone.

  I am running Feisty on a Compaq Presario notebook (V5201US model, if that helps). I do realize that laptops sometimes exhibit strange behavior, due to their proprietary hardware, so I'm not sure if this issue is resolvable or not. I would like to use my microphone if I can, but if I can't, it's a very small price to pay to not have the headaches I had when I was using WinXP. So, if you can help me, I'll be grateful. If the proprietary hardware isn't compatible, I just won't record on my laptop.

  When playing media (CDs, DVDs, MP3s, games, etc.) everything sounds completely normal. However, if I try to record using a microphone, the sound is either nonexistent, or there is a lot of static and the sound is garbled. In other words, I'm fairly certain that the microphone isn't sending the right signals to the recording program(s). The sound card seems to function properly otherwise.

  I enabled recording from microphone in the Volume Controls (before trying to record) and the Recording Level Monitor shows activity when I turn it on. However, when trying to record using Sound Recorder, the program doesn't seem to be aware of the microphone. It other words, it doesn't show any recording progress after clicking Record. Playback doesn't seem to work (because I don't think it has recorded anything) so I went to Audacity.

  I tested different settings by changing to different inputs in Audacity, which is why there are differing results mentioned above. The settings available are as follows:
OSS /dev/dsp 
OSS, /dev/dsp1
ALSA: ATI IXP: ATI IXP AC97 (hw:0,0)
ALSA: ATI IXP Modem: ATI IXP MC97 (hw:1,0)
ALSA: Front

  I noticed in another topic that lspci is handy for a situation like this, so to save some time here is the result(s) of lspci for my computer:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

  I should probably mention that I've tried more than one microphone in the jack. This was to eliminate the microphone itself as the problem. So what would be the next step for me?

Thanks in advance,
-Rob.

---

### Post by Efrain Valles on 2007-08-24
Same situation here... :(

My model is a m2000... but it has the same hardware...

:confused:

---

