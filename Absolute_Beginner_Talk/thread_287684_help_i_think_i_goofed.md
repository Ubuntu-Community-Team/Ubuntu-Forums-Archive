---
title: "help i think i goofed"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-29
i set out to change the write pemission in my media folder ,had the command typed in and hit enter,and suffered a power failure,so when the power came back on i srartd my computer,
 well it went in to a forced check or something and i have this problem
 
/dev/hda1 :unexpected inconsistency run/fsrab manually
   (ie.,without -a or -p options)
 line1 in etc/fstab is bad
  
 it tells me to do this in recovery mode or whatever,
 
 so how do i get to that mode and what commands do i give to fix this problem

---

### Post by taurus on 2006-10-29
You can get into recovery mode from GRUB menu!!!  Boot from that and at the prompt, you can edit your /etc/fstab again...

```
nano -B /etc/fstab
```
Otherwise, boot from the LiveCD, mount your harddrive here / is, and edit your /etc/fstab.

---

### Post by STREETURCHINE on 2006-10-29
> **taurus said:**
> You can get into recovery mode from GRUB menu!!!  Boot from that and at the prompt, you can edit your /etc/fstab again...

```
nano -B /etc/fstab
```
Otherwise, boot from the LiveCD, mount your harddrive here / is, and edit your /etc/fstab.

ok i have the livecd in already so how do i mount the hard drive,ps i have no idea how the commands work so they have to be exactly as i should type them in.yes total newbie here,thanks

---

