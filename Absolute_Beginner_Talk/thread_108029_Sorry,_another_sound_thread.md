---
title: "Sorry, another sound thread"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by derekho55 on 2005-12-24
Hi,

I currently have a Kubuntu 5.10 on my Sony Vaio (VGN-B100B) laptop. From the very beginning, since installation, I did not have any sound. 

Here is my lspci:
```

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:02:04.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
0000:02:0b.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

```

And here is my lsmod | grep snd:

```

snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

```

I recently installed the ALSA 1.0.10, thinking that it would help solve my problem. But it didnt.

Please help!

---

### Post by Badojo on 2005-12-24
Well first off it would be good to check the wiki as I always say but did you try opening up volume control at all? if not turn everything thing up and mess around with it and it might start working.

---

### Post by derekho55 on 2005-12-24
I heard about volume control.. but I don't know how to do it in Kubuntu. Can you give me the code?

If you are talking about alsamixer, I have all possible things on (Master, Mic, etc)

Thanks for replying though

---

### Post by derekho55 on 2005-12-24
Oh, and when I go to system settings through "sudo system settings", and I try to "Test sound" in the "Sound & Multimedia"  General tab, the console gives me "Unable to connect to sound server." 

Just something that I think I should disclose.

Any advice would be appreciated. Thanks

---

