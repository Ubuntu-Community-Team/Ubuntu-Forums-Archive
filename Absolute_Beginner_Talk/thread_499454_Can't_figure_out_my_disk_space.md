---
title: "Can't figure out my disk space"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-07-12
I recently had a disk space error message although I can't figure out why...

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              36G   34G     0 100% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  104K 1014M   1% /proc/bus/usb
udev                 1014M  104K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   15M  999M   2% /lib/modules/2.6.20-16-generic/volatile

```

---

### Post by pbaehr on 2007-07-12
It would appear you've completely filled your hard drive (/dev/sda4).

---

### Post by insane_alien on 2007-07-12
your root partition is 100% full

it is the top line on that output. 

try deleting some things.

---

### Post by bean77 on 2007-07-12
It was fine yesterday and I don't think I downloaded anything since then?

---

### Post by davidjmayo on 2007-07-12
Check your log files. If there is a problem one could be writing an error repeatedly

---

### Post by pbaehr on 2007-07-12
It may have been nearly full for a long time and something just pushed it over the edge. 'du' can provide you with more detailed information about what files take up what space, but it can be cumbersome when run on a directory with a lot of files or directories. Maybe someone has a better command to help you find where you can cut down on some disk use.

---

### Post by bean77 on 2007-07-12
I just put all of my music and photos on a DVD...I've freed up about 2%.

How would I go about checking davidjmayo's idea?

Thanks so much!

---

### Post by twiceasworn on 2007-07-12
The first thing I would take a look at is your messages log.

```
tail -100 /var/log/messages
```

That should give you the last 100 lines of /var/log/messages.  There are other logs in that directory as well that you may want to look at.

---

### Post by bapoumba on 2007-07-12
```
sudo aptitude clean
```
Will make some room on your system partition.

Look also in you /home and in your ~/.Trash

---

### Post by bean77 on 2007-07-12
> **twiceasworn said:**
> The first thing I would take a look at is your messages log.

```
tail -100 /var/log/messages
```

That should give you the last 100 lines of /var/log/messages.  There are other logs in that directory as well that you may want to look at.

OK, this is what I get:

```
Jul 12 17:05:14 lydia-desktop kernel: [   12.405073] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 17:05:14 lydia-desktop kernel: [   12.405199] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Jul 12 17:05:14 lydia-desktop kernel: [   12.405274] sda: Write Protect is off
Jul 12 17:05:14 lydia-desktop kernel: [   12.405352] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 17:05:14 lydia-desktop kernel: [   12.405436]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
Jul 12 17:05:14 lydia-desktop kernel: [   12.446353] sd 1:0:0:0: Attached scsi disk sda
Jul 12 17:05:14 lydia-desktop kernel: [   12.450888] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jul 12 17:05:14 lydia-desktop kernel: [   12.502381] ehci_hcd 0000:00:10.4: EHCI Host Controller
Jul 12 17:05:14 lydia-desktop kernel: [   12.502482] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 2
Jul 12 17:05:14 lydia-desktop kernel: [   12.502593] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
Jul 12 17:05:14 lydia-desktop kernel: [   12.502661] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 17:05:14 lydia-desktop kernel: [   12.502830] usb usb2: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   12.502919] hub 2-0:1.0: USB hub found
Jul 12 17:05:14 lydia-desktop kernel: [   12.502984] hub 2-0:1.0: 8 ports detected
Jul 12 17:05:14 lydia-desktop kernel: [   12.609128] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jul 12 17:05:14 lydia-desktop kernel: [   12.609235] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Jul 12 17:05:14 lydia-desktop kernel: [   12.609344] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
Jul 12 17:05:14 lydia-desktop kernel: [   12.609502] usb usb3: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   12.609598] hub 3-0:1.0: USB hub found
Jul 12 17:05:14 lydia-desktop kernel: [   12.609663] hub 3-0:1.0: 2 ports detected
Jul 12 17:05:14 lydia-desktop kernel: [   12.681930] Attempting manual resume
Jul 12 17:05:14 lydia-desktop kernel: [   12.697814] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 12 17:05:14 lydia-desktop kernel: [   12.697886] EXT3-fs: write access will be enabled during recovery.
Jul 12 17:05:14 lydia-desktop kernel: [   12.715345] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jul 12 17:05:14 lydia-desktop kernel: [   12.715434] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Jul 12 17:05:14 lydia-desktop kernel: [   12.715532] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
Jul 12 17:05:14 lydia-desktop kernel: [   12.715688] usb usb4: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   12.715776] hub 4-0:1.0: USB hub found
Jul 12 17:05:14 lydia-desktop kernel: [   12.715841] hub 4-0:1.0: 2 ports detected
Jul 12 17:05:14 lydia-desktop kernel: [   12.819388] uhci_hcd 0000:00:10.3: UHCI Host Controller
Jul 12 17:05:14 lydia-desktop kernel: [   12.819478] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Jul 12 17:05:14 lydia-desktop kernel: [   12.819574] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
Jul 12 17:05:14 lydia-desktop kernel: [   12.819724] usb usb5: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   12.819811] hub 5-0:1.0: USB hub found
Jul 12 17:05:14 lydia-desktop kernel: [   12.819877] hub 5-0:1.0: 2 ports detected
Jul 12 17:05:14 lydia-desktop kernel: [   12.923689] eth0: VIA Rhine II at 0x1cc00, 00:16:17:c3:51:2e, IRQ 23.
Jul 12 17:05:14 lydia-desktop kernel: [   12.924745] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
Jul 12 17:05:14 lydia-desktop kernel: [   12.999527] usb 2-2: new high speed USB device using ehci_hcd and address 2
Jul 12 17:05:14 lydia-desktop kernel: [   13.018629] kjournald starting.  Commit interval 5 seconds
Jul 12 17:05:14 lydia-desktop kernel: [   13.018641] EXT3-fs: recovery complete.
Jul 12 17:05:14 lydia-desktop kernel: [   13.018985] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 17:05:14 lydia-desktop kernel: [   13.134724] usb 2-2: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   14.104848] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 12 17:05:14 lydia-desktop kernel: [   14.274556] usb 3-2: configuration #1 chosen from 1 choice
Jul 12 17:05:14 lydia-desktop kernel: [   19.710787] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 12 17:05:14 lydia-desktop kernel: [   20.692383] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 17:05:14 lydia-desktop kernel: [   20.695462] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 17:05:14 lydia-desktop kernel: [   20.787016] Linux agpgart interface v0.102 (c) Dave Jones
Jul 12 17:05:14 lydia-desktop kernel: [   20.815888] agpgart: Detected VIA VT3314 chipset
Jul 12 17:05:14 lydia-desktop kernel: [   20.824087] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 12 17:05:14 lydia-desktop kernel: [   20.984109] parport: PnPBIOS parport detected.
Jul 12 17:05:14 lydia-desktop kernel: [   20.984222] parport0: PC-style at 0x378, irq 7 [PCSPP]
Jul 12 17:05:14 lydia-desktop kernel: [   21.295382] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
Jul 12 17:05:14 lydia-desktop kernel: [   21.318603] nvidia: module license 'NVIDIA' taints kernel.
Jul 12 17:05:14 lydia-desktop kernel: [   21.578763] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
Jul 12 17:05:14 lydia-desktop kernel: [   21.608468] input: PC Speaker as /class/input/input3
Jul 12 17:05:14 lydia-desktop kernel: [   21.620979] NET: Registered protocol family 17
Jul 12 17:05:14 lydia-desktop kernel: [   21.692096] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1086
Jul 12 17:05:14 lydia-desktop kernel: [   21.692190] usbcore: registered new interface driver usblp
Jul 12 17:05:14 lydia-desktop kernel: [   21.692254] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jul 12 17:05:14 lydia-desktop kernel: [   22.515417] fuse init (API version 7.8)
Jul 12 17:05:14 lydia-desktop kernel: [   22.530776] lp0: using parport0 (interrupt-driven).
Jul 12 17:05:14 lydia-desktop kernel: [   22.690049] Adding 1662656k swap on /dev/disk/by-uuid/31da93c4-f86f-40c9-9dbf-ec52741b00fc.  Priority:-1 extents:1 across:1662656k
Jul 12 17:05:14 lydia-desktop kernel: [   22.783539] EXT3 FS on sda4, internal journal
Jul 12 17:05:14 lydia-desktop kernel: [   22.917091] NET: Registered protocol family 10
Jul 12 17:05:14 lydia-desktop kernel: [   22.917183] lo: Disabled Privacy Extensions
Jul 12 17:05:14 lydia-desktop kernel: [   28.441061] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Jul 12 17:05:14 lydia-desktop kernel: [   28.441100] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Jul 12 17:05:14 lydia-desktop kernel: [   28.441202] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Jul 12 17:05:14 lydia-desktop kernel: [   28.441252] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
Jul 12 17:05:17 lydia-desktop dhcdbd: Started up.
Jul 12 17:05:17 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 12 17:05:17 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 12 17:05:17 lydia-desktop kernel: [   30.658046] ppdev: user-space parallel port driver
Jul 12 17:05:18 lydia-desktop kernel: [   31.389282] NVRM: failed to register with the ACPI subsystem!
Jul 12 17:05:19 lydia-desktop kernel: [   31.731073] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul 12 17:05:19 lydia-desktop kernel: [   31.731092] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 12 17:05:19 lydia-desktop kernel: [   31.731178] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 12 17:05:19 lydia-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 12 17:05:20 lydia-desktop kernel: [   32.830770] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul 12 17:05:20 lydia-desktop kernel: [   32.830777] apm: disabled - APM is not SMP safe.
Jul 12 17:05:20 lydia-desktop kernel: [   33.072501] Bluetooth: Core ver 2.11
Jul 12 17:05:20 lydia-desktop kernel: [   33.072558] NET: Registered protocol family 31
Jul 12 17:05:20 lydia-desktop kernel: [   33.072562] Bluetooth: HCI device and connection manager initialized
Jul 12 17:05:20 lydia-desktop kernel: [   33.072567] Bluetooth: HCI socket layer initialized
Jul 12 17:05:20 lydia-desktop kernel: [   33.082903] Bluetooth: L2CAP ver 2.8
Jul 12 17:05:20 lydia-desktop kernel: [   33.082909] Bluetooth: L2CAP socket layer initialized
Jul 12 17:05:20 lydia-desktop kernel: [   33.287693] Bluetooth: RFCOMM socket layer initialized
Jul 12 17:05:20 lydia-desktop kernel: [   33.287705] Bluetooth: RFCOMM TTY layer initialized
Jul 12 17:05:20 lydia-desktop kernel: [   33.287707] Bluetooth: RFCOMM ver 1.8
Jul 12 17:05:24 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 12 17:05:24 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 12 17:05:24 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): starting (version 2.18.0.1), pid 5343 user 'lydia'
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readwrite:/home/lydia/.gconf" to a writable configuration source at position 1
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 12 17:05:31 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 12 17:05:34 lydia-desktop gconfd (lydia-5343): Resolved address "xml:readwrite:/home/lydia/.gconf" to a writable configuration source at position 0

