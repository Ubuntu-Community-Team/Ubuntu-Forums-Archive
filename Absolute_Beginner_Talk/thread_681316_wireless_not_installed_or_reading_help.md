---
title: "wireless not installed or reading help"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by stevensonfire on 2008-01-28
alright so i went to the wiki site for the wireless cards etc 
i have tried lspci -v | less
and got

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0020
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

i don't know what that means but i do know access denied.. haha

i went to the intel link on the wiki page it says my card is recognized
the Pro/Wireless 3945 ABG

but when i turn the wireless switch on i get no light indicating its on
i can't find the wireless 
help?

---

### Post by UltraMathMan on 2008-01-28
If you have a 3945 I suspect you might be running into [this issue]("http://ubuntuforums.org/showthread.php?t=246074").

---

### Post by stevensonfire on 2008-01-28
the problem im getting is not with the killswitch but the fact i can't even turn it on.. im not sure the driver is installed.. i've been searching, googling etc but im getting nothing... its disappointing.. i really like the ubuntu but my notebook without the wireless might as well be using a desktop... also camera dosent seem to function on ubuntu.... 
if any help my notebook is the Compal PowerPro Hel80 8:15

---

### Post by UltraMathMan on 2008-01-28
Could you post the output of ```
dmesg
```

---

### Post by stevensonfire on 2008-01-28
i dunno how to make that iput box thing but here you go

