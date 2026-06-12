---
title: "Wireless works, ethernet doesn't..."
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Starks on 2008-02-18
How do I solve this?

Ubuntu 8.04 Hardy Heron
Linux kingfisher 2.6.24-8-generic #1 SMP Thu Feb 14 20:40:45 UTC 2008 i686 GNU/Linux

---

### Post by amohanty on 2008-02-18
I would recommend checking if the cable works for other computers first :)

If it works, then check to see if the network applet shows the option of "Wired Network".

Click on it and if it does not work, post the output of the following (in a terminal)

dmesg | tail -n 100

AM

---

### Post by Starks on 2008-02-18
I don't see eth0 anywhere in the output...




[   24.793924] Bluetooth: HCI device and connection manager initialized
[   24.793929] Bluetooth: HCI socket layer initialized
[   24.848517] Bluetooth: HCI USB driver ver 2.9
[   24.850578] usbcore: registered new interface driver hci_usb
[   25.143136] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   25.143141] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   25.143293] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.143310] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   25.143336] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   25.343065] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   25.343093] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   25.369280] iTCO_vendor_support: vendor-support=0
[   25.407471] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.408067] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.408123] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.449491] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   25.490292] intel_rng: FWH not detected
[   25.542631] ricoh-mmc: Ricoh MMC Controller disabling driver
[   25.542636] ricoh-mmc: Copyright(c) Philip Langdale
[   25.558898] sdhci: Secure Digital Host Controller Interface driver
[   25.558902] sdhci: Copyright(c) Pierre Ossman
[   26.375390] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   26.411367] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   28.289391] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   29.011453] ricoh-mmc: Ricoh MMC controller found at 0000:02:01.2 [1180:0843] (rev 1)
[   29.011474] ricoh-mmc: Controller is now disabled.
[   29.034945] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
[   29.035013] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   29.035114] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   27.265349] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.281282] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   27.427435] NET: Registered protocol family 17
[   32.857545] lp: driver loaded but no devices found
[   34.835878] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   35.187195] EXT3 FS on sda1, internal journal
[   34.124403] Bridge firewalling registered
[   34.124526] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.126620] device eth0 entered promiscuous mode
[   34.126630] audit(1203313571.344:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   36.544163] NET: Registered protocol family 10
[   36.544511] lo: Disabled Privacy Extensions
[   36.545094] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.229516] br0: no IPv6 routers present
[   46.967750] No dock devices found.
[   47.015336] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   49.573716] ppdev: user-space parallel port driver
[   49.918353] audit(1203313648.732:3): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5854 profile="/usr/sbin/cupsd" namespace="default"
[   50.004874] apm: BIOS not found.
[   63.073820] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   63.073829] vboxdrv: Successfully done.
[   63.074557] vboxdrv: Successfully loaded version 1.5.4_OSE (interface 0x00050002).
[   65.103645] tun: Universal TUN/TAP device driver, 1.6
[   65.103655] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   63.679951] Bluetooth: L2CAP ver 2.9
[   63.679960] Bluetooth: L2CAP socket layer initialized
[   65.639770] Bluetooth: RFCOMM socket layer initialized
[   65.639791] Bluetooth: RFCOMM TTY layer initialized
[   65.639796] Bluetooth: RFCOMM ver 1.8
[   66.889679] [drm] Initialized drm 1.1.0 20060810
[   66.892188] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   66.892196] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   66.892248] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  101.226093] CPU0 attaching NULL sched-domain.
[  101.226102] CPU1 attaching NULL sched-domain.
[  101.235439] CPU0 attaching sched-domain:
[  101.235446]  domain 0: span 03
[  101.235449]   groups: 01 02
[  101.235453] CPU1 attaching sched-domain:
[  101.235455]  domain 0: span 03
[  101.235457]   groups: 02 01
[  173.155084] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  174.764486] wlan0: Initial auth_alg=0
[  174.764494] wlan0: authenticate with AP 00:1c:57:43:67:50
[  174.766039] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  174.766043] wlan0: authenticated
[  174.766046] wlan0: associate with AP 00:1c:57:43:67:50
[  176.796945] wlan0: associate with AP 00:1c:57:43:67:50
[  176.996767] wlan0: associate with AP 00:1c:57:43:67:50
[  177.195456] wlan0: association with AP 00:1c:57:43:67:50 timed out
[  236.422869] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  236.464603] wlan0: Initial auth_alg=0
[  236.464611] wlan0: authenticate with AP 00:1c:57:43:67:50
[  236.466046] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  236.466050] wlan0: authenticated
[  236.466053] wlan0: associate with AP 00:1c:57:43:67:50
[  236.469584] wlan0: RX AssocResp from 00:1c:57:43:67:50 (capab=0x421 status=0 aid=198)
[  236.469589] wlan0: associated
[  236.471826] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.513767] wlan0: disassociate(reason=3)
[  237.986500] wlan0: Initial auth_alg=0
[  237.986512] wlan0: authenticate with AP 00:1c:57:43:67:50
[  239.820842] wlan0: Initial auth_alg=0
[  239.820854] wlan0: authenticate with AP 00:1c:57:43:67:50
[  239.820887] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  239.820893] wlan0: authenticated
[  239.820898] wlan0: associate with AP 00:1c:57:43:67:50
[  237.989595] wlan0: authentication frame received from 00:1c:57:43:67:50, but not in authenticate state - ignored
[  237.991382] wlan0: RX ReassocResp from 00:1c:57:43:67:50 (capab=0x421 status=0 aid=198)
[  237.991391] wlan0: associated
[  246.227421] wlan0: no IPv6 routers present
eric@kingfisher:~$ dmesg | tail -n 100
[   24.793924] Bluetooth: HCI device and connection manager initialized
[   24.793929] Bluetooth: HCI socket layer initialized
[   24.848517] Bluetooth: HCI USB driver ver 2.9
[   24.850578] usbcore: registered new interface driver hci_usb
[   25.143136] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   25.143141] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   25.143293] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.143310] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   25.143336] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   25.343065] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   25.343093] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   25.369280] iTCO_vendor_support: vendor-support=0
[   25.407471] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.408067] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.408123] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.449491] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   25.490292] intel_rng: FWH not detected
[   25.542631] ricoh-mmc: Ricoh MMC Controller disabling driver
[   25.542636] ricoh-mmc: Copyright(c) Philip Langdale
[   25.558898] sdhci: Secure Digital Host Controller Interface driver
[   25.558902] sdhci: Copyright(c) Pierre Ossman
[   26.375390] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   26.411367] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   28.289391] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   29.011453] ricoh-mmc: Ricoh MMC controller found at 0000:02:01.2 [1180:0843] (rev 1)
[   29.011474] ricoh-mmc: Controller is now disabled.
[   29.034945] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
[   29.035013] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   29.035114] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   27.265349] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.281282] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   27.427435] NET: Registered protocol family 17
[   32.857545] lp: driver loaded but no devices found
[   34.835878] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   35.187195] EXT3 FS on sda1, internal journal
[   34.124403] Bridge firewalling registered
[   34.124526] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.126620] device eth0 entered promiscuous mode
[   34.126630] audit(1203313571.344:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   36.544163] NET: Registered protocol family 10
[   36.544511] lo: Disabled Privacy Extensions
[   36.545094] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.229516] br0: no IPv6 routers present
[   46.967750] No dock devices found.
[   47.015336] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   49.573716] ppdev: user-space parallel port driver
[   49.918353] audit(1203313648.732:3): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5854 profile="/usr/sbin/cupsd" namespace="default"
[   50.004874] apm: BIOS not found.
[   63.073820] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   63.073829] vboxdrv: Successfully done.
[   63.074557] vboxdrv: Successfully loaded version 1.5.4_OSE (interface 0x00050002).
[   65.103645] tun: Universal TUN/TAP device driver, 1.6
[   65.103655] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   63.679951] Bluetooth: L2CAP ver 2.9
[   63.679960] Bluetooth: L2CAP socket layer initialized
[   65.639770] Bluetooth: RFCOMM socket layer initialized
[   65.639791] Bluetooth: RFCOMM TTY layer initialized
[   65.639796] Bluetooth: RFCOMM ver 1.8
[   66.889679] [drm] Initialized drm 1.1.0 20060810
[   66.892188] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   66.892196] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   66.892248] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  101.226093] CPU0 attaching NULL sched-domain.
[  101.226102] CPU1 attaching NULL sched-domain.
[  101.235439] CPU0 attaching sched-domain:
[  101.235446]  domain 0: span 03
[  101.235449]   groups: 01 02
[  101.235453] CPU1 attaching sched-domain:
[  101.235455]  domain 0: span 03
[  101.235457]   groups: 02 01
[  173.155084] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  174.764486] wlan0: Initial auth_alg=0
[  174.764494] wlan0: authenticate with AP 00:1c:57:43:67:50
[  174.766039] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  174.766043] wlan0: authenticated
[  174.766046] wlan0: associate with AP 00:1c:57:43:67:50
[  176.796945] wlan0: associate with AP 00:1c:57:43:67:50
[  176.996767] wlan0: associate with AP 00:1c:57:43:67:50
[  177.195456] wlan0: association with AP 00:1c:57:43:67:50 timed out
[  236.422869] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  236.464603] wlan0: Initial auth_alg=0
[  236.464611] wlan0: authenticate with AP 00:1c:57:43:67:50
[  236.466046] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  236.466050] wlan0: authenticated
[  236.466053] wlan0: associate with AP 00:1c:57:43:67:50
[  236.469584] wlan0: RX AssocResp from 00:1c:57:43:67:50 (capab=0x421 status=0 aid=198)
[  236.469589] wlan0: associated
[  236.471826] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.513767] wlan0: disassociate(reason=3)
[  237.986500] wlan0: Initial auth_alg=0
[  237.986512] wlan0: authenticate with AP 00:1c:57:43:67:50
[  239.820842] wlan0: Initial auth_alg=0
[  239.820854] wlan0: authenticate with AP 00:1c:57:43:67:50
[  239.820887] wlan0: RX authentication from 00:1c:57:43:67:50 (alg=0 transaction=2 status=0)
[  239.820893] wlan0: authenticated
[  239.820898] wlan0: associate with AP 00:1c:57:43:67:50
[  237.989595] wlan0: authentication frame received from 00:1c:57:43:67:50, but not in authenticate state - ignored
[  237.991382] wlan0: RX ReassocResp from 00:1c:57:43:67:50 (capab=0x421 status=0 aid=198)
[  237.991391] wlan0: associated
[  246.227421] wlan0: no IPv6 routers present

