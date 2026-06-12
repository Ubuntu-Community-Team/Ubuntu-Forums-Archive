---
title: "Firewire Ipod not mounting in Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Stambo00 on 2007-10-22
I am having substantial problems trying to mount my 4gb iPod mini. It previously worked fine in Fiesty. I am now running Gutsy on a clean install.

The iPod mounts using USB on Ubuntu but not Firewire.

The iPod mounts with Firewire perfectly on my Windows partition but no longer on Ubuntu.

My dmesg reads as follows:

> 
[   26.789854]  sda: sda1 sda2 sda3 <sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.800133] Uniform CD-ROM driver Revision: 3.20
[   26.800195] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   26.818530]  sda5 >
[   26.818657] sd 1:0:0:0: [sda] Attached SCSI disk
[   26.818852] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.818870] sd 1:0:1:0: [sdb] Write Protect is off
[   26.818875] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.818901] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.818965] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   26.818982] sd 1:0:1:0: [sdb] Write Protect is off
[   26.818986] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.819022] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.819028]  sdb:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   26.823601] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   26.823633] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   26.838022]  sdb1
[   26.838107] sd 1:0:1:0: [sdb] Attached SCSI disk
[   27.052669] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a27000291a7e2]
[   27.052805] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[000fea0000b32ca1]
[   27.067236] scsi2 : SBP-2 IEEE-1394
[   27.095066] usb 5-6: new high speed USB device using ehci_hcd and address 3
[   27.167300] Attempting manual resume
[   27.167305] swsusp: Resume From Partition 8:5
[   27.167307] PM: Checking swsusp image.
[   27.167511] PM: Resume from disk failed.
[   27.198078] kjournald starting.  Commit interval 5 seconds
[   27.198090] EXT3-fs: mounted filesystem with ordered data mode.
[   27.228795] usb 5-6: configuration #1 chosen from 1 choice
[   27.649968] usb 2-2: new full speed USB device using uhci_hcd and address 4
[   27.823548] usb 2-2: configuration #1 chosen from 1 choice
[   27.826470] hub 2-2:1.0: USB hub found
[   27.829437] hub 2-2:1.0: 4 ports detected
[   28.072580] ieee1394: sbp2: Logged into SBP-2 device
[   28.073115] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   28.076594] scsi 2:0:0:0: Direct-Access-RBC Apple    iPod             1.62 PQ: 0 ANSI: 0
[   28.096659] sd 2:0:0:0: [sdc] Spinning up disk...<6>usb 4-1: new low speed USB device using uhci_hcd and address 2
[   28.359297] usb 4-1: configuration #1 chosen from 1 choice
[   29.103106] ..ready
[   30.123732] sd 2:0:0:0: [sdc] 7999488 512-byte hardware sectors (4096 MB)
[   30.125543] sd 2:0:0:0: [sdc] Write Protect is off
[   30.125546] sd 2:0:0:0: [sdc] Mode Sense: 04 00 00 00
[   30.128623] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.133613] sd 2:0:0:0: [sdc] 7999488 512-byte hardware sectors (4096 MB)
[   30.135441] sd 2:0:0:0: [sdc] Write Protect is off
[   30.135444] sd 2:0:0:0: [sdc] Mode Sense: 04 00 00 00
[   30.138761] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.138766]  sdc: sdc1 sdc2
[   30.167955] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   30.168002] sd 2:0:0:0: Attached scsi generic sg3 type 14
[   31.877010] end_request: I/O error, dev sdc, sector 7999480
[   31.877017] Buffer I/O error on device sdc, logical block 999935
[   31.882629] end_request: I/O error, dev sdc, sector 7999480
[   31.882637] Buffer I/O error on device sdc, logical block 999935
[   31.884494] end_request: I/O error, dev sdc, sector 7999480
[   31.884504] Buffer I/O error on device sdc, logical block 999935
[   31.889195] end_request: I/O error, dev sdc, sector 7999480
[   31.889202] Buffer I/O error on device sdc, logical block 999935
[   31.893508] end_request: I/O error, dev sdc, sector 7999480
[   31.893515] Buffer I/O error on device sdc, logical block 999935
[   31.895109] end_request: I/O error, dev sdc, sector 7999480
[   31.895120] Buffer I/O error on device sdc, logical block 999935
[   31.896185] end_request: I/O error, dev sdc, sector 7999480
[   31.896193] Buffer I/O error on device sdc, logical block 999935
[   31.951825] end_request: I/O error, dev sdc, sector 7999480
[   31.951836] Buffer I/O error on device sdc, logical block 999935
[   31.953806] end_request: I/O error, dev sdc, sector 7999480
[   31.953818] Buffer I/O error on device sdc, logical block 999935
[   31.956289] end_request: I/O error, dev sdc, sector 40
[   31.956297] Buffer I/O error on device sdc, logical block 5
[   31.958400] end_request: I/O error, dev sdc, sector 40
[   31.959467] end_request: I/O error, dev sdc, sector 40
[   31.963285] end_request: I/O error, dev sdc, sector 40
[   31.964388] end_request: I/O error, dev sdc, sector 40
[   31.997663] end_request: I/O error, dev sdc, sector 80191
[   31.999963] end_request: I/O error, dev sdc, sector 80191
[   32.001006] end_request: I/O error, dev sdc, sector 80193
[   32.050459] end_request: I/O error, dev sdc, sector 80303
[   32.054977] end_request: I/O error, dev sdc, sector 80325
[   32.056022] end_request: I/O error, dev sdc, sector 80329
[   32.058302] end_request: I/O error, dev sdc, sector 80303
[   32.061544] end_request: I/O error, dev sdc, sector 80325
[   32.062606] end_request: I/O error, dev sdc, sector 80329
[   32.067464] end_request: I/O error, dev sdc, sector 63
[   32.068589] end_request: I/O error, dev sdc, sector 65
[   32.070153] end_request: I/O error, dev sdc, sector 80325
[   32.094205] end_request: I/O error, dev sdc, sector 63
[   32.122230] end_request: I/O error, dev sdc, sector 63
[   32.123326] end_request: I/O error, dev sdc, sector 80319
[   32.124358] end_request: I/O error, dev sdc, sector 80321
[   32.125462] end_request: I/O error, dev sdc, sector 80319
[   32.126539] end_request: I/O error, dev sdc, sector 80321
[   32.127590] end_request: I/O error, dev sdc, sector 80319
[   32.128678] end_request: I/O error, dev sdc, sector 80321
[   32.134066] end_request: I/O error, dev sdc, sector 80319
[   32.135177] end_request: I/O error, dev sdc, sector 80319
[   32.136236] end_request: I/O error, dev sdc, sector 80321
[   32.137271] end_request: I/O error, dev sdc, sector 80325
[   32.138308] end_request: I/O error, dev sdc, sector 80329
[   32.139388] end_request: I/O error, dev sdc, sector 80319
[   32.140487] end_request: I/O error, dev sdc, sector 80321
[   32.141715] end_request: I/O error, dev sdc, sector 80255
[   32.142798] end_request: I/O error, dev sdc, sector 80257
[   32.143876] end_request: I/O error, dev sdc, sector 80311
[   32.144952] end_request: I/O error, dev sdc, sector 80313
[   32.146019] end_request: I/O error, dev sdc, sector 80319
[   32.147084] end_request: I/O error, dev sdc, sector 80321
[   32.148466] end_request: I/O error, dev sdc, sector 80319
[   32.149507] end_request: I/O error, dev sdc, sector 80321
[   32.150579] end_request: I/O error, dev sdc, sector 63
[   32.151647] end_request: I/O error, dev sdc, sector 65
[   32.152848] end_request: I/O error, dev sdc, sector 63
[   32.153909] end_request: I/O error, dev sdc, sector 65
[   32.158251] end_request: I/O error, dev sdc, sector 63
[   32.159359] end_request: I/O error, dev sdc, sector 65
[   32.160456] end_request: I/O error, dev sdc, sector 63
[   32.161497] end_request: I/O error, dev sdc, sector 65
[   32.162713] end_request: I/O error, dev sdc, sector 63
[   32.163790] end_request: I/O error, dev sdc, sector 65
[   32.164856] end_request: I/O error, dev sdc, sector 63
[   32.165914] end_request: I/O error, dev sdc, sector 65
[   32.167016] end_request: I/O error, dev sdc, sector 63
[   32.168086] end_request: I/O error, dev sdc, sector 65
[   32.171317] end_request: I/O error, dev sdc, sector 63
[   32.172508] end_request: I/O error, dev sdc, sector 65
[   32.173598] end_request: I/O error, dev sdc, sector 63
[   32.174702] end_request: I/O error, dev sdc, sector 65
[   32.175796] end_request: I/O error, dev sdc, sector 63
[   32.176849] end_request: I/O error, dev sdc, sector 65
[   32.177965] end_request: I/O error, dev sdc, sector 63
[   32.179049] end_request: I/O error, dev sdc, sector 65
[   32.180120] end_request: I/O error, dev sdc, sector 63
[   32.181172] end_request: I/O error, dev sdc, sector 65
[   32.183291] end_request: I/O error, dev sdc, sector 63
[   32.184357] end_request: I/O error, dev sdc, sector 65
[   32.185417] end_request: I/O error, dev sdc, sector 63
[   32.186472] end_request: I/O error, dev sdc, sector 65
[   32.187552] end_request: I/O error, dev sdc, sector 63
[   32.188596] end_request: I/O error, dev sdc, sector 65
[   32.189655] end_request: I/O error, dev sdc, sector 63
[   32.190686] end_request: I/O error, dev sdc, sector 65
[   32.191750] end_request: I/O error, dev sdc, sector 63
[   32.192958] end_request: I/O error, dev sdc, sector 65
[   32.194061] end_request: I/O error, dev sdc, sector 63
[   32.195158] end_request: I/O error, dev sdc, sector 65
[   32.196270] end_request: I/O error, dev sdc, sector 63
[   32.197292] end_request: I/O error, dev sdc, sector 65
[   32.199424] end_request: I/O error, dev sdc, sector 63
[   32.200496] end_request: I/O error, dev sdc, sector 65
[   32.201991] end_request: I/O error, dev sdc, sector 63
[   32.203197] end_request: I/O error, dev sdc, sector 65
[   32.204284] end_request: I/O error, dev sdc, sector 63
[   32.205374] end_request: I/O error, dev sdc, sector 65
[   32.206467] end_request: I/O error, dev sdc, sector 63
[   32.207531] end_request: I/O error, dev sdc, sector 65
[   32.209672] end_request: I/O error, dev sdc, sector 63
[   32.210748] end_request: I/O error, dev sdc, sector 65
[   32.211856] end_request: I/O error, dev sdc, sector 63
[   32.213054] end_request: I/O error, dev sdc, sector 65
[   32.214383] end_request: I/O error, dev sdc, sector 80325
[   32.215481] end_request: I/O error, dev sdc, sector 80325
[   32.216630] end_request: I/O error, dev sdc, sector 80329
[   32.217731] end_request: I/O error, dev sdc, sector 80325
[   32.218795] end_request: I/O error, dev sdc, sector 80329
[   32.219903] end_request: I/O error, dev sdc, sector 80325
[   32.220994] end_request: I/O error, dev sdc, sector 80329
[   32.222063] end_request: I/O error, dev sdc, sector 80325
[   32.223256] end_request: I/O error, dev sdc, sector 80329
[   32.225342] end_request: I/O error, dev sdc, sector 80325
[   32.226499] end_request: I/O error, dev sdc, sector 80329
[   32.227689] end_request: I/O error, dev sdc, sector 80325
[   32.228741] end_request: I/O error, dev sdc, sector 80329
[   32.229850] end_request: I/O error, dev sdc, sector 80325
[   32.230910] end_request: I/O error, dev sdc, sector 80329
[   32.234764] end_request: I/O error, dev sdc, sector 80325
[   32.235836] end_request: I/O error, dev sdc, sector 80329
[   32.237048] end_request: I/O error, dev sdc, sector 80325
[   32.238115] end_request: I/O error, dev sdc, sector 80329
[   32.239175] end_request: I/O error, dev sdc, sector 80325
[   32.240179] end_request: I/O error, dev sdc, sector 80329
[   32.241249] end_request: I/O error, dev sdc, sector 80325
[   32.242281] end_request: I/O error, dev sdc, sector 80329
[   32.243351] end_request: I/O error, dev sdc, sector 80325
[   32.244529] end_request: I/O error, dev sdc, sector 80329
[   32.245867] end_request: I/O error, dev sdc, sector 80325
[   32.246934] end_request: I/O error, dev sdc, sector 80329
[   32.248130] end_request: I/O error, dev sdc, sector 80325
[   32.249200] end_request: I/O error, dev sdc, sector 80329
[   32.252267] end_request: I/O error, dev sdc, sector 80325
[   32.253339] end_request: I/O error, dev sdc, sector 80329
[   32.254525] end_request: I/O error, dev sdc, sector 80325
[   32.255589] end_request: I/O error, dev sdc, sector 80329
[   32.256730] end_request: I/O error, dev sdc, sector 80325
[   32.257796] end_request: I/O error, dev sdc, sector 80329
[   32.258874] end_request: I/O error, dev sdc, sector 80325
[   32.259918] end_request: I/O error, dev sdc, sector 80329
[   32.261270] end_request: I/O error, dev sdc, sector 80325
[   32.262398] end_request: I/O error, dev sdc, sector 80329
[   32.263602] end_request: I/O error, dev sdc, sector 80325
[   32.264935] end_request: I/O error, dev sdc, sector 80329
[   32.266024] end_request: I/O error, dev sdc, sector 80325
[   32.267192] end_request: I/O error, dev sdc, sector 80329
[   32.268364] end_request: I/O error, dev sdc, sector 80325
[   32.269433] end_request: I/O error, dev sdc, sector 80329
[   32.270574] end_request: I/O error, dev sdc, sector 80325
[   32.271801] end_request: I/O error, dev sdc, sector 80329
[   32.779969] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.791204] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.034235] Linux agpgart interface v0.102 (c) Dave Jones
[   33.098002] agpgart: Detected an Intel 865 Chipset.
[   33.104611] agpgart: AGP aperture is 128M @ 0xe0000000
[   33.723360] intel_rng: FWH not detected
[   33.808100] iTCO_vendor_support: vendor-support=0
[   33.809530] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   34.018256] usbcore: registered new interface driver xpad
[   34.018263] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   34.077291] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[   34.077328] usbcore: registered new interface driver usblp
[   34.077333] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   34.171077] usbcore: registered new interface driver hiddev
[   34.198383] input: Logitech WingMan Cordless Gamepad as /class/input/input2
[   34.198418] input: USB HID v1.10 Joystick [Logitech WingMan Cordless Gamepad] on usb-0000:00:1d.3-1
[   34.198438] usbcore: registered new interface driver usbhid
[   34.198444] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.416630] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   34.416655] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   34.437075] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   34.440212] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[   34.440255] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.440469] input: PC Speaker as /class/input/input4
[   34.440767] parport_pc 00:0b: reported by Plug and Play ACPI
[   34.440809] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   34.739926] intel8x0_measure_ac97_clock: measured 54668 usecs
[   34.739930] intel8x0: clocking to 48000
[   35.481593] lp0: using parport0 (interrupt-driven).
[   35.531657] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   35.769807] EXT3 FS on sda2, internal journal
[   36.567039] kjournald starting.  Commit interval 5 seconds
[   36.572492] EXT3 FS on sdb1, internal journal
[   36.572498] EXT3-fs: mounted filesystem with ordered data mode.
[   37.191518] input: Power Button (FF) as /class/input/input5
[   37.191548] ACPI: Power Button (FF) [PWRF]
[   37.191611] input: Power Button (CM) as /class/input/input6
[   37.191639] ACPI: Power Button (CM) [PWRB]
[   37.257422] No dock devices found.
[   38.538431] ppdev: user-space parallel port driver
[   38.718151] audit(1193101283.108:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4883 profile="/usr/sbin/cupsd"
[   38.771173] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.771180] apm: disabled - APM is not SMP safe.
[   38.844688] skge eth0: enabling interface
[   38.912658] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   39.124581] Failure registering capabilities with primary security module.
[   39.234971] end_request: I/O error, dev sdc, sector 0
[   39.234977] printk: 224 messages suppressed.
[   39.234980] Buffer I/O error on device sdc, logical block 0
[   39.236305] end_request: I/O error, dev sdc, sector 0
[   39.237489] end_request: I/O error, dev sdc, sector 0
[   39.382121] end_request: I/O error, dev sdc, sector 80191
[   39.383448] end_request: I/O error, dev sdc, sector 80191
[   39.384456] end_request: I/O error, dev sdc, sector 80193
[   39.385747] end_request: I/O error, dev sdc, sector 80303
[   39.386913] end_request: I/O error, dev sdc, sector 80305
[   39.388005] end_request: I/O error, dev sdc, sector 80303
[   39.389039] end_request: I/O error, dev sdc, sector 80305
[   39.390463] end_request: I/O error, dev sdc, sector 63
[   39.391562] end_request: I/O error, dev sdc, sector 65
[   39.393265] end_request: I/O error, dev sdc, sector 63
[   39.394465] end_request: I/O error, dev sdc, sector 65
[   39.395916] end_request: I/O error, dev sdc, sector 63
[   39.397107] end_request: I/O error, dev sdc, sector 65
[   39.398957] end_request: I/O error, dev sdc, sector 80319
[   39.400153] end_request: I/O error, dev sdc, sector 80321
[   39.403339] end_request: I/O error, dev sdc, sector 80319
[   39.404382] end_request: I/O error, dev sdc, sector 80321
[   39.412526] end_request: I/O error, dev sdc, sector 80319
[   39.413592] end_request: I/O error, dev sdc, sector 80321
[   39.414712] end_request: I/O error, dev sdc, sector 80319
[   39.415783] end_request: I/O error, dev sdc, sector 80321
[   39.417236] end_request: I/O error, dev sdc, sector 80319
[   39.418282] end_request: I/O error, dev sdc, sector 80321
[   39.419498] end_request: I/O error, dev sdc, sector 80319
[   39.420535] end_request: I/O error, dev sdc, sector 80321
[   39.421872] end_request: I/O error, dev sdc, sector 80255
[   39.422912] end_request: I/O error, dev sdc, sector 80257
[   39.424019] end_request: I/O error, dev sdc, sector 80311
[   39.425198] end_request: I/O error, dev sdc, sector 80313
[   39.426288] end_request: I/O error, dev sdc, sector 80319
[   39.427458] end_request: I/O error, dev sdc, sector 80321
[   39.428503] end_request: I/O error, dev sdc, sector 80319
[   39.429703] end_request: I/O error, dev sdc, sector 80321
[   39.430854] end_request: I/O error, dev sdc, sector 63
[   39.431995] end_request: I/O error, dev sdc, sector 65
[   39.433084] end_request: I/O error, dev sdc, sector 63
[   39.434130] end_request: I/O error, dev sdc, sector 65
[   39.435197] end_request: I/O error, dev sdc, sector 63
[   39.436236] end_request: I/O error, dev sdc, sector 65
[   39.437585] end_request: I/O error, dev sdc, sector 63
[   39.438609] end_request: I/O error, dev sdc, sector 65
[   39.439825] end_request: I/O error, dev sdc, sector 63
[   39.440850] end_request: I/O error, dev sdc, sector 65
[   39.442046] end_request: I/O error, dev sdc, sector 63
[   39.443096] end_request: I/O error, dev sdc, sector 65
[   39.444322] end_request: I/O error, dev sdc, sector 63
[   39.445360] end_request: I/O error, dev sdc, sector 65
[   39.446438] end_request: I/O error, dev sdc, sector 63
[   39.447593] end_request: I/O error, dev sdc, sector 65
[   39.448797] end_request: I/O error, dev sdc, sector 63
[   39.449830] end_request: I/O error, dev sdc, sector 65
[   39.451136] end_request: I/O error, dev sdc, sector 63
[   39.452170] end_request: I/O error, dev sdc, sector 65
[   39.453469] end_request: I/O error, dev sdc, sector 63
[   39.454467] end_request: I/O error, dev sdc, sector 65
[   39.455541] end_request: I/O error, dev sdc, sector 63
[   39.456580] end_request: I/O error, dev sdc, sector 65
[   39.457784] end_request: I/O error, dev sdc, sector 63
[   39.458822] end_request: I/O error, dev sdc, sector 65
[   39.459885] end_request: I/O error, dev sdc, sector 63
[   39.461150] end_request: I/O error, dev sdc, sector 65
[   39.462226] end_request: I/O error, dev sdc, sector 63
[   39.463272] end_request: I/O error, dev sdc, sector 65
[   39.464353] end_request: I/O error, dev sdc, sector 63
[   39.465388] end_request: I/O error, dev sdc, sector 65
[   39.466431] end_request: I/O error, dev sdc, sector 63
[   39.467478] end_request: I/O error, dev sdc, sector 65
[   39.468923] end_request: I/O error, dev sdc, sector 63
[   39.469942] end_request: I/O error, dev sdc, sector 65
[   39.471013] end_request: I/O error, dev sdc, sector 63
[   39.472045] end_request: I/O error, dev sdc, sector 65
[   39.473099] end_request: I/O error, dev sdc, sector 63
[   39.474151] end_request: I/O error, dev sdc, sector 65
[   39.475433] end_request: I/O error, dev sdc, sector 63
[   39.476459] end_request: I/O error, dev sdc, sector 65
[   39.479569] end_request: I/O error, dev sdc, sector 63
[   39.480605] end_request: I/O error, dev sdc, sector 65
[   39.481713] end_request: I/O error, dev sdc, sector 63
[   39.482759] end_request: I/O error, dev sdc, sector 65
[   39.483837] end_request: I/O error, dev sdc, sector 63
[   39.484863] end_request: I/O error, dev sdc, sector 65
[   39.485923] end_request: I/O error, dev sdc, sector 63
[   39.486959] end_request: I/O error, dev sdc, sector 65
[   39.489642] end_request: I/O error, dev sdc, sector 0
[   39.490683] end_request: I/O error, dev sdc, sector 8
[   39.491714] end_request: I/O error, dev sdc, sector 0
[   39.492916] end_request: I/O error, dev sdc, sector 0
[   39.711267] Bluetooth: Core ver 2.11
[   39.711659] NET: Registered protocol family 31
[   39.711666] Bluetooth: HCI device and connection manager initialized
[   39.711673] Bluetooth: HCI socket layer initialized
[   39.747844] Bluetooth: L2CAP ver 2.8
[   39.747851] Bluetooth: L2CAP socket layer initialized
[   39.897965] end_request: I/O error, dev sdc, sector 80325
[   39.898972] end_request: I/O error, dev sdc, sector 80329
[   39.900219] end_request: I/O error, dev sdc, sector 80325
[   39.901360] end_request: I/O error, dev sdc, sector 80329
[   39.902810] end_request: I/O error, dev sdc, sector 80333
[   39.903849] end_request: I/O error, dev sdc, sector 80337
[   39.904899] end_request: I/O error, dev sdc, sector 80325
[   39.929699] Bluetooth: RFCOMM socket layer initialized
[   39.930095] Bluetooth: RFCOMM TTY layer initialized
[   39.930100] Bluetooth: RFCOMM ver 1.8
[   39.962903] end_request: I/O error, dev sdc, sector 80325
[   39.963953] end_request: I/O error, dev sdc, sector 80329
[   39.965282] end_request: I/O error, dev sdc, sector 80325
[   39.966295] end_request: I/O error, dev sdc, sector 80329
[   39.967726] end_request: I/O error, dev sdc, sector 80325
[   39.968770] end_request: I/O error, dev sdc, sector 80329
[   39.970192] end_request: I/O error, dev sdc, sector 80325
[   39.971250] end_request: I/O error, dev sdc, sector 80329
[   39.972588] end_request: I/O error, dev sdc, sector 80325
[   39.973635] end_request: I/O error, dev sdc, sector 80329
[   39.975178] end_request: I/O error, dev sdc, sector 80325
[   39.976231] end_request: I/O error, dev sdc, sector 80329
[   39.977639] end_request: I/O error, dev sdc, sector 80325
[   39.978660] end_request: I/O error, dev sdc, sector 80329
[   39.979816] end_request: I/O error, dev sdc, sector 80325
[   39.980862] end_request: I/O error, dev sdc, sector 80329
[   39.982121] end_request: I/O error, dev sdc, sector 80325
[   39.983131] end_request: I/O error, dev sdc, sector 80329
[   39.984397] end_request: I/O error, dev sdc, sector 80325
[   39.985461] end_request: I/O error, dev sdc, sector 80329
[   39.986767] end_request: I/O error, dev sdc, sector 80325
[   39.987956] end_request: I/O error, dev sdc, sector 80329
[   39.989120] end_request: I/O error, dev sdc, sector 80325
[   39.990135] end_request: I/O error, dev sdc, sector 80329
[   39.991537] end_request: I/O error, dev sdc, sector 80325
[   39.992842] end_request: I/O error, dev sdc, sector 80325
[   39.993849] end_request: I/O error, dev sdc, sector 80329
[   39.995123] end_request: I/O error, dev sdc, sector 80325
[   39.996193] end_request: I/O error, dev sdc, sector 80329
[   39.997708] end_request: I/O error, dev sdc, sector 80325
[   39.998750] end_request: I/O error, dev sdc, sector 80329
[   40.000113] end_request: I/O error, dev sdc, sector 80325
[   40.001163] end_request: I/O error, dev sdc, sector 80329
[   40.002450] end_request: I/O error, dev sdc, sector 80325
[   40.003492] end_request: I/O error, dev sdc, sector 80329
[   40.004851] end_request: I/O error, dev sdc, sector 80325
[   40.005881] end_request: I/O error, dev sdc, sector 80329
[   40.007446] end_request: I/O error, dev sdc, sector 80325
[   40.008593] end_request: I/O error, dev sdc, sector 80329
[   40.009656] end_request: I/O error, dev sdc, sector 80325
[   40.010693] end_request: I/O error, dev sdc, sector 80329
[   40.011751] end_request: I/O error, dev sdc, sector 80325
[   40.012819] end_request: I/O error, dev sdc, sector 80329
[   40.013875] end_request: I/O error, dev sdc, sector 80325
[   40.014919] end_request: I/O error, dev sdc, sector 80329
[   40.015980] end_request: I/O error, dev sdc, sector 80325
[   40.017025] end_request: I/O error, dev sdc, sector 80329
[   40.018219] end_request: I/O error, dev sdc, sector 80325
[   40.019257] end_request: I/O error, dev sdc, sector 80329
[   40.021422] end_request: I/O error, dev sdc, sector 0
[   40.022469] end_request: I/O error, dev sdc, sector 8
[   40.023509] end_request: I/O error, dev sdc, sector 0
[   40.024618] end_request: I/O error, dev sdc, sector 0
[   42.521562] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   42.526677] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   42.526709] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   42.781081] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.219202] NET: Registered protocol family 17
[   45.520223] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   45.520230] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   45.520234] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   45.521261] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   45.521461] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   45.521636] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   45.521809] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   45.530328] [fglrx] total      GART = 134217728
[   45.530335] [fglrx] free       GART = 118222848
[   45.530338] [fglrx] max single GART = 118222848
[   45.530340] [fglrx] total      LFB  = 134217728
[   45.530342] [fglrx] free       LFB  = 107171840
[   45.530344] [fglrx] max single LFB  = 107171840
[   45.530346] [fglrx] total      Inv  = 0
[   45.530347] [fglrx] free       Inv  = 0
[   45.530349] [fglrx] max single Inv  = 0
[   45.530351] [fglrx] total      TIM  = 0
[   46.785609] NET: Registered protocol family 10
[   46.786154] lo: Disabled Privacy Extensions
[   46.786695] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.327171] eth1: no IPv6 routers present
[   74.083356] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   74.083363] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   81.300158] UDF-fs: No VRS found
[   81.314650] ISO 9660 Extensions: Microsoft Joliet Level 3
[   81.342699] ISOFS: changing to secondary root
[  129.784387] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  129.784395] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  130.400573] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  130.400581] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  140.374151] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  140.374157] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  145.670977] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  145.670982] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  279.831497] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  279.831503] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  280.038076] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  280.038082] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  286.373770] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  286.373775] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  301.430635] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  301.430643] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  306.452723] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  306.452728] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  359.169481] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  359.169486] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.