[    5.128000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.132000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.132000] Uniform CD-ROM driver Revision: 3.20
[    5.132000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.156000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    5.320000] usb 3-2: configuration #1 chosen from 1 choice
[    5.380000] Attempting manual resume
[    5.380000] swsusp: Resume From Partition 8:5
[    5.380000] PM: Checking swsusp image.
[    5.380000] PM: Resume from disk failed.
[    5.388000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.388000] EXT3-fs: write access will be enabled during recovery.
[    6.320000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f7393403cb1]
[   10.328000] kjournald starting.  Commit interval 5 seconds
[   10.328000] EXT3-fs: recovery complete.
[   10.332000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.340000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.520000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.524000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.544000] intel_rng: FWH not detected
[   16.828000] tpm_inf_pnp 00:02: Found TPM with ID IFX0102
[   16.828000] tpm_inf_pnp 00:02: TPM found: config base 0x4e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   16.856000] sdhci: Secure Digital Host Controller Interface driver
[   16.856000] sdhci: Copyright(c) Pierre Ossman
[   16.856000] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   16.856000] PCI: Enabling device 0000:06:04.2 (0000 -> 0002)
[   16.856000] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   16.856000] PCI: Setting latency timer of device 0000:06:04.2 to 64
[   16.856000] mmc0: SDHCI at 0xd2100c00 irq 17 DMA
[   16.856000] sdhci: SDHCI controller found at 0000:06:04.4 [1524:0551] (rev 1)
[   16.856000] PCI: Enabling device 0000:06:04.4 (0000 -> 0002)
[   16.856000] ACPI: PCI Interrupt 0000:06:04.4[B] -> GSI 17 (level, low) -> IRQ 17
[   16.856000] mmc1: SDHCI at 0xd2100900 irq 17 PIO
[   16.868000] iTCO_vendor_support: vendor-support=0
[   16.872000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   16.888000] nvidia: module license 'NVIDIA' taints kernel.
[   17.140000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.140000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   17.144000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   17.188000] Yenta: CardBus bridge found at 0000:06:04.0 [14c0:0020]
[   17.188000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.188000] Yenta: Routing CardBus interrupts to PCI
[   17.188000] Yenta TI: socket 0000:06:04.0, mfunc 0x88501212, devctl 0x44
[   17.252000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   17.252000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   17.432000] Yenta: ISA IRQ mask 0x04f8, PCI irq 16
[   17.432000] Socket status: 30000006
[   17.432000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   17.432000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   17.432000] cs: IO port probe 0x4000-0x4fff: clean.
[   17.432000] pcmcia: parent PCI bridge Memory window: 0xd2100000 - 0xd21fffff
[   17.432000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   17.436000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   17.436000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.724000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   17.772000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   17.776000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.776000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.776000] cs: IO port probe 0x100-0x3af: clean.
[   17.780000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.780000] cs: IO port probe 0x820-0x8ff: clean.
[   17.780000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.784000] cs: IO port probe 0xa00-0xaff: clean.
[   19.004000] si3054: cannot initialize. EXT MID = 0000
[   19.028000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.028000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   19.028000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   19.172000] iwl4965: Radio disabled by HW RF Kill switch
[   19.288000] lp: driver loaded but no devices found
[   19.356000] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   19.528000] EXT3 FS on sda2, internal journal
[   20.376000] input: Power Button (FF) as /class/input/input3
[   20.376000] ACPI: Power Button (FF) [PWRF]
[   20.376000] input: Lid Switch as /class/input/input4
[   20.376000] ACPI: Lid Switch [LID0]
[   20.376000] input: Power Button (CM) as /class/input/input5
[   20.376000] ACPI: Power Button (CM) [PWRB]
[   20.424000] No dock devices found.
[   20.452000] ACPI: AC Adapter [ACAD] (on-line)
[   20.624000] ACPI: Battery Slot [BAT1] (battery present)
[   20.720000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.732000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.796000] r8169: eth0: link up
[   21.796000] r8169: eth0: link up
[   25.836000] ppdev: user-space parallel port driver
[   27.304000] audit(1201291231.070:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5257 profile="/usr/sbin/cupsd"
[   27.352000] apm: BIOS not found.
[   27.608000] Failure registering capabilities with primary security module.
[   27.796000] Bluetooth: Core ver 2.11
[   27.796000] NET: Registered protocol family 31
[   27.796000] Bluetooth: HCI device and connection manager initialized
[   27.796000] Bluetooth: HCI socket layer initialized
[   27.836000] Bluetooth: L2CAP ver 2.8
[   27.836000] Bluetooth: L2CAP socket layer initialized
[   27.904000] Bluetooth: RFCOMM socket layer initialized
[   27.904000] Bluetooth: RFCOMM TTY layer initialized
[   27.904000] Bluetooth: RFCOMM ver 1.8
[   32.100000] NET: Registered protocol family 17
[   34.520000] NET: Registered protocol family 10
[   34.520000] lo: Disabled Privacy Extensions
[   41.636000] UDF-fs: No VRS found
[   41.668000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.700000] ISOFS: changing to secondary root
[   45.492000] eth0: no IPv6 routers present
[ 2103.700000] r8169: eth0: link down
[ 2109.212000] r8169: eth0: link up
[ 2109.216000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2117.880000] r8169: eth0: link down
[ 2122.108000] r8169: eth0: link up
[ 2122.108000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2137.632000] eth0: no IPv6 routers present
[54253.516000] r8169: eth0: link down
[54307.900000] r8169: eth0: link up
[54321.828000] eth0: no IPv6 routers present
[91238.788000] r8169: eth0: link down
[91261.144000] r8169: eth0: link up
[91261.148000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[91274.880000] eth0: no IPv6 routers present
[91322.376000] r8169: eth0: link down
[95178.512000] r8169: eth0: link up
[95178.516000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[95195.052000] eth0: no IPv6 routers present
[95273.864000] r8169: eth0: link down
[98041.396000] r8169: eth0: link down
[98043.816000] r8169: eth0: link up
[98043.820000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[98061.668000] eth0: no IPv6 routers present
[129515.100000] r8169: eth0: link down
[129749.528000] r8169: eth0: link up
[129749.532000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[129763.292000] eth0: no IPv6 routers present
[131423.976000] r8169: eth0: link down
[131447.844000] r8169: eth0: link up
[131447.848000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[131462.924000] eth0: no IPv6 routers present
[131912.388000] NVRM: Xid (0001:00): 6, PE0000 06d0 ff040502 0000fd18 ff010404 ff010404
[131912.404000] NVRM: Xid (0001:00): 29,  L1 -> L0
[131912.456000] NVRM: Xid (0001:00): 13, 0000 01016100 0000008a 00000404 ff000600 00004000
[131916.468000] NVRM: Xid (0001:00): 29,  L0 -> L0
[132824.004000] r8169: eth0: link down
[132835.016000] r8169: eth0: link up
[132835.020000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[132853.012000] eth0: no IPv6 routers present
[137329.236000] r8169: eth0: link down
[149225.876000] r8169: eth0: link up
[149225.880000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[149239.752000] eth0: no IPv6 routers present
[179477.968000] r8169: eth0: link up
[187063.536000] r8169: eth0: link down
[193735.776000] r8169: eth0: link up
[193735.780000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[193749.108000] eth0: no IPv6 routers present
[280016.220000] r8169: eth0: link down
[280018.624000] r8169: eth0: link up
[280018.628000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[280032.996000] eth0: no IPv6 routers present

---

### Post by UltraMathMan on 2008-01-28
```
[ 19.028000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 19.172000] iwl4965: Radio disabled by HW RF Kill switch
```

So the killswitch is on. So far to my knowledge the option is sometimes in the BIOS, but in my case the only remedy so far has been to boot into Windows and enable it there. After rebooting the key combination has then worked in Linux.

Oh, and you can put code in that box by using the {CODE} and {/CODE} tags (replacing {} with []).

---

