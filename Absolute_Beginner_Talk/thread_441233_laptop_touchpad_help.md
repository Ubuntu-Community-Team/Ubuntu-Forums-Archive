---
title: "laptop touchpad help"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2007-05-12
Does anyone know how to configure laptop touchpads in Ubuntu? For example, I can't use the scroll feature or any area specific functions. Thanks

---

### Post by Kobalt on 2007-05-12
What kind of a touchpad do you have ? If it's a Synaptics one then you can check [that]("https://help.ubuntu.com/community/SynapticsTouchpad") out. If you don't know which type of touchpad it is you can find it out with the command line *lspci* for example.

---

### Post by cptjaben on 2007-05-12
typing lspci give this output:


```
i
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M66-P ATI Mobility Radeon X1700
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

```

Any idea?

---

### Post by Linked on 2007-05-12
> **Kobalt said:**
> What kind of a touchpad do you have ? If it's a Synaptics one then you can check [that]("https://help.ubuntu.com/community/SynapticsTouchpad") out. If you don't know which type of touchpad it is you can find it out with the command line *lspci* for example.
Correct me if Im wrong, but lspci didn't show anything about which type of touchpad I have, as you can see below.
The link you gave helped a lot.
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```
Quote from the page:> synaptics touchpads seem to be misdetected as some kind of wacom device, so the scrollbar may not work.
This was the case on my laptop, and I tried [editing the Xorg.conf file]("https://help.ubuntu.com/community/SynapticsTouchpad#head-771b9659c0e19809759b49f470d568c7d7a36cc3") and it worked well. (I was sure that I had Synaptics Touchpad).

---

### Post by Bachstelze on 2007-05-12
The touchpad should be detected as an input device during bootup

```
$ dmesg | grep input
input: AT Translated Set 2 keyboard as /class/input/input0
input: PC Speaker as /class/input/input1
input: SynPS/2 Synaptics TouchPad as /class/input/input2
input: Power Button (FF) as /class/input/input3
input: Lid Switch as /class/input/input4
input: Power Button (CM) as /class/input/input5
input: Sleep Button (CM) as /class/input/input6
input: Logitech USB Gaming Mouse as /class/input/input7
input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```

---