This comes up if I type dmesg | tail:

> 
 dmesg | tail
[ 5135.413597] end_request: I/O error, dev sdc, sector 0
[ 5135.414552] end_request: I/O error, dev sdc, sector 0
[ 5135.415876] end_request: I/O error, dev sdc, sector 7999480
[ 5135.417225] end_request: I/O error, dev sdc, sector 0
[ 5135.418229] end_request: I/O error, dev sdc, sector 0
[ 5135.419475] end_request: I/O error, dev sdc, sector 0
[ 5135.426651] end_request: I/O error, dev sdc, sector 0
[ 5135.427682] end_request: I/O error, dev sdc, sector 8
[ 5135.428609] end_request: I/O error, dev sdc, sector 0
[ 5135.429575] end_request: I/O error, dev sdc, sector 0


---

### Post by Stambo00 on 2007-10-25
Bump?

I can confirm the ipod works in debian etch using the firewire. So whats going on then?

---

### Post by deltateam2 on 2007-10-30
I have some problem.  I shouldn't have update to gutsy as it is a rather inopportune time to not have my ipod for listening to lectures.  :/

anyone fix this?

I have roughly the same dmesg.

---

### Post by misterbeetz on 2007-10-30
I also seem to have problems mounting my firewire ipod in gutsy (worked fine in feisty).  It seems to mount upon boot but once I unplug it doesn't seem to mount any more after that.  My external usb hard drive is also having the same problem.

