---
title: "How to get Altera firmware to load"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by masq-man on 2007-02-17
Greetings,
I have an older Hauppauge Tv card (WinTV PCI) that is almost working in Edgy. The Video works fine, but I suspect that the firmware for the Altera Chip is not loading, and therefor I have no audio. After searching for similar problems  I found a reference to putting the firmware file (hcwAMC.rbf) from the Hauppauge CD into /lib/firmware/2.6.17.11-generic folder and restarting. Still no luck.  If I first boot in windows then restart in linux it does work, but what a pain..

Any suggestions would be appreciated.

Below is the dmesg I think is relevant:
 
[   36.079535] Linux video capture interface: v1.00
[   36.159143] bttv: driver version 0.9.16 loaded
[   36.159147] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   36.159195] bttv: Bt8xx card found (0).
[   36.159672] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   36.159677] GSI 21 sharing vector 0x3A and IRQ 21
[   36.159684] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 58
[   36.159693] bttv0: Bt878 (rev 17) at 0000:04:08.0, irq: 58, latency: 64, mmio: 0xbfefe000
[   36.159704] bttv0: detected: Hauppauge WinTV/PVR [card=80], PCI subsystem ID is 0070:4500
[   36.159707] bttv0: using: Hauppauge WinTV PVR [card=80,autodetected]
[   36.159737] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   36.197881] parport: PnPBIOS parport detected.
[   36.198001] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   36.273688] FDC 0 is a post-1991 82077
[   36.475256] nvidia: module license 'NVIDIA' taints kernel.
[   36.730475] input: PC Speaker as /class/input/input1
[   37.135707] bttv0: no altera firmware [via hotplug]
[   37.224985] tveeprom 0-0050: Hauppauge model 45231, rev C423, serial# 4053259
[   37.224988] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)
[   37.224991] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   37.224994] tveeprom 0-0050: audio processor is MSP3435 (idx 10)
[   37.224996] tveeprom 0-0050: has radio
[   37.224998] bttv0: Hauppauge eeprom indicates model#45231
[   37.225000] bttv0: using tuner=2
[   37.225111] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   37.227243] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   37.229371] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   37.368644] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Logitech QC Communicate STX 
[   37.370143] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   37.451917] ts: Compaq touchscreen protocol output
[   37.498683] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   37.520367] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   37.520397] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   37.550315] bttv0: registered device video0
[   37.550331] bttv0: registered device vbi0
[   37.550344] bttv0: registered device radio0
[   37.550365] bttv0: PLL: 28636363 => 35468950 .<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.568313] . ok
[   37.587072] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 17
[   37.587078] GSI 22 sharing vector 0x42 and IRQ 22
[   37.587085] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNEC] -> GSI 17 (level, low) -> IRQ 66
[   37.587092] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   37.587239] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri Dec 15 10:19:35 PST 2006
[   37.587850] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   37.587854] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 209
[   37.587931] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   37.703277] bt878: AUDIO driver version 0.0.0 loaded
[   38.153550] usbcore: registered new driver spca5xx
[   38.153555] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[   38.158412] NET: Registered protocol family 17
[   38.159648] bt878: Bt878 AUDIO function found (0).
[   38.159666] ACPI: PCI Interrupt 0000:04:08.1[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 58
[   38.159673] bt878_probe: card id=[0x45000070], Unknown card.
[   38.159674] Exiting..

---

### Post by masq-man on 2007-02-19
Two days of searching, etc., and the problem was just that bttv.c was looking for the file "hcwamc.rbf", and after i unzipped it from the CD it was "hcwAMC.rbf". 
LOL, oh yeah, lesson 1=linux is case sensitive.  :rolleyes:

---

