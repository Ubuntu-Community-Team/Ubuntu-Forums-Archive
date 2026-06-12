---
title: "linksys wireless problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by witham on 2007-08-02
I have installed ndiswrapper and installed the driver for the wireless card as listed below

martin@martin-desktop:~$ ndiswrapper -l
rt61 : driver installed
        device (1814:0401) present (alternate driver: rt61)

I still however cannot get it to connect to the router wifi-radar does show the router but I cannot get connected.
Any help would be greatly appreciated.

---

### Post by Kawasaki12 on 2007-08-02
so far, from what i've read about ubuntu, its a pain in the butt to use a wireless connection...i wish i could help, but i use a wired connection...try and google it...

---

### Post by milosz.galazka on 2007-08-02
Please look [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

---

### Post by witham on 2007-08-03
Thanks for your reply and I have done a bit more research and from the command below it seems that the hardware isn't listed although the led is flashing away?

Could this be the problem and how would I resolve it please!!


martin@martin-desktop:~$ sudo lspci
Password:
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge [0620]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 Network controller: RaLink Ralink RT2600 802.11 MIMO
00:0f.0 Communication controller: Conexant HSF 56k Data/Fax Modem (WorldW SmartDAA) (rev 01)
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)
martin@martin-desktop:~$

---

### Post by mishaco on 2007-09-18
for the desktop wireless card i have - linksys wireless - g pci network adapter with speed booster , the only thing that ever worked for me was mandriva linux .

i've tried and tried on ubuntu . since 6.0 and nothing has ever worked .

---

