---
title: "Sound error after compling v4l drivers"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by mangurt on 2008-01-21
Greetings all,
I have a problem with my sound now after I compliled drivers from v4l.  I have no sound (the speaker icon is red x out).  When I click on the speaker I get a message stating "No volume controller Gstreamer plugins and/or device found"

This is the results from doing lspci in terminal

ed@ed-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0c.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
ed@ed-des

Any help would be greatly appreciated.
Thanks

---

### Post by balaknair on 2008-01-21
Could you please paste the output for
aplay -l

---

### Post by balaknair on 2008-01-22
I think reinstalling ALSA(maybe ALSA 1.0.15 RC3 via Gutsy backports) ought to fix your issue, since to me it seems like the v4l install might have messed up your sound modules.

---

### Post by mangurt on 2008-01-22
I tried reinstalling ALSA and that totally screwed up my system.  I ended up doing a complete wipe and install.  Hopefully I will not have this problem again.  I think I will post on v4l message group for solutions.
Thanks again.

---

