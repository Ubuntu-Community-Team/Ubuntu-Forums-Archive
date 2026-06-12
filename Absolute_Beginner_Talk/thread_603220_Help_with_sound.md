---
title: "Help with sound"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by sicknature on 2007-11-04
I'd just gotten Ubuntu to work on my system, the only thing left is my sound card. When I choose ALSA, my sound level is always mute and I'm unable to change it. But when I change it to OSS, the volume is either 100% or mute. I can't select anywhere in between. Sound test doesn't work for me, none of the application produce any sound at all. 

This is what I get for lspci:
> 00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
02:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

and this si what I get for lsmod | grep snd
> snd_ice1724            78220  1 
snd_ice17xx_ak4xxx      5120  1 snd_ice1724
snd_ac97_codec        100644  1 snd_ice1724
ac97_bus                3200  1 snd_ac97_codec
snd_ak4114             10880  1 snd_ice1724
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_pt2258              5248  1 snd_ice1724
snd_i2c                 6656  2 snd_ice1724,snd_pt2258
snd_ak4xxx_adda         8832  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_mpu401_uart         9600  1 snd_ice1724
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_pt2258,snd_i2c,snd_ak4xxx_adda,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd


PS: I'm using toslink out from my sound card. I'd try installing ALSA guimixer and such from synaptic package managers, nothing helps. Please help me! Thank you!! :)

---

### Post by sicknature on 2007-11-05
anyone able to help me?

---

