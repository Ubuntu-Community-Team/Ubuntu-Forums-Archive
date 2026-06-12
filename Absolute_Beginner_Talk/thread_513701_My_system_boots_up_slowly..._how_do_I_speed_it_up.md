---
title: "My system boots up slowly... how do I speed it up?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-30
I ran dmesg on the command line to see what was slowing it up, and while I have isolated a few spots, I don't know where to begin to correct them. These spots are:

```
[    0.000000] Detected 1862.128 MHz processor.
[    7.451789] Built 1 zonelists.  Total pages: 257699
```Which I think cannot be sped up.

```
[   10.893881] libata version 2.20 loaded.
[    3.324000] Time: acpi_pm clocksource has been installed.
```This I'm not sure if it's a slow spot or what, but the time code gets (somewhat) reset.

```
[    8.336000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    8.648000] usb 5-5: configuration #1 chosen from 1 choice
[   10.544000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   11.636000] usb 2-1: configuration #1 chosen from 1 choice
[   25.080000] eth0: link down
```

```
[   31.540000] cs: IO port probe 0x100-0x3af: clean.
[   31.544000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.544000] cs: IO port probe 0x820-0x8ff: clean.
[   31.544000] cs: IO port probe 0xc00-0xcf7: clean.
[   31.544000] cs: IO port probe 0xa00-0xaff: clean.
[   46.056000] NET: Registered protocol family 10
```

```
[   46.056000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.492000] fuse init (API version 7.8)
```

```
[   59.044000] EXT3 FS on sda3, internal journal
[   59.044000] EXT3-fs: mounted filesystem with ordered data mode.
[   70.844000] ACPI: Battery Slot [BAT1] (battery present)
```

```
[   73.436000] pcc_acpi: loading...
[   83.456000] ppdev: user-space parallel port driver
```

```
[   92.760000] /dev/vmnet: open called by PID 5402 (vmnet-netifup)
[   92.760000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   92.760000] /dev/vmnet: port on hub 1 successfully opened
[   93.300000] /dev/vmnet: open called by PID 5407 (vmnet-dhcpd)
[   93.300000] /dev/vmnet: port on hub 1 successfully opened
[   93.304000] /dev/vmnet: open called by PID 5424 (vmnet-netifup)
[   93.304000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   93.304000] /dev/vmnet: port on hub 8 successfully opened
[   93.380000] /dev/vmnet: open called by PID 5439 (vmnet-dhcpd)
[   93.380000] /dev/vmnet: port on hub 8 successfully opened
[   93.396000] /dev/vmnet: open called by PID 5444 (vmnet-natd)
[   93.396000] /dev/vmnet: port on hub 8 successfully opened
[  103.712000] vmnet1: no IPv6 routers present
[  104.480000] vmnet8: no IPv6 routers present
[  129.148000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  129.512000] ieee80211_crypt: registered algorithm 'WEP'
[  145.380000] eth1: no IPv6 routers present
```

Any help with this is deeply appreciated. I have the entire log at hand if you want to look at it. Thanks!!!

---

### Post by ronocdh on 2007-07-30
I don't know why you're posting in the "Absolute Beginners" forum on a topic so advanced. Briefest advice I can give you is that you could try recompiling your kernel with a custom configuration tailored to your machine. Would take a while to create, but hopefully worthwhile, if you're trying to speed up booting.

---

