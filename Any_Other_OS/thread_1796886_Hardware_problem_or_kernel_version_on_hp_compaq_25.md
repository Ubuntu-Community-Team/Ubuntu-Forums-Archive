---
title: "Hardware problem or kernel version on hp compaq 2510p debian squeeze"
date: 2011-07-04
forum: Any Other OS
---

### Post by smurphy_it on 2011-07-04
Good day.  My debian squeeze installation has been fine up to about a week ago.  The hp media bar doesn't seem to work any longer.  Too bad that's where my wireless is enabled/disabled.  Sound muting etc I can live with manually, not a big deal.  Not sure how to enable / disable the wifi if the button isn't working (or even if I can).  Tried booting a couple of liveCDs/DVDs, no help.  Wireless light will "turn on" as soon as boot the laptop, however, once I get to the grub loading screen, it automatically turns off... and can't be re-enabled.  Could be hardware, don't know.  Suggestions ?

```
vmlinuz-2.6.32-5-amd64
```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
02:06.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
02:06.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
02:06.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

```
lspci -vv
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1000
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at e0000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn

```
Excluded other devices other than Wireless Card.  Can be posted if required.

```
ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```

```
cat  /var/log/syslog | grep wlan0
Jul  4 11:22:47 ch48808 NetworkManager[1525]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:10:00.0/net/wlan0, iface: wlan0)
Jul  4 11:22:47 ch48808 NetworkManager[1525]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:10:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): now managed
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): bringing up device.
Jul  4 11:22:48 ch48808 NetworkManager[1525]: <info> (wlan0): deactivating device (reason: 2).
Jul  4 11:22:49 ch48808 NetworkManager[1525]: <info> (wlan0): supplicant manager state:  down -> idle

```

Worked itself out.  After about 6 days I was able to re-enable the WIFI button, and it worked from then on.  To be on the safe side, I had a hardware technician take the laptop apart and un-attach and re-attach the keyboard + hp media bar cable(s).  Has worked fine since.

---

