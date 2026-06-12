---
title: "Can't install ndiswrapper - Error: dependancy not satisifiable:libc6"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-08-19
Hi, I'm trying to install drivers for my network card and to do so I need ndiswrapper installed. I'm following the instructions here: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

When I try to install ndiswrapper-util (1.43) I get the error "Dependency not satisfiable: libc6".

I then found libc6 (2.3.6) but I can't install that because it says a later version is already installed.

What's going on?

This post has the same problem, but the solution doesn't work: [http://ubuntuforums.org/archive/index.php/t-356498.html](http://ubuntuforums.org/archive/index.php/t-356498.html)

All it does is unmount my cd drive.

This is quite a painful introduction to linux. Can someone cheer me up?

---

### Post by tdrusk on 2007-08-19
You can try to use the ndiswrapper in the repositories (in Synaptic).
or
You could try the newest version of ndiswrapper 1.47.

Do this for me. Open your terminal, enter
```
lspci
```
and copy and paste the output in here so I can figure out what card you have and get that beast working.

EDIT: Ah, I understand why your drive was opening. Your repositories are set to use the Ubuntu CD instead of downloading off the internet. Go to System>Administration>Synaptic and go to Settings>Repositories and remove the Ubuntu CD.

You really just need a guide to follow. That's why I asked you to post your lspci.

---

### Post by acl123 on 2007-08-19
Hi, that speedy reply did cheer me up - thanks!
I actually got it working by installing the older version of ndiswrapper (1.38 instead of 1.43) and that's working fine now. So no problem now.

In case you can still provide some insight, here's the output from lspci:

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
05:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

---

### Post by tdrusk on 2007-08-19
> **acl123 said:**
> Hi, that speedy reply did cheer me up - thanks!
I actually got it working by installing the older version of ndiswrapper (1.38 instead of 1.43) and that's working fine now. So no problem now.

In case you can still provide some insight, here's the output from lspci:

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
05:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

So did you get everything working?

---

### Post by acl123 on 2007-08-25
Yes thanks, it's working with the older version of ndiswrapper

---

