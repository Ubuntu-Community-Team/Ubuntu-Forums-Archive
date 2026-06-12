---
title: "No Sound after new install of 6.06"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by CarbonFisher on 2006-06-11
Ok, so I recently installed Dapper Drake onto my PC. (Just so you know, it is a dual boot XP...for now).

Most everything works fine, except my sound. I have a Sound Blaster PCI128 (Ensoniq 5880?) which I believe is using snd-ens1371. I've looked through a bunch of posts that came up when I searched, but after trying the few things I could understand, I'm at a loss. Unfortunately, I'm relatively new to Linux, so most threads lost me early on.

A bit about my setup:
AMD Athlon 2800
1 GB RAM
2 Hard drives (One NTFS, one Ubuntu)
Sound Blaster PCI128 w/ Creative SBS 4.1 speakers.
nVidia GForce 5800 video card.

Here's what I *have* done so far:
Opened Volume Control, went to preferences and clicked everthing. Then I made sure *all* of the slider bars are at max. I'm currently using Device 1 (Ensoniq Audio PCI - Alsa), and have two others, 0 being the onboard (Via 8235 ALsa), and 2 being the Ensoniq Audio (OSS).

I've also installed alsamixergui, which looks like (attached screenshot). One thing that's kind of weird...If I turn on the switch labeled IEC958 1, I get static/noise from my speakers.

Following is the output from lspci (which I have no clue what it is, I just saw it):
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0f.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

This is what I get from cat /proc/asound/cards
```

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with AD1980 at 0xe000, irq 193
1 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xd400, irq 201

```

And this is from aplay -l (again, no clue. Just randomly typing stuff I've ssen elsewhere in terminal. I know that's bad XD ):

```

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Now, I did notice that my IRQ's are kind of weird. In XP, my soundcard IRQ is set to 18. Ubuntu has it as 201. And I'm not really sure if or how to change it.

I currently have XMMS and Rythmbox installed, and I believe I properly set up Rythmbox to play mp3's. My understanding is that XMMS plays mp3's out of the box...

So....That is apparently that. Please help me, as sound is really the only thing I'm missing at the moment.

Thanks,
Carbon Fisher

---