### Post by taurus on 2006-10-29
Wait for it to finish booting.  Then, open a terminal with Applications -> Accessories -> Terminal, and type

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu 
(assuming that your / is on /dev/hda1...)
gksudo gedit /mnt/ubuntu/etc/fstab
```
Now, make the correct changes and save it.  Unmount your harddrive and reboot.

```
sudo umount /mnt/ubuntu
```

---

### Post by STREETURCHINE on 2006-10-29
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ gksudo gedit /mnt/ubuntu/etc/fstab

(gedit:7631): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$


i dont know if i did this the right way but here is what happend

---

### Post by taurus on 2006-10-29
Do you know what partition is your / because it's not /dev/hda1?  What is the output of this command from a prompt?

```
sudo fdisk -l
```

---

### Post by STREETURCHINE on 2006-10-29
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23944   192330148+  83  Linux
/dev/hda2           23945       24321     3028252+   5  Extended
/dev/hda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326   83  Linux
ubuntu@ubuntu:~$



here is the out put

---

### Post by STREETURCHINE on 2006-10-29
(gedit:7631): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$   dmesg | tail  or so
tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory
ubuntu@ubuntu:~$  dmesg | tail
[17179664.052000] Bluetooth: Core ver 2.8
[17179664.052000] NET: Registered protocol family 31
[17179664.052000] Bluetooth: HCI device and connection manager initialized
[17179664.052000] Bluetooth: HCI socket layer initialized
[17179664.248000] Bluetooth: L2CAP ver 2.8
[17179664.248000] Bluetooth: L2CAP socket layer initialized
[17179664.552000] Bluetooth: RFCOMM socket layer initialized
[17179664.552000] Bluetooth: RFCOMM TTY layer initialized
[17179664.552000] Bluetooth: RFCOMM ver 1.7
[17181479.808000] ext3: No journal on filesystem on hda1
ubuntu@ubuntu:~$ dmesg so
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262064
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32688 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa100
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x04000521 MSFT 0x00000097) @ 0x3ffb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x04000521 MSFT 0x00000097) @ 0x3ffb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x04000521 MSFT 0x00000097) @ 0x3ffb0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x04000521 MSFT 0x00000097) @ 0x3ffc0040
[17179569.184000] ACPI: DSDT (v001  75VM8 75VM8000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3000.496 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.332000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.332000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.356000] Memory: 1028436k/1048256k available (1976k kernel code, 19156k reserved, 606k data, 288k init, 130752k highmem)
[17179570.356000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.436000] Calibrating delay using timer specific routine.. 6008.28 BogoMIPS (lpj=12016575)
[17179570.436000] Security Framework v1.0.0 initialized
[17179570.436000] SELinux:  Disabled at boot.
[17179570.436000] Mount-cache hash table entries: 512
[17179570.436000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179570.436000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179570.436000] monitor/mwait feature present.
[17179570.436000] using mwait in idle threads.
[17179570.436000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.436000] CPU: L2 cache: 2048K
[17179570.436000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000649d 00000000 00000000
[17179570.436000] mtrr: v2.0 (20020519)
[17179570.436000] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179570.436000] Enabling fast FPU save and restore... done.
[17179570.436000] Enabling unmasked SIMD FPU exception support... done.
[17179570.436000] Checking 'hlt' instruction... OK.
[17179570.452000] checking if image is initramfs... it is
[17179570.984000] Freeing initrd memory: 6843k freed
[17179570.992000] ACPI: Looking for DSDT ... not found!
[17179570.992000] ENABLING IO-APIC IRQs
[17179570.996000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.136000] NET: Registered protocol family 16
[17179571.136000] EISA bus registered
[17179571.136000] ACPI: bus type pci registered
[17179571.136000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[17179571.136000] PCI: Using configuration type 1
[17179571.136000] ACPI: Subsystem revision 20051216
[17179571.140000] ACPI: Interpreter enabled
[17179571.140000] ACPI: Using IOAPIC for interrupt routing
[17179571.140000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.140000] PCI: Probing PCI hardware (bus 00)
[17179571.144000] Boot video device is 0000:01:00.0
[17179571.144000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.156000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179571.164000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179571.164000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.164000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.164000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179571.164000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.164000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.164000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.164000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.164000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.164000] pnp: PnP ACPI init
[17179571.168000] pnp: PnP ACPI: found 10 devices
[17179571.168000] PnPBIOS: Disabled by ACPI PNP
[17179571.168000] PCI: Using ACPI for IRQ routing
[17179571.168000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.176000] PCI: Bridge: 0000:00:01.0
[17179571.176000]   IO window: disabled.
[17179571.176000]   MEM window: fc200000-fe2fffff
[17179571.176000]   PREFETCH window: dff00000-efefffff
[17179571.176000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.176000] audit: initializing netlink socket (disabled)
[17179571.176000] audit(1162105313.176:1): initialized
[17179571.176000] highmem bounce pool size: 64 pages
[17179571.176000] VFS: Disk quotas dquot_6.5.1
[17179571.176000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.176000] Initializing Cryptographic API
[17179571.176000] io scheduler noop registered
[17179571.176000] io scheduler anticipatory registered
[17179571.176000] io scheduler deadline registered
[17179571.176000] io scheduler cfq registered
[17179571.176000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179571.176000] isapnp: Scanning for PnP cards...
[17179571.528000] isapnp: No Plug & Play device found
[17179571.544000] PNP: No PS/2 controller found. Probing ports directly.
[17179571.544000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.544000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.544000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.544000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.548000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.548000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[17179571.548000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.548000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.548000] mice: PS/2 mouse device common for all mice
[17179571.548000] EISA: Probing bus 0 at eisa.0
[17179571.548000] EISA: Detected 0 cards.
[17179571.548000] NET: Registered protocol family 2
[17179571.588000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.588000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179571.588000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.588000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.588000] TCP reno registered
[17179571.588000] TCP bic registered
[17179571.588000] NET: Registered protocol family 1
[17179571.588000] NET: Registered protocol family 8
[17179571.588000] NET: Registered protocol family 20
[17179571.588000] Using IPI Shortcut mode
[17179571.588000] ACPI wakeup devices:
[17179571.588000] PCI0 UAR1 MC97 USB1 USB2 USB3 USB4 ILAN
[17179571.588000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.588000] Freeing unused kernel memory: 288k freed
[17179571.632000] vga16fb: initializing
[17179571.632000] vga16fb: mapped to 0xc00a0000
[17179571.760000] Console: switching to colour frame buffer device 80x25
[17179571.760000] fb0: VGA16 VGA frame buffer device
[17179572.868000] Capability LSM initialized
[17179573.332000] SCSI subsystem initialized
[17179573.332000] ACPI: bus type scsi registered
[17179573.332000] libata version 1.20 loaded.
[17179573.332000] sata_via 0000:00:0f.0: version 1.1
[17179573.332000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[17179573.332000] sata_via 0000:00:0f.0: routed to hard irq line 11
[17179573.332000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 169
[17179573.332000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 169
[17179574.500000] scsi0 : sata_via
[17179575.668000] scsi1 : sata_via
[17179575.696000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179575.696000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[17179575.696000] PCI: VIA IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179575.696000] VP_IDE: chipset revision 6
[17179575.696000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.696000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179575.696000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179575.696000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[17179575.696000] Probing IDE interface ide0...
[17179576.112000] hda: WDC WD2000JB-00GVC0, ATA DISK drive
[17179576.392000] hdb: HDS728080PLAT20, ATA DISK drive
[17179576.448000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.472000] Probing IDE interface ide1...
[17179577.620000] hdd: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
[17179577.676000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.680000] hda: max request size: 1024KiB
[17179577.744000] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179577.744000] hda: cache flushes supported
[17179577.744000]  hda: hda1 hda2 < hda5 >
[17179577.796000] hdb: max request size: 1024KiB
[17179577.796000] hdb: 160836480 sectors (82348 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(133)
[17179577.796000] hdb: cache flushes supported
[17179577.796000]  hdb: hdb1
[17179577.808000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[17179577.808000] Uniform CD-ROM driver Revision: 3.20
[17179578.160000] ieee1394: Initialized config rom entry `ip1394'
[17179578.160000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.160000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179578.216000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[febff000-febff7ff]  Max Packet=[2048]
[17179578.228000] usbcore: registered new driver usbfs
[17179578.228000] usbcore: registered new driver hub
[17179578.232000] USB Universal Host Controller Interface driver v2.3
[17179578.284000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 185
[17179578.284000] PCI: VIA IRQ fixup for 0000:00:10.0, from 10 to 9
[17179578.284000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.288000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.288000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000c000
[17179578.288000] hub 1-0:1.0: USB hub found
[17179578.288000] hub 1-0:1.0: 2 ports detected
[17179578.392000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 185
[17179578.392000] PCI: VIA IRQ fixup for 0000:00:10.1, from 10 to 9
[17179578.392000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.392000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.392000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000c400
[17179578.392000] hub 2-0:1.0: USB hub found
[17179578.392000] hub 2-0:1.0: 2 ports detected
[17179578.496000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 185
[17179578.496000] PCI: VIA IRQ fixup for 0000:00:10.2, from 11 to 9
[17179578.496000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.496000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.496000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000c800
[17179578.496000] hub 3-0:1.0: USB hub found
[17179578.496000] hub 3-0:1.0: 2 ports detected
[17179578.600000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 185
[17179578.600000] PCI: VIA IRQ fixup for 0000:00:10.3, from 11 to 9
[17179578.600000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179578.600000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.600000] uhci_hcd 0000:00:10.3: irq 185, io base 0x0000cc00
[17179578.600000] hub 4-0:1.0: USB hub found
[17179578.600000] hub 4-0:1.0: 2 ports detected
[17179578.704000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 185
[17179578.704000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179578.704000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179578.704000] ehci_hcd 0000:00:10.4: irq 185, io mem 0xfebff800
[17179578.704000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.704000] hub 5-0:1.0: USB hub found
[17179578.704000] hub 5-0:1.0: 8 ports detected
[17179579.556000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011066645556c63]
[17179579.876000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179579.896000] ISO 9660 Extensions: RRIP_1991A
[17179579.924000] loop: loaded (max 8 devices)
[17179579.936000] Registering unionfs 1.1.2
[17179579.980000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[17179579.996000] usb 2-2: new low speed USB device using uhci_hcd and address 2[17179580.184000] usbcore: registered new driver hiddev
[17179580.204000] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input0
[17179580.204000] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:10.1-2
[17179580.348000] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input1
[17179580.348000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:10.1-2
[17179580.348000] usbcore: registered new driver usbhid
[17179580.348000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179613.404000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179613.404000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179613.404000] eth0: VIA Rhine II at 0x1d400, 00:0b:6a:e3:51:74, IRQ 193.
[17179613.408000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 40a1.
[17179630.688000] eth0: link up, 100Mbps, half-duplex, lpa 0x40A1
[17179630.772000] ts: Compaq touchscreen protocol output
[17179631.768000] NET: Registered protocol family 17
[17179632.144000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179632.980000] NET: Registered protocol family 10
[17179632.980000] lo: Disabled Privacy Extensions
[17179632.980000] IPv6 over IPv4 tunneling driver
[17179633.060000] Linux agpgart interface v0.101 (c) Dave Jones
[17179633.892000] parport: PnPBIOS parport detected.
[17179633.892000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179633.988000] input: PC Speaker as /class/input/input2
[17179634.116000] Floppy drive(s): fd0 is 1.44M
[17179634.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179634.140000] FDC 0 is a post-1991 82077
[17179634.248000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179634.264000] agpgart: AGP aperture is 64M @ 0xf4000000
[17179634.352000] Real Time Clock Driver v1.12
[17179634.412000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 201
[17179634.412000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179635.900000] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[17179636.140000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179636.140000] md: bitmap version 4.39
[17179636.468000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179643.356000] eth0: no IPv6 routers present
[17179644.352000] ACPI: Power Button (FF) [PWRF]
[17179644.352000] ACPI: Power Button (CM) [PWRB]
[17179644.436000] ibm_acpi: ec object not found
[17179644.464000] pcc_acpi: loading...
[17179655.628000] lp0: using parport0 (interrupt-driven).
[17179655.672000] ppdev: user-space parallel port driver
[17179657.568000] apm: BIOS not found.
[17179664.052000] Bluetooth: Core ver 2.8
[17179664.052000] NET: Registered protocol family 31
[17179664.052000] Bluetooth: HCI device and connection manager initialized
[17179664.052000] Bluetooth: HCI socket layer initialized
[17179664.248000] Bluetooth: L2CAP ver 2.8
[17179664.248000] Bluetooth: L2CAP socket layer initialized
[17179664.552000] Bluetooth: RFCOMM socket layer initialized
[17179664.552000] Bluetooth: RFCOMM TTY layer initialized
[17179664.552000] Bluetooth: RFCOMM ver 1.7
[17181479.808000] ext3: No journal on filesystem on hda1
ubuntu@ubuntu:~$

this is the output after dmesg so

---

