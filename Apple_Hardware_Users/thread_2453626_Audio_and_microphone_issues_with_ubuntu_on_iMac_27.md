---
title: "Audio and microphone issues with ubuntu on iMac 27 inch"
date: 2020-11-14
forum: Apple Hardware Users
---

### Post by enjoydambience on 2020-11-14
I recently installed ubuntu 20.04 on an iMac 27 inch (late 2015, model identifier iMac17,1).
Everything works great except for audio.

By default, the audio quality was bad and sounded muffled.
I later added "options snd-hda-intel model=imac27" to "/etc/modprobe.d/alsa-base.conf". This improved audio quality (still worse than native mac), but now the internal microphone isn't being picked up at all.
The microphone was working fine before I changed alsa-base.conf; reverting "alsa-base.conf" also magically makes the microphone work again.

Is there a way so I don't have to choose between audio quality and a working microphone? I already dug through half the internet and can't find a working solution.

Still a ubuntu/linux newbie, but have been reading lots of documentation/forums.

Additional info below:

Output of "cat /proc/asound/card0/codec* | grep Codec" is "Codec: Cirrus Logic CS4206"

Optut from inxi -SMA:
```

System:
  Host: linuxintosh Kernel: 5.4.0-53-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Apple product: iMac17,1 v: 1.0 
  serial: <superuser/root required> 
  Mobo: Apple model: Mac-DB15BD556843C820 v: iMac17,1 
  serial: <superuser/root required> UEFI: Apple v: 428.0.0.0.0 
  date: 06/16/2020 
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio 
  driver: snd_hda_intel 
  Device-2: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 
  Series] 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-53-generic 

```

Output of lspci:
```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1b.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #17 (rev f1)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #2 (rev f1)
00:1c.4 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Z170 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series]
02:00.0 Mass storage controller: Apple Inc. S1X NVMe Controller (rev 01)
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC (rev 01)
04:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe (rev 01)
04:00.1 SD Host controller: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader (rev 01)
05:00.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:00.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:03.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:04.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:05.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
06:06.0 PCI bridge: Intel Corporation DSL5520 Thunderbolt 2 Bridge [Falcon Ridge 4C 2013]
07:00.0 System peripheral: Intel Corporation DSL5520 Thunderbolt 2 NHI [Falcon Ridge 4C 2013]

```

---

### Post by wildmanne39 on 2020-11-14
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

