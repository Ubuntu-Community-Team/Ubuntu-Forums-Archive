---
title: "Blacklist On-Board Audio Card/Controller"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-10-22
Hi I have two sound cards in my computer an on-board and a PCI card. I have gotten this PCI card because my other [audio card]("http://ubuntuforums.org/showthread.php?t=540980") doesn't [work in Ubuntu]("http://ubuntuforums.org/showthread.php?t=502242"). Now I need to disable the old on-board card to force Ubuntu to use the new one, how do I do.

Here is some info:
dmesg | lspci
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:08.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
00:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
I want to disable
> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

I have tried to play around with /etc/modprobe.d/blacklist but I can't figure out how to use it!

Thanks

---

### Post by overdrank on 2007-10-22
Hi and have you tried to just disable the onboard sound in bios of the motherboard?

---

### Post by shad0w_walker on 2007-10-22
Try running this command and output the results, hopefully we can see what modules the card loads.

```
lsmod | grep snd
```

---

### Post by kasperbs on 2007-10-22
> **shad0w_walker said:**
> Try running this command and output the results, hopefully we can see what modules the card loads.

```
lsmod | grep snd
```
here you go, hope that helps.
> lsmod | grep snd
snd_cmipci             37024  0
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_seq_dummy           4740  0
snd_mpu401              9640  0
snd_mpu401_uart         9600  2 snd_cmipci,snd_mpu401
snd_intel8x0           34972  1
snd_ac97_codec        100644  1 snd_intel8x0
snd_seq_oss            33152  0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                80388  5 saa7134_alsa,snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
gameport               16776  2 snd_cmipci,analog
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_opl3_lib,snd_pcm,snd_seq
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54660  18 saa7134_alsa,snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


---

### Post by shad0w_walker on 2007-10-22
By the looks of that, the module you need to black list would be:

```
snd_ac97_codec
```

That should hopefully stop the modules to use the onboard audio from loading.

---

### Post by houstonbofh on 2007-10-22
Do it in the BIOS.  It is cleaner and will save an IRQ.  And later if you want to try it again when it is supported you won't have to hunt for what you changed.

---

