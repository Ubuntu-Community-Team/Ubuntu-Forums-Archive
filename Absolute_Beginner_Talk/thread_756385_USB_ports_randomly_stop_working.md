---
title: "USB ports randomly stop working"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by steelisreal on 2008-04-15
Seemingly at random my usb ports have stopped working.  It begin with the ports in the rear and then the front ports go out maybe 2 minutes later.  It fixes itself on reboot.  I have yet to notice anything that I am doing at the time of them going out.

here is what i get when i do a dmesg | grep usb
```

[   33.159087] usbcore: registered new interface driver usbfs
[   33.159110] usbcore: registered new interface driver hub
[   33.159134] usbcore: registered new device driver usb
[   33.215875] usb usb1: configuration #1 chosen from 1 choice
[   33.329774] usb usb2: configuration #1 chosen from 1 choice
[   34.357668] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   34.576623] usb 1-2: configuration #1 chosen from 1 choice
[   34.882086] usb 1-4: new full speed USB device using ohci_hcd and address 3
[   35.096082] usb 1-4: configuration #1 chosen from 1 choice
[   35.097940] usbcore: registered new interface driver hiddev
[   35.107975] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input2
[   35.127649] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-2
[   35.127667] usbcore: registered new interface driver usbhid
[   35.127670] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.129156] usbcore: registered new interface driver libusual
[   35.142148] usbcore: registered new interface driver usb-storage
[   35.142250] usb-storage: device found at 3
[   35.142252] usb-storage: waiting for device to settle before scanning
[   40.137789] usb-storage: device scan complete
[   49.760941] usbcore: registered new interface driver lmpcm_usb
[   49.760947] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
```

---

### Post by spiderbatdad on 2008-04-15
you might try adding pci=routeirq to the end of the kernel line in /boot/grub/menu.lst

---

### Post by steelisreal on 2008-04-15
> **spiderbatdad said:**
> you might try adding pci=routeirq to the end of the kernel line in /boot/grub/menu.lst

I am new so please excuse my ignorance.

How do I go about doing that and what exactly would it do?

Also is there any other information I should post.

---

### Post by spiderbatdad on 2008-04-15
This is done by opening /boot/grub/menu.lst  (Lst, as in list) in superuser mode, so that you have write permission in the file. You would open a command line interface (CLI) by clicking, Applications>>Accessories>>Terminal. Then input the following:```
gksu gedit /boot/grub/menu.lst
``` Input your password. You will not see any response that the password is being input...just type it in, and hit enter. The file will open.

Scroll down to the section that begins: *****END DEFAULT OPTIONS********

```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd0,0)
**kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

```

The default kernel is the first one listed unless user modified. I have highlighted the kernel line above. At the end  of the line, I have added 'lapic pci=routeirq' as boot parameters. I suggested that you add pci=routeirq.  Save the file by clicking the little floppy disk image near the top of the window. I do not know if it will help your situation, but it may. Reboot. 
You can read the output of :```
dmesg
``` for more information.

---

### Post by steelisreal on 2008-04-15
Thank you I added what you suggested, we will see if it helps

I am not sure what part of dmesg is helpful, here is the whole thing

