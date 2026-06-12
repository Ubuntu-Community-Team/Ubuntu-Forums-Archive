---
title: "Mac Mini wireless"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by stair314 on 2008-07-18
My lab just got a Mac Mini and installed kubuntu on it. I thought that the wireless card was meant to work on the Mac Mini using the automatically installed restricted drivers, but KNetworkManager doesn't seem to detect my wireless card. Under the "Device" tab it says "Device: No active device."
Any ideas?

---

### Post by cyberdork33 on 2008-07-18
> **stair314 said:**
> My lab just got a Mac Mini and installed kubuntu on it. I thought that the wireless card was meant to work on the Mac Mini using the automatically installed restricted drivers, but KNetworkManager doesn't seem to detect my wireless card. Under the "Device" tab it says "Device: No active device."
Any ideas?
what does 'lspci' give?

---

### Post by stair314 on 2008-07-23
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                            er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                            er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                            er #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                            er #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Control                                            ler (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (re                                            v 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (re                                            v 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Con                                            troller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit                                             Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wi                                            reless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by cyberdork33 on 2008-07-23
You are going to fall into the same category as the First generation MacBook:
[https://help.ubuntu.com/community/MacBook#Wireless](https://help.ubuntu.com/community/MacBook#Wireless)

You will need to isntall madwifi.

---