---

### Post by kaginken on 2008-02-18
Got an IP?  Post your:

ifconfig

Are you connecting your interface directly to the router?  Are the link lights on at each end of the cable?  

Can you pull up the routers interface or ping it?  Is it just the internet you cannot connect to, or even things like other local network resources?

Any more info you can provide would be useful...

---

### Post by amohanty on 2008-02-18
Do you see the "Wired Network" option in the network applet that you use for the wireless network?

Can you post the contents of /etc/network/interfaces?

Also the output of
lspci
and the output of
ifconfig -a

AM

---

### Post by kaginken on 2008-02-18
Contrare my ubuntuing friend, eth0 does show up in your dmesg:

[ 36.545094] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 38.229516] br0: no IPv6 routers present
[ 46.967750] No dock devices found.

Are you docked?  If so, undock and plug the ethernet cable directly into the laptop.  May want to reboot after this also.

---

### Post by amohanty on 2008-02-18
<head and desk meet>

I got to learn how to type, searching for eht0 does not lead one to salvation.

AM

---

### Post by Starks on 2008-02-18
> **amohanty said:**
> Do you see the "Wired Network" option in the network applet that you use for the wireless network?

Can you post the contents of /etc/network/interfaces?

Also the output of
lspci
and the output of
ifconfig -a