```
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515547
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=aca902ec-5fb2-419a-9035-2e4ef792f560 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   22.263488] Marking TSC unstable due to TSCs unsynchronized
[   22.263490] time.c: Detected 2204.590 MHz processor.
[   22.264928] Console: colour VGA+ 80x25
[   22.264931] console [tty0] enabled
[   22.264946] Checking aperture...
[   22.264948] CPU 0: aperture @ cd30000000 size 32 MB
[   22.264950] Aperture too small (32 MB)
[   22.271830] No AGP bridge found
[   22.290257] Memory: 2054468k/2096064k available (2466k kernel code, 41208k reserved, 1309k data, 316k init)
[   22.290290] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.369368] Calibrating delay using timer specific routine.. 4413.13 BogoMIPS (lpj=8826260)
[   22.369398] Security Framework initialized
[   22.369404] SELinux:  Disabled at boot.
[   22.369416] AppArmor: AppArmor initialized
[   22.369420] Failure registering capabilities with primary security module.
[   22.369561] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   22.370778] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.371366] Mount-cache hash table entries: 256
[   22.371493] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.371495] CPU: L2 Cache: 512K (64 bytes/line)
[   22.371497] CPU 0/0 -> Node 0
[   22.371499] CPU: Physical Processor ID: 0
[   22.371500] CPU: Processor Core ID: 0
[   22.371519] SMP alternatives: switching to UP code
[   22.372050] Early unpacking initramfs... done
[   22.651667] ACPI: Core revision 20070126
[   22.651720] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.698062] Using local APIC timer interrupts.
[   22.743378] APIC timer calibration result 12526082
[   22.743380] Detected 12.526 MHz APIC timer.
[   22.743466] SMP alternatives: switching to SMP code
[   22.743909] Booting processor 1/2 APIC 0x1
[   22.754188] Initializing CPU#1
[   22.831526] Calibrating delay using timer specific routine.. 4409.21 BogoMIPS (lpj=8818432)
[   22.831531] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.831533] CPU: L2 Cache: 512K (64 bytes/line)
[   22.831535] CPU 1/1 -> Node 0
[   22.831537] CPU: Physical Processor ID: 0
[   22.831538] CPU: Processor Core ID: 1
[   22.831613] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   22.831430] Brought up 2 CPUs
[   22.831555] CPU0 attaching sched-domain:
[   22.831557]  domain 0: span 03
[   22.831559]   groups: 01 02
[   22.831561]   domain 1: span 03
[   22.831563]    groups: 03
[   22.831564] CPU1 attaching sched-domain:
[   22.831566]  domain 0: span 03
[   22.831567]   groups: 02 01
[   22.831569]   domain 1: span 03
[   22.831570]    groups: 03
[   22.831780] net_namespace: 120 bytes
[   22.832172] Time: 22:19:52  Date: 04/15/08
[   22.832203] NET: Registered protocol family 16
[   22.832368] ACPI: bus type pci registered
[   22.832430] PCI: Using configuration type 1
[   22.833681] ACPI: EC: Look up EC in DSDT
[   22.839930] ACPI: Interpreter enabled
[   22.839932] ACPI: (supports S0 S3 S4 S5)
[   22.839944] ACPI: Using IOAPIC for interrupt routing
[   22.848623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.849581] PCI: Transparent bridge - 0000:00:10.0
[   22.849597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.849849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.938623] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.938795] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   22.938963] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.939132] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[   22.939304] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[   22.939472] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.939640] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.939808] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.939978] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   22.940145] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.940314] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   22.940482] ACPI: PCI Interrupt Link [LACI] (IRQs *5 7 9 10 11 14 15)
[   22.940651] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.940822] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)
[   22.940990] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.941160] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   22.941328] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   22.941495] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.941665] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   22.941866] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   22.942060] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   22.942253] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   22.942446] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   22.942639] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   22.942832] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   22.943026] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   22.943227] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   22.943421] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.943615] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.943813] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.944007] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   22.944201] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   22.944396] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   22.944591] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   22.944786] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.944981] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.945176] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   22.945370] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.945569] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.945698] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.945721] pnp: PnP ACPI init
[   22.945729] ACPI: bus type pnp registered
[   22.950320] pnpacpi: exceeded the max number of mem resources: 12
[   22.950377] pnp: PnP ACPI: found 11 devices
[   22.950379] ACPI: ACPI bus type pnp unregistered
[   22.950576] PCI: Using ACPI for IRQ routing
[   22.950580] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.959205] NET: Registered protocol family 8
[   22.959207] NET: Registered protocol family 20
[   22.959315] AppArmor: AppArmor Filesystem Enabled
[   22.971186] system 00:01: ioport range 0x1000-0x107f has been reserved
[   22.971188] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   22.971190] system 00:01: ioport range 0x1400-0x147f has been reserved
[   22.971192] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   22.971194] system 00:01: ioport range 0x1800-0x187f has been reserved
[   22.971197] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   22.971199] system 00:01: ioport range 0x2000-0x207f has been reserved
[   22.971201] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   22.971204] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   22.971206] system 00:01: iomem range 0x0-0x0 could not be reserved
[   22.971211] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   22.971214] system 00:02: ioport range 0x800-0x80f has been reserved
[   22.971216] system 00:02: ioport range 0x290-0x29f has been reserved
[   22.971218] system 00:02: ioport range 0x290-0x297 has been reserved
[   22.971226] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.971231] system 00:0a: iomem range 0xd0000-0xd3fff has been reserved
[   22.971233] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved
[   22.971235] system 00:0a: iomem range 0xf0000-0xfbfff could not be reserved
[   22.971238] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[   22.971240] system 00:0a: iomem range 0x7fef0000-0x7fefffff could not be reserved
[   22.971242] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[   22.971244] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   22.971247] system 00:0a: iomem range 0x100000-0x7feeffff could not be reserved
[   22.971249] system 00:0a: iomem range 0x0-0x0 could not be reserved
[   22.971251] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.971253] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[   22.971255] system 00:0a: iomem range 0xfefff000-0xfeffffff has been reserved
[   22.971587] PCI: Bridge: 0000:00:03.0
[   22.971589]   IO window: c000-cfff
[   22.971592]   MEM window: fe800000-fe8fffff
[   22.971594]   PREFETCH window: fe700000-fe7fffff
[   22.971598] PCI: Bridge: 0000:00:04.0
[   22.971600]   IO window: b000-bfff
[   22.971602]   MEM window: fb000000-fdffffff
[   22.971603]   PREFETCH window: d0000000-dfffffff
[   22.971606] PCI: Bridge: 0000:00:10.0
[   22.971607]   IO window: a000-afff
[   22.971610]   MEM window: fea00000-feafffff
[   22.971612]   PREFETCH window: fe900000-fe9fffff
[   22.971625] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.971631] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   22.971638] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   22.971649] NET: Registered protocol family 2
[   22.975155] Time: acpi_pm clocksource has been installed.
[   22.975171] Switched to high resolution mode on CPU 0
[   22.975491] Switched to high resolution mode on CPU 1
[   23.007188] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.007915] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   23.010317] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.010913] TCP: Hash tables configured (established 262144 bind 65536)
[   23.010916] TCP reno registered
[   23.019213] checking if image is initramfs... it is
[   23.562207] Freeing initrd memory: 7513k freed
[   23.567874] audit: initializing netlink socket (disabled)
[   23.567888] audit(1208297992.272:1): initialized
[   23.569835] VFS: Disk quotas dquot_6.5.1
[   23.569898] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.569996] io scheduler noop registered
[   23.569998] io scheduler anticipatory registered
[   23.570000] io scheduler deadline registered
[   23.570090] io scheduler cfq registered (default)
[   23.588033] Boot video device is 0000:02:00.0
[   23.588214] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   23.588234] assign_interrupt_mode Found MSI capability
[   23.588251] Allocate Port Service[0000:00:03.0:pcie00]
[   23.588312] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   23.588331] assign_interrupt_mode Found MSI capability
[   23.588344] Allocate Port Service[0000:00:04.0:pcie00]
[   23.612976] Real Time Clock Driver v1.12ac
[   23.613070] Linux agpgart interface v0.102
[   23.613072] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.614036] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.614096] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.614173] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.614175] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   23.614580] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.627735] mice: PS/2 mouse device common for all mice
[   23.627772] cpuidle: using governor ladder
[   23.627774] cpuidle: using governor menu
[   23.627903] NET: Registered protocol family 1
[   23.627955] registered taskstats version 1
[   23.628080]   Magic number: 4:719:350
[   23.628199] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.628202] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.628203] EDD information not available.
[   23.628216] Freeing unused kernel memory: 316k freed
[   23.662644] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.809321] fuse init (API version 7.9)
[   24.823062] ACPI: Fan [FAN] (on)
[   24.829297] ACPI: Thermal Zone [THRM] (17 C)
[   25.262353] usbcore: registered new interface driver usbfs
[   25.262375] usbcore: registered new interface driver hub
[   25.262417] usbcore: registered new device driver usb
[   25.262588] SCSI subsystem initialized
[   25.269181] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   25.269195] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   25.269367] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   25.269375] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   25.269639] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   25.269674] ehci_hcd 0000:00:0b.1: debug port 1
[   25.269678] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   25.269690] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xfebfe000
[   25.271923] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.272773] libata version 3.00 loaded.
[   25.280631] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.280754] usb usb1: configuration #1 chosen from 1 choice
[   25.280774] hub 1-0:1.0: USB hub found
[   25.280780] hub 1-0:1.0: 8 ports detected
[   25.385112] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   25.385124] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   25.385290] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   25.385297] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   25.385348] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   25.385368] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfebff000
[   25.442565] usb usb2: configuration #1 chosen from 1 choice
[   25.442588] hub 2-0:1.0: USB hub found
[   25.442596] hub 2-0:1.0: 8 ports detected
[   25.544544] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   25.544895] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   25.544905] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   25.544911] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   26.064179] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:15:58:53:d0:49
[   26.064184] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   26.064979] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   26.065001] ACPI: PCI Interrupt 0000:03:06.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   26.111716] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   26.115086] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   26.114949] pata_amd 0000:00:0d.0: version 0.3.10
[   26.115008] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   26.117599] scsi0 : pata_amd
[   26.118375] scsi1 : pata_amd
[   26.119061] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   26.119063] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   26.288191] ata1.00: ATA-6: WDC WD3200BB-00KEA0, 08.05J08, max UDMA/100
[   26.288195] ata1.00: 625142448 sectors, multi 16: LBA48 
[   26.293476] ata1.01: ATA-8: WDC WD3200AAJB-00WGA0, 00.02C01, max UDMA/100
[   26.293478] ata1.01: 625142448 sectors, multi 16: LBA48 
[   26.308102] ata1.00: configured for UDMA/100
[   26.325310] ata1.01: configured for UDMA/100
[   26.329869] usb 2-2: configuration #1 chosen from 1 choice
[   26.636454] usb 2-4: new full speed USB device using ohci_hcd and address 3
[   26.644661] ata2.00: ATAPI: HL-DT-ST DVD-RW GSA-H11N, JG03, max UDMA/66
[   26.816410] ata2.00: configured for UDMA/66
[   26.816278] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BB-00K 08.0 PQ: 0 ANSI: 5
[   26.816365] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3200AAJB-0 00.0 PQ: 0 ANSI: 5
[   26.821121] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GSA-H11N  JG03 PQ: 0 ANSI: 5
[   26.820972] sata_nv 0000:00:0e.0: version 3.5
[   26.821326] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   26.821336] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   26.821525] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   26.824938] scsi2 : sata_nv
[   26.825944] scsi3 : sata_nv
[   26.826119] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[   26.826122] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[   26.851336] usb 2-4: configuration #1 chosen from 1 choice
[   26.854150] usbcore: registered new interface driver hiddev
[   26.864173] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input2
[   26.886890] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-2
[   26.886907] usbcore: registered new interface driver usbhid
[   26.886911] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.888350] usbcore: registered new interface driver libusual
[   26.900083] Initializing USB Mass Storage driver...
[   26.901241] scsi4 : SCSI emulation for USB Mass Storage devices
[   26.902040] usbcore: registered new interface driver usb-storage
[   26.902043] USB Mass Storage support registered.
[   26.902352] usb-storage: device found at 3
[   26.902357] usb-storage: waiting for device to settle before scanning
[   27.134593] ata3: SATA link down (SStatus 0 SControl 300)
[   27.382652] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200020b1e9]
[   27.454488] ata4: SATA link down (SStatus 0 SControl 300)
[   27.472772] Driver 'sd' needs updating - please use bus_type methods
[   27.472861] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.472871] sd 0:0:0:0: [sda] Write Protect is off
[   27.472873] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.472886] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.472932] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.472939] sd 0:0:0:0: [sda] Write Protect is off
[   27.472941] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.472952] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.472955]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   27.479051]  sda1
[   27.479119] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.479185] sd 0:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   27.479196] sd 0:0:1:0: [sdb] Write Protect is off
[   27.479198] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.479212] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.479254] sd 0:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   27.479262] sd 0:0:1:0: [sdb] Write Protect is off
[   27.479264] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.479276] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.479280]  sdb: sdb1 sdb2 < sdb5 >
[   27.500062] sd 0:0:1:0: [sdb] Attached SCSI disk
[   27.503611] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.503629] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   27.503644] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   27.506264] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   27.506270] Uniform CD-ROM driver Revision: 3.20
[   27.506325] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   27.862096] Attempting manual resume
[   27.862100] swsusp: Resume From Partition 8:21
[   27.862101] PM: Checking swsusp image.
[   27.862323] PM: Resume from disk failed.
[   27.876294] EXT3-fs: INFO: recovery required on readonly filesystem.
[   27.876299] EXT3-fs: write access will be enabled during recovery.
[   30.185920] kjournald starting.  Commit interval 5 seconds
[   30.186171] EXT3-fs: recovery complete.
[   30.186665] EXT3-fs: mounted filesystem with ordered data mode.
[   31.896038] usb-storage: device scan complete
[   31.902774] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   31.909770] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   31.916754] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   31.923758] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   31.934776] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   31.934801] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   32.213466] sd 4:0:0:1: [sdd] 1000944 512-byte hardware sectors (512 MB)
[   32.226449] sd 4:0:0:1: [sdd] Write Protect is off
[   32.226452] sd 4:0:0:1: [sdd] Mode Sense: 03 00 00 00
[   32.226454] sd 4:0:0:1: [sdd] Assuming drive cache: write through
[   32.252417] sd 4:0:0:1: [sdd] 1000944 512-byte hardware sectors (512 MB)
[   32.265411] sd 4:0:0:1: [sdd] Write Protect is off
[   32.265413] sd 4:0:0:1: [sdd] Mode Sense: 03 00 00 00
[   32.265414] sd 4:0:0:1: [sdd] Assuming drive cache: write through
[   32.265417]  sdd: sdd1
[   32.283443] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   32.283466] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   32.294399] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   32.294420] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   32.305394] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   32.305418] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   39.387967] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   39.498459] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.534431] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.642318] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xfc00
[   39.642336] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf800
[   39.729049] parport_pc 00:07: reported by Plug and Play ACPI
[   39.729104] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.769656] input: Power Button (FF) as /devices/virtual/input/input4
[   39.835186] ath_hal: module license 'Proprietary' taints kernel.
[   39.837050] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   39.865999] ACPI: Power Button (FF) [PWRF]
[   39.866059] input: Power Button (CM) as /devices/virtual/input/input5
[   39.917914] ACPI: Power Button (CM) [PWRB]
[   39.942744] wlan: 0.9.4
[   39.978702] ath_pci: 0.9.4
[   39.979131] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   39.979144] ACPI: PCI Interrupt 0000:03:08.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   40.600227] ath_rate_sample: 1.2 (0.9.4)
[   40.601211] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   40.601216] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   40.601223] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   40.601225] wifi0: mac 7.8 phy 4.5 radio 5.6
[   40.601229] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   40.601230] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   40.601232] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   40.601233] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   40.601235] wifi0: Use hw queue 8 for CAB traffic
[   40.601236] wifi0: Use hw queue 9 for beacons
[   40.709417] wifi0: Atheros 5212: mem=0xfeae0000, irq=17
[   41.300408] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   41.300413] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 23
[   41.300566] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   41.626997] usbcore: registered new interface driver lmpcm_usb
[   41.627004] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   41.679926] intel8x0_measure_ac97_clock: measured 53077 usecs
[   41.679930] intel8x0: clocking to 46890
[   41.683162] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   41.683175] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   41.683182] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   41.683330] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   43.399122] lp0: using parport0 (interrupt-driven).
[   43.498374] Adding 6040400k swap on /dev/sdb5.  Priority:-1 extents:1 across:6040400k
[   44.046529] EXT3 FS on sdb1, internal journal
[   45.124581] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.451546] No dock devices found.
[   45.812281] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   45.812136] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   45.812140] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   45.812142] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   45.812144] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   47.836328] eth0: no link during initialization.
[   48.033781] ppdev: user-space parallel port driver
[   48.159860] audit(1208316017.855:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5460 profile="/usr/sbin/cupsd" namespace="default"
[   48.343179] Bluetooth: Core ver 2.11
[   48.343926] NET: Registered protocol family 31
[   48.343930] Bluetooth: HCI device and connection manager initialized
[   48.343935] Bluetooth: HCI socket layer initialized
[   48.357311] Bluetooth: L2CAP ver 2.9
[   48.357316] Bluetooth: L2CAP socket layer initialized
[   48.361618] Bluetooth: RFCOMM socket layer initialized
[   48.361636] Bluetooth: RFCOMM TTY layer initialized
[   48.361638] Bluetooth: RFCOMM ver 1.8
[   49.359456] Clocksource tsc unstable (delta = -82920314 ns)
[   56.272560] NET: Registered protocol family 10
[   56.272770] lo: Disabled Privacy Extensions
[   56.273146] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.778615] ISO 9660 Extensions: Microsoft Joliet Level 1
[   60.781150] ISOFS: changing to secondary root
[   62.589289] ath0: no IPv6 routers present
[   63.347532] NET: Registered protocol family 17
[   81.042353] ath0: no IPv6 routers present
```

---

### Post by steelisreal on 2008-04-21
This issue is still occuring, it did seem to stop for a few days after adding the pci=routeirq that spiderbatdad recommended.

It is extremely annoying and seems to not have any trigger that causes it.

Please help with this issue.

---

