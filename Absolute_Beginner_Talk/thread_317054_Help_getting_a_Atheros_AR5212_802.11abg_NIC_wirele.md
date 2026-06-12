---
title: "Help getting a Atheros AR5212 802.11abg NIC wireless card to work"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2006-12-11
Hey all, I'm new to the Linux community and am having issues with getting my wireless card working. It's detecting the wireless network I'm trying to connect to, but just won't let me on the internet. Here are the outputs from lspci, sudo lshw -C network, and iwconfig:
```

0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01 )
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01 )
0000:00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI  IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audi o Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
0000:02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader C ontroller
0000:02:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Control ler
0000:02:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520
```

--
```

  *-network:0 DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@02:02.0
       logical name: ath0
       version: 01
       serial: 00:90:96:bc:a1:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
       resources: iomemory:e8200000-e820ffff irq:209
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:d5:0f:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.102 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:e8214800-e82148ff irq:201

```
--
```

  *-network:0 DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@02:02.0
       logical name: ath0
       version: 01
       serial: 00:90:96:bc:a1:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
       resources: iomemory:e8200000-e820ffff irq:209
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:d5:0f:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.102 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:e8214800-e82148ff irq:201
```


I have a Toshiba Satellite A75-S226, and have 6.06 Ubuntu installed from the .iso image supplied on the site.


Hopefully that's enough info to be helpful; if not, just respond and I'll be able to supply whatever you need.


Thanks!


Evan.

---

### Post by evanvlane on 2006-12-11
Any help guys?
I've already searched the forums for help with Atheros cards, and I've Googled my brains out. If someone could point me in a useful direction, I'd really appreciate it! :)

Evan.

PS: I know that the wireless card says disabled. I had to disable it so that my ethernet would work, but even when it's enabled it doesn't work properly.

---

### Post by dunder on 2006-12-21
got:
```

0000:02:02.0 Network controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```
IBM thinkpad T30, ath0 works fine, can connect to 2GHz APs, but 5GHz frequencies are gone ...:
```

# iwlist ath0 chan
ath0      27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)

```
```

# iwconfig ath0 mode 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

```

/var/log/syslog:
```

Dec 21 13:46:07 localhost kernel: [17181385.736000] ath_rate_sample: 1.2 (svn r1860)
Dec 21 13:46:12 localhost kernel: [17181391.180000] ath_pci: 0.9.4.5 (svn r1860)
Dec 21 13:46:12 localhost kernel: [17181391.180000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec 21 13:46:13 localhost kernel: [17181391.400000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Dec 21 13:46:13 localhost kernel: [17181391.400000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Dec 21 13:46:13 localhost kernel: [17181391.400000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Dec 21 13:46:13 localhost kernel: [17181391.400000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: mac 5.6 phy 4.1 radio 4.6
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 8 for CAB traffic
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Use hw queue 9 for beacons
Dec 21 13:46:13 localhost kernel: [17181391.404000] wifi0: Atheros 5212: mem=0xd0200000, irq=11
Dec 21 13:46:24 localhost kernel: [17181402.364000] ath0: no IPv6 routers present

```

**where is A mode? how can i scan and connect to 5GHz APs? please help!**

---

### Post by sumo on 2006-12-30
guys the answer is very simple, download and install ndiswrapper (google for it) that alone will fix it.

---

### Post by dunder on 2007-01-02
the same situation with ndiswrapper:
> root@adam:/# iwlist wlan0 chan
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)


there's still no A frequencies ... any ideas?

---

### Post by hohonuuli on 2007-01-23
It could be a bug in the madwifi code. See this thread: [http://madwifi.org/ticket/1016]("http://madwifi.org/ticket/1016"). In a nutshell, there's a bug in madwifi that prevents it from connecting to WEP enabled networks. A patch has been submitted for it and hopefully a new release will be out soon. 

Ta Ta
B

---

### Post by tedy58 on 2007-09-19
Hi m8s,
I have HP Pavilion zv5000. 
In my case when I install UBUNTU 7.04 FF it recognizes the card immediately and install it on the installation phase, but on debian it wasn't recognized and installed at all.
Now I am looking for the installation on my debian. 
Can somebody have experience with it? 
Any help will be appreciated.

This is the # *lspci *and *_lspci -n _*that answer me.
 
debian:/home/tedy/Download# lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
debian:/home/tedy/Download# lspci -n
00:00.0 0600: 1002:5833 (rev 02)
00:01.0 0604: 1002:5838
00:13.0 0c03: 1002:4347 (rev 01)
00:13.1 0c03: 1002:4348 (rev 01)
00:14.0 0c05: 1002:4353 (rev 16)
00:14.1 0101: 1002:4349
00:14.3 0601: 1002:434c
00:14.4 0604: 1002:4342
00:14.5 0401: 1002:4341
00:14.6 0703: 1002:434d (rev 01)
01:05.0 0300: 1002:5835
02:00.0 0c00: 104c:8026
02:03.0 0200: 10ec:8139 (rev 10)
02:04.0 0607: 104c:ac54 (rev 01)
02:04.1 0607: 104c:ac54 (rev 01)
02:04.2 0880: 104c:8201 (rev 01)
02:07.0 0c03: 1033:0035 (rev 43)
02:07.1 0c03: 1033:0035 (rev 43)
02:07.2 0c03: 1033:00e0 (rev 04)
03:00.0 0200: 168c:0013 (rev 01)

---