AM
First an foremost: **There is no router. I am on a college ResNet. I use wireless for my host machine and wired connection for my guest OS. BOTH USE SEPARATE, DISTINCT IP ADDRESSES.**

auto lo

iface lo inet loopback

auto br0

iface br0 inet dhcp

bridge_ports eth0

up chmod 0666 /dev/net/tun




iface eth0 inet dhcp

auto eth0


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by kaginken on 2008-02-18
If you're using Network Manager (nm-applet) for your network configs, it will ignore any interfaces listed in your /etc/network/interfaces.  I use Network Manager and my /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback

Just fyi

---

### Post by amohanty on 2008-02-18
Hes using eth0 as a bridge and that is not quite working as planned. I believe nm-applet does not allow you to set that up. 

I would try removeing the bridge related config options and see if you can bring up the interface?

Also IIRC, you should not be specifying the config for the interfaces to be used by the bridge as that ought to be doen automatically , so you could try removing all eth0 related config from the file.

AM

PS:

> I use wireless for my host machine and wired connection for my guest OS. 
This is not very helpful, if you are setting up a bridge mentioning it might be helpful. Same goes for the bold and caps. We are only trying to help. Insufficient information and such only get in the way :)

---

### Post by Starks on 2008-02-18
> **kaginken said:**
> If you're using Network Manager (nm-applet) for your network configs, it will ignore any interfaces listed in your /etc/network/interfaces.  I use Network Manager and my /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback

Just fyi

I tried that earlier and it didn't work.

---

### Post by Starks on 2008-02-18
bump

---

### Post by Starks on 2008-02-18
Hahaha. It was a bum ethernet cable.

---

### Post by stalkingwolf on 2008-02-18
post #2

> **amohanty said:**
> **I would recommend checking if the cable works for other computers first :)**

If it works, then check to see if the network applet shows the option of "Wired Network".

Click on it and if it does not work, post the output of the following (in a terminal)

dmesg | tail -n 100

AM

---

