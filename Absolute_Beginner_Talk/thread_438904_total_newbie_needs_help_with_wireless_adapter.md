---
title: "total newbie needs help with wireless adapter"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jabie5 on 2007-05-10
i cannot get linux to recognise my laptop built in wireless adapter , so ive been reading the forums to gain info but imm still lost. ive opened  a terminal and typed in lspci to find out what card i have built in these are the results

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
00:09.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
00:0a.0 Network controller: Agere Systems Unknown device ab34
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
ubuntu@ubuntu:~$ 

can any one help me get my wirless connection working


thanks

---

### Post by bapoumba on 2007-05-11
Thread moved to the "Absolute Beginner Talk" support forum.

---

### Post by nightfall_sgp on 2007-05-26
Hi Jabie5,

Seeing no one has replied to you, let me see if I can at least better define your problem.

How do you tell if the wireless adaptor has been recognised or not?

Can you select the Enable Wireless setting in the NetworkManager Applet found on the top right of Ubuntu desktop?

---

### Post by jabie5 on 2007-06-18
sorry its been a while since i was last on my laptop has been away for repair.

there are no wireless  options in the top right hand corner

---

### Post by jimrz on 2007-06-18
> **jabie5 said:**
> sorry its been a while since i was last on my laptop has been away for repair.

there are no wireless  options in the top right hand corner

what make and model laptop? also, you might got the manufacturer's website and see if you can determine which wifi card / chipset it has

---