```

---

### Post by twiceasworn on 2007-07-12
```
Jul 12 17:05:14 lydia-desktop kernel: [   12.681930] Attempting manual resume
Jul 12 17:05:14 lydia-desktop kernel: [   12.697814] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 12 17:05:14 lydia-desktop kernel: [   12.697886] EXT3-fs: write access will be enabled during recovery.
```

This worries me a little bit, seems that this is caused when the disk has to many write errors.  Does ```
tail -100 /var/log/syslog
```have anything interesting in it?

---

### Post by davidjmayo on 2007-07-12
thanx twiceasworn

Sorry I have not replied but I have my own issues at the moment
Sorry to go off thread but I can't do anything on this site. If I try to reply or refresh the page I find I'm logged out and have to login again. I tried another browser but that made no difference. Is there a problem with this site?

---

### Post by pbaehr on 2007-07-12
> **twiceasworn said:**
> ```
Jul 12 17:05:14 lydia-desktop kernel: [   12.681930] Attempting manual resume
Jul 12 17:05:14 lydia-desktop kernel: [   12.697814] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 12 17:05:14 lydia-desktop kernel: [   12.697886] EXT3-fs: write access will be enabled during recovery.
```

This worries me a little bit, seems that this is caused when the disk has to many write errors.  Does ```
tail -100 /var/log/syslog
```have anything interesting in it?

Just a thought, could the write errors be caused by the 100% hard drive usage?

---

### Post by twiceasworn on 2007-07-12
I would say that they are probably related, if not one in the same.  Either way multiple write errors aren't good for the health of the drive, thats for sure.

EDIT:  Also for future reference, I would write a perl script or shell script ( or download one, they are all over ) that checks your diskspace regularly and emails you when it is getting full.  Or you could also just set a cronjob that executes the command "df -h" and have it set to go every couple days.  It will email you whatever is output during the cronjob.

---

### Post by bean77 on 2007-07-12
Does ```
tail -100 /var/log/syslog
```have anything interesting in it?[/QUOTE]

```
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IDeactivating device eth0. 
Jul 12 18:37:38 lydia-desktop avahi-daemon[4714]: Withdrawing address record for 192.168.1.102 on eth0.
Jul 12 18:37:38 lydia-desktop avahi-daemon[4714]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
Jul 12 18:37:38 lydia-desktop avahi-daemon[4714]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 12 18:37:38 lydia-desktop avahi-daemon[4714]: Withdrawing address record for fe80::216:17ff:fec3:512e on eth0.
Jul 12 18:37:38 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Jul 12 18:37:38 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IWill activate connection 'eth0'. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IDevice eth0 activation scheduled... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) started... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jul 12 18:37:38 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jul 12 18:37:38 lydia-desktop kernel: [   29.550902] ppdev: user-space parallel port driver
Jul 12 18:37:39 lydia-desktop kernel: [   30.018916] NVRM: failed to register with the ACPI subsystem!
Jul 12 18:37:39 lydia-desktop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Jul 12 18:37:39 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jul 12 18:37:39 lydia-desktop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Jul 12 18:37:40 lydia-desktop kernel: [   30.360412] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul 12 18:37:40 lydia-desktop kernel: [   30.360433] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 12 18:37:40 lydia-desktop kernel: [   30.360507] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 12 18:37:40 lydia-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 12 18:37:40 lydia-desktop kernel: [   31.444312] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul 12 18:37:40 lydia-desktop kernel: [   31.444317] apm: disabled - APM is not SMP safe.
Jul 12 18:37:40 lydia-desktop hcid[4997]: Bluetooth HCI daemon
Jul 12 18:37:40 lydia-desktop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Jul 12 18:37:40 lydia-desktop NetworkManager: <debug info>^I[1184279860.897535] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul 12 18:37:40 lydia-desktop kernel: [   31.668798] Bluetooth: Core ver 2.11
Jul 12 18:37:40 lydia-desktop kernel: [   31.668850] NET: Registered protocol family 31
Jul 12 18:37:40 lydia-desktop kernel: [   31.668852] Bluetooth: HCI device and connection manager initialized
Jul 12 18:37:40 lydia-desktop kernel: [   31.668855] Bluetooth: HCI socket layer initialized
Jul 12 18:37:40 lydia-desktop hcid[4997]: Starting SDP server
Jul 12 18:37:40 lydia-desktop kernel: [   31.708003] Bluetooth: L2CAP ver 2.8
Jul 12 18:37:40 lydia-desktop kernel: [   31.708007] Bluetooth: L2CAP socket layer initialized
Jul 12 18:37:41 lydia-desktop kernel: [   31.850796] Bluetooth: RFCOMM socket layer initialized
Jul 12 18:37:41 lydia-desktop kernel: [   31.850806] Bluetooth: RFCOMM TTY layer initialized
Jul 12 18:37:41 lydia-desktop kernel: [   31.850808] Bluetooth: RFCOMM ver 1.8
Jul 12 18:37:41 lydia-desktop anacron[5045]: Anacron 2.3 started on 2007-07-12
Jul 12 18:37:41 lydia-desktop anacron[5045]: Normal exit (0 jobs run)
Jul 12 18:37:41 lydia-desktop /usr/sbin/cron[5076]: (CRON) INFO (pidfile fd = 3)
Jul 12 18:37:41 lydia-desktop /usr/sbin/cron[5077]: (CRON) STARTUP (fork ok)
Jul 12 18:37:41 lydia-desktop /usr/sbin/cron[5077]: (CRON) INFO (Running @reboot jobs)
Jul 12 18:37:42 lydia-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jul 12 18:37:42 lydia-desktop dhclient: DHCPACK from 192.168.1.1
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: New relevant interface eth0.IPv4 for mDNS.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Registering new address record for 192.168.1.102 on eth0.IPv4.
Jul 12 18:37:42 lydia-desktop dhclient: bound to 192.168.1.102 -- renewal in 40979 seconds.
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jul 12 18:37:42 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 12 18:37:42 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 12 18:37:42 lydia-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  address 192.168.1.102 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  netmask 255.255.255.0 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  broadcast 192.168.1.255 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  gateway 192.168.1.1 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  nameserver 68.87.71.226 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  nameserver 68.87.73.242 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^I  domain name 'lndnnh.adelphia.net' 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jul 12 18:37:42 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Withdrawing address record for 192.168.1.102 on eth0.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: New relevant interface eth0.IPv4 for mDNS.
Jul 12 18:37:42 lydia-desktop avahi-daemon[4714]: Registering new address record for 192.168.1.102 on eth0.IPv4.
Jul 12 18:37:43 lydia-desktop NetworkManager: <information>^IClearing nscd hosts cache. 
Jul 12 18:37:43 lydia-desktop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul 12 18:37:43 lydia-desktop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Jul 12 18:37:43 lydia-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul 12 18:37:43 lydia-desktop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Jul 12 18:37:42 lydia-desktop ntpdate[5220]: step time server 82.211.81.145 offset -1.275139 sec
Jul 12 18:37:43 lydia-desktop avahi-daemon[4714]: Registering new address record for fe80::216:17ff:fec3:512e on eth0.*.
Jul 12 18:37:52 lydia-desktop kernel: [   44.560292] eth0: no IPv6 routers present
Jul 12 18:57:35 lydia-desktop -- MARK --
Jul 12 19:17:01 lydia-desktop /USR/SBIN/CRON[5227]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 12 19:17:33 lydia-desktop gconfd (lydia-5273): starting (version 2.18.0.1), pid 5273 user 'lydia'
Jul 12 19:17:34 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 12 19:17:34 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readwrite:/home/lydia/.gconf" to a writable configuration source at position 1
Jul 12 19:17:34 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 12 19:17:34 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 12 19:17:34 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 12 19:17:37 lydia-desktop gconfd (lydia-5273): Resolved address "xml:readwrite:/home/lydia/.gconf" to a writable configuration source at position 0
Jul 12 19:17:39 lydia-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul 12 19:17:39 lydia-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

```

---

### Post by twiceasworn on 2007-07-12
Did you manage to free up some space?  What exactly is in your root partition that is taking up so much space?  As stated above I am pretty sure that the write errors are from there being no space to write to.

---