- misterbeetz

---

### Post by Yv12345vY on 2007-11-02
Bump.  Same problem here.

---

### Post by Stambo00 on 2007-11-09
This seems to be a common problem, yes? Maybe we should file a bug report?

Anyone else had any luck fixing this problem?

---

### Post by chez17 on 2007-11-19
Bump. Same problem, The ipod doesn't even show the screen saying 'Do not disconnect' so my ipod doesn't even know its connected.

---

### Post by Stambo00 on 2007-11-21
I just installed the latest updates.

And.....

Firewire iPod now works! Thank-you Ubuntu!

How about everyone else?

---

### Post by stmiller on 2007-11-22
I'm still having this problem with my firewire ipod. This is the output of dmesg:

```
[  192.640378] end_request: I/O error, dev sdb, sector 80327
[  192.640951] end_request: I/O error, dev sdb, sector 80325
[  192.641490] end_request: I/O error, dev sdb, sector 80327
[  192.642629] end_request: I/O error, dev sdb, sector 0
[  192.643263] end_request: I/O error, dev sdb, sector 8
[  192.643816] end_request: I/O error, dev sdb, sector 0
[  192.644409] end_request: I/O error, dev sdb, sector 0
```

:(

There were [significant changes]("http://wiki.linux1394.org/ReleaseNotesKernel") to the kernel firewire module from kernel 2.6.22 to 2.6.23. I am trying 2.6.23 on gutsy and still having same issue though.

EDIT: I found [this]("http://www.mail-archive.com/debian-kernel@lists.debian.org/msg28620.html") bug report which looks to be related.


EDIT 2:

I just tried the latest 2.6.23.8 kernel, and looks like it keeps trying to connect, but can't.

```

Nov 22 14:06:09 localhost kernel: [  378.211874] ohci1394: fw-host0: Got reqTxComplete interrupt status=0x00008012
Nov 22 14:06:09 localhost kernel: [  378.211877] ohci1394: fw-host0: Packet sent to node 0 tcode=0x1 tLabel=40 ack=0x12 spd=0 dataLength=8 ctx=0
Nov 22 14:06:09 localhost kernel: [  378.212092] ohci1394: fw-host0: IntEvent: 00000020
Nov 22 14:06:09 localhost kernel: [  378.212095] ohci1394: fw-host0: Got RSPkt interrupt status=0x00008451
Nov 22 14:06:09 localhost kernel: [  378.212099] ohci1394: fw-host0: Single packet rcv'd
Nov 22 14:06:09 localhost kernel: [  378.212103] ohci1394: fw-host0: Packet received from node 0 ack=0x11 spd=2 tcode=0x2 length=16 ctx=0 tlabel=40
Nov 22 14:06:09 localhost kernel: [  378.212381] ohci1394: fw-host0: IntEvent: 00000010
Nov 22 14:06:09 localhost kernel: [  378.212384] ohci1394: fw-host0: Got RQPkt interrupt status=0x00008451
Nov 22 14:06:09 localhost kernel: [  378.212388] ohci1394: fw-host0: Single packet rcv'd
Nov 22 14:06:09 localhost kernel: [  378.212392] ohci1394: fw-host0: Packet received from node 0 ack=0x11 spd=2 tcode=0x1 length=28 ctx=0 tlabel=3
Nov 22 14:06:10 localhost kernel: [  378.672513] ohci1394: fw-host0: IntEvent: 00020010
Nov 22 14:06:10 localhost kernel: [  378.672520] ohci1394: fw-host0: irq_handler: Bus reset requested
Nov 22 14:06:10 localhost kernel: [  378.672523] ohci1394: fw-host0: Cancel request received
Nov 22 14:06:10 localhost kernel: [  378.672527] ohci1394: fw-host0: Got RQPkt interrupt status=0x00008409
Nov 22 14:06:10 localhost kernel: [  378.672531] ohci1394: fw-host0: Single packet rcv'd
Nov 22 14:06:10 localhost kernel: [  378.672536] ohci1394: fw-host0: IntEvent: 00010000
Nov 22 14:06:10 localhost kernel: [  378.672538] ohci1394: fw-host0: SelfID interrupt received (phyid 0, root)
Nov 22 14:06:10 localhost kernel: [  378.672541] ohci1394: fw-host0: SelfID packet 0x807f8952 received
Nov 22 14:06:10 localhost kernel: [  378.672545] ohci1394: fw-host0: SelfID for this node is 0x807f8952
Nov 22 14:06:10 localhost kernel: [  378.672547] ohci1394: fw-host0: SelfID complete
Nov 22 14:06:10 localhost kernel: [  378.672550] ohci1394: fw-host0: PhyReqFilter=ffffffffffffffff

```

---

### Post by Stambo00 on 2007-11-23
It was false hope! It has gone back to not working. It actually only worked once after installing the updates I mentioned earlier.

I tried mounting my iPod via firewire in a Gusty Live CD on the same computer and it worked fine! It seems like the problem only occurred after installing.

Still lost for suggestions!

---

