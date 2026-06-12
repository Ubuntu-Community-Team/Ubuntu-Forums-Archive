---
title: "What the heck is this? :: cpu freq:change failed with new state 0 and result 0"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by webmiester on 2007-12-09
Hi guys,

Im using Gutsy Gibbon ubuntu.  Lastely, my bootup screen disappeared (I have a different thread on this).  Strangely though, I noticed that when I press Ctrl-Alt-F1, the resolution of the terminal screen is really big (like old computers)

Then if I wait for awhile, the following error appears:

webmiester@mobile-one-linux:~$ [559.06000] cpufreq: change failed with new_state 0 and result 0

Then it starts displaying block garbage all over my screen and stops working :(

From here I can press Ctrl-Alt F2, and get a new terminal.  The same thing happend after a few seconds wait.  Then number [599.06000] changes to another number though...  Actually when it first happened the number was at 400+, then it kept increasing...

It happens again at F3, etc.  The strange thing with the Ctrl-Alt-F3 is that there was a follow-up:  Instead of a garbage screen appearing, the following came up:

webmiester@mobile-one-linux:~$ [581.040000] cpufreq: change failed with new_state 1 and result 0

Then it stops working.  I can get back to my GUI by pressing Ctrl-Alt-F7, then everything is still normal within the Gnome environment.  Running a terminal window from Gnome also has no problem.

Does anyone have any idea what this is?

---

### Post by CRCarl on 2007-12-09
Can you post your messages file?

```
cat /var/log/messages
```

Thanks,

C

---

### Post by webmiester on 2007-12-10
the message log only displays what happened today.  Unfortunately, I cant recreate the problem anymore.  Now when I press Ctrl-Alt-F1, Im given a blank screen.  A check on the log file reveals that it isnt updated after I do that (the time which is listed on the last event remains the same no matter how often I press Ctrl-Alt-F1, F2, F3,...)

Is there a way to display the log of a few days ago?

---

### Post by webmiester on 2007-12-10
Anyway, here's what it displays:

Dec 10 01:44:40 mobile-one-linux kernel: [    7.600000] Clocksource tsc unstable (delta = -90444856 ns)
Dec 10 01:44:40 mobile-one-linux kernel: [   20.816000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 10 01:44:40 mobile-one-linux kernel: [   20.820000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 10 01:44:40 mobile-one-linux kernel: [   20.920000] Yenta: CardBus bridge found at 0000:00:03.0 [1028:00b0]
Dec 10 01:44:40 mobile-one-linux kernel: [   20.920000] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 10 01:44:40 mobile-one-linux kernel: [   20.920000] Yenta: Routing CardBus interrupts to PCI
Dec 10 01:44:40 mobile-one-linux kernel: [   20.920000] Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x64
Dec 10 01:44:40 mobile-one-linux kernel: [   20.944000] Linux agpgart interface v0.102 (c) Dave Jones
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Socket status: 30000006
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Yenta: CardBus bridge found at 0000:00:03.1 [1028:00b0]
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Yenta: Routing CardBus interrupts to PCI
Dec 10 01:44:40 mobile-one-linux kernel: [   21.152000] Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x64
Dec 10 01:44:40 mobile-one-linux kernel: [   21.384000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Dec 10 01:44:40 mobile-one-linux kernel: [   21.384000] Socket status: 30000006
Dec 10 01:44:40 mobile-one-linux kernel: [   21.400000] agpgart: Detected an Intel 440BX Chipset.
Dec 10 01:44:40 mobile-one-linux kernel: [   21.404000] agpgart: AGP aperture is 64M @ 0xf0000000
Dec 10 01:44:40 mobile-one-linux kernel: [   23.352000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
Dec 10 01:44:40 mobile-one-linux kernel: [   23.596000] input: PC Speaker as /class/input/input2
Dec 10 01:44:40 mobile-one-linux kernel: [   24.264000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x378-0x37f
Dec 10 01:44:40 mobile-one-linux kernel: [   24.264000] cs: IO port probe 0x3e0-0x4ff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.264000] cs: IO port probe 0x820-0x8ff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.264000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.264000] cs: IO port probe 0xa00-0xaff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.272000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Dec 10 01:44:40 mobile-one-linux kernel: [   24.272000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec 10 01:44:40 mobile-one-linux kernel: [   24.280000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x378-0x37f
Dec 10 01:44:40 mobile-one-linux kernel: [   24.280000] cs: IO port probe 0x3e0-0x4ff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.280000] cs: IO port probe 0x820-0x8ff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.280000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.280000] cs: IO port probe 0xa00-0xaff: clean.
Dec 10 01:44:40 mobile-one-linux kernel: [   24.520000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Dec 10 01:44:40 mobile-one-linux kernel: [   24.548000] parport_pc 00:0e: reported by Plug and Play ACPI
Dec 10 01:44:40 mobile-one-linux kernel: [   24.548000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Dec 10 01:44:40 mobile-one-linux kernel: [   25.296000] lp0: using parport0 (interrupt-driven).
Dec 10 01:44:40 mobile-one-linux kernel: [   25.400000] Adding 3478064k swap on /dev/sda3.  Priority:-1 extents:1 across:3478064k
Dec 10 01:44:40 mobile-one-linux kernel: [   25.888000] EXT3 FS on sda2, internal journal
Dec 10 01:44:40 mobile-one-linux kernel: [   53.340000] ACPI: ACPI Dock Station Driver 
Dec 10 01:44:40 mobile-one-linux kernel: [   53.388000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Dec 10 01:44:40 mobile-one-linux kernel: [   53.492000] input: Lid Switch as /class/input/input4
Dec 10 01:44:40 mobile-one-linux kernel: [   53.492000] ACPI: Lid Switch [LID]
Dec 10 01:44:40 mobile-one-linux kernel: [   53.520000] input: Power Button (CM) as /class/input/input5
Dec 10 01:44:40 mobile-one-linux kernel: [   53.520000] ACPI: Power Button (CM) [PBTN]
Dec 10 01:44:40 mobile-one-linux kernel: [   53.536000] input: Sleep Button (CM) as /class/input/input6
Dec 10 01:44:40 mobile-one-linux kernel: [   53.536000] ACPI: Sleep Button (CM) [SBTN]
Dec 10 01:44:40 mobile-one-linux kernel: [   53.844000] ACPI: AC Adapter [AC] (on-line)
Dec 10 01:44:40 mobile-one-linux kernel: [   54.452000] ACPI: Battery Slot [BAT0] (battery present)
Dec 10 01:44:40 mobile-one-linux kernel: [   54.452000] ACPI: Battery Slot [BAT1] (battery absent)
Dec 10 01:44:41 mobile-one-linux kernel: [   59.540000] ppdev: user-space parallel port driver
Dec 10 01:44:41 mobile-one-linux kernel: [   59.696000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Dec 10 01:44:42 mobile-one-linux kernel: [   60.192000] audit(1197222282.114:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4514 profile="/usr/sbin/cupsd"
Dec 10 01:44:42 mobile-one-linux kernel: [   60.280000] Dell Inspiron machine detected. Enabling interrupts during APM calls.
Dec 10 01:44:42 mobile-one-linux kernel: [   60.280000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 10 01:44:42 mobile-one-linux kernel: [   60.280000] apm: overridden by ACPI.
Dec 10 01:44:42 mobile-one-linux kernel: [   60.564000] ondemand governor failed to load due to too long transition latency
Dec 10 01:44:42 mobile-one-linux kernel: [   60.792000] Failure registering capabilities with primary security module.
Dec 10 01:44:42 mobile-one-linux dhcdbd: Started up.
Dec 10 01:44:43 mobile-one-linux kernel: [   61.268000] Bluetooth: Core ver 2.11
Dec 10 01:44:43 mobile-one-linux kernel: [   61.272000] NET: Registered protocol family 31
Dec 10 01:44:43 mobile-one-linux kernel: [   61.272000] Bluetooth: HCI device and connection manager initialized
Dec 10 01:44:43 mobile-one-linux kernel: [   61.272000] Bluetooth: HCI socket layer initialized
Dec 10 01:44:43 mobile-one-linux kernel: [   61.324000] Bluetooth: L2CAP ver 2.8
Dec 10 01:44:43 mobile-one-linux kernel: [   61.324000] Bluetooth: L2CAP socket layer initialized
Dec 10 01:44:43 mobile-one-linux kernel: [   61.424000] Bluetooth: RFCOMM socket layer initialized
Dec 10 01:44:43 mobile-one-linux kernel: [   61.424000] Bluetooth: RFCOMM TTY layer initialized
Dec 10 01:44:43 mobile-one-linux kernel: [   61.424000] Bluetooth: RFCOMM ver 1.8
Dec 10 01:44:45 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 10 01:44:48 mobile-one-linux kernel: [   66.688000] NET: Registered protocol family 17
Dec 10 01:44:49 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 10 01:44:49 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 10 01:44:49 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 10 01:44:49 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 10 01:44:51 mobile-one-linux kernel: [   69.696000] NET: Registered protocol family 10
Dec 10 01:44:51 mobile-one-linux kernel: [   69.696000] lo: Disabled Privacy Extensions
Dec 10 01:45:14 mobile-one-linux kernel: [   92.636000] ondemand governor failed to load due to too long transition latency
Dec 10 01:47:32 mobile-one-linux kernel: [  230.960000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 01:48:05 mobile-one-linux kernel: [  263.900000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 01:50:09 mobile-one-linux kernel: [  386.884000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 01:50:49 mobile-one-linux exiting on signal 15
Dec 10 10:46:55 mobile-one-linux syslogd 1.4.1#21ubuntu3: restart.
Dec 10 10:46:55 mobile-one-linux kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 10 10:46:55 mobile-one-linux kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec 10 10:46:55 mobile-one-linux kernel: Symbols match kernel version 2.6.22.
Dec 10 10:46:55 mobile-one-linux kernel: No module symbols loaded - kernel modules not enabled. 
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffdb000 (usable)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 000000000ffdb000 - 0000000010000000 (reserved)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] 0MB HIGHMEM available.
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] 255MB LOWMEM available.
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Zone PFN ranges:
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]   DMA             0 ->     4096
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]   Normal       4096 ->    65499
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]   HighMem     65499 ->    65499
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000]     0:        0 ->    65499
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] DMI 2.3 present.
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F4C80 checksum 0
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: RSDP 000F4C80, 0014 (r0 DELL  )
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: RSDT 0FFF0000, 0028 (r1 DELL    CPi R   27D20B07 ASL        61)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: FACP 0FFF0400, 0074 (r1 DELL    CPi R   27D20B07 ASL        61)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: DSDT 0FFF0800, 2ACA (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: FACS 0FFFF800, 0040
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efd00000)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Built 1 zonelists.  Total pages: 64988
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Kernel command line: root=UUID=35f3f868-1207-4d16-8b38-6501e6a9a93f ro quiet splash vga=791
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Initializing CPU#0
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [    0.000000] Detected 851.991 MHz processor.
Dec 10 10:46:55 mobile-one-linux kernel: [   15.983793] Console: colour dummy device 80x25
Dec 10 10:46:55 mobile-one-linux kernel: [   15.984303] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   15.984805] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011898] Memory: 248332k/261996k available (2015k kernel code, 13188k reserved, 916k data, 364k init, 0k highmem)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011924] virtual kernel memory layout:
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011927]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011931]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011934]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011937]     lowmem  : 0xc0000000 - 0xcffdb000   ( 255 MB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011941]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011944]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011948]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.011956] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.012045] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092015] Calibrating delay using timer specific routine.. 1705.24 BogoMIPS (lpj=3410495)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092078] Security Framework v1.0.0 initialized
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092097] SELinux:  Disabled at boot.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092133] Mount-cache hash table entries: 512
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092438] CPU: L1 I cache: 16K, L1 D cache: 16K
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092445] CPU: L2 cache: 256K
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092477] Compat vDSO mapped to ffffe000.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.092511] Checking 'hlt' instruction... OK.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.108220] SMP alternatives: switching to UP code
Dec 10 10:46:55 mobile-one-linux kernel: [   16.108579] Freeing SMP alternatives: 11k freed
Dec 10 10:46:55 mobile-one-linux kernel: [   16.109235] Early unpacking initramfs... done
Dec 10 10:46:55 mobile-one-linux kernel: [   16.890490] ACPI: Core revision 20070126
Dec 10 10:46:55 mobile-one-linux kernel: [   16.890711] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.893588] ACPI: setting ELCR to 0200 (from 0820)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.895693] CPU0: Intel Pentium III (Coppermine) stepping 06
Dec 10 10:46:55 mobile-one-linux kernel: [   16.895708] SMP motherboard not detected.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.895714] Local APIC not detected. Using dummy APIC emulation.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.895818] Brought up 1 CPUs
Dec 10 10:46:55 mobile-one-linux kernel: [   16.896128] Booting paravirtualized kernel on bare hardware
Dec 10 10:46:55 mobile-one-linux kernel: [   16.896271] Time: 10:45:58  Date: 11/10/107
Dec 10 10:46:55 mobile-one-linux kernel: [   16.896337] NET: Registered protocol family 16
Dec 10 10:46:55 mobile-one-linux kernel: [   16.896594] EISA bus registered
Dec 10 10:46:55 mobile-one-linux kernel: [   16.896618] ACPI: bus type pci registered
Dec 10 10:46:55 mobile-one-linux kernel: [   16.900393] PCI: PCI BIOS revision 2.10 entry at 0xfc13e, last bus=8
Dec 10 10:46:55 mobile-one-linux kernel: [   16.900399] PCI: Using configuration type 1
Dec 10 10:46:55 mobile-one-linux kernel: [   16.900405] Setting up standard PCI resources
Dec 10 10:46:55 mobile-one-linux kernel: [   16.918279] ACPI: Interpreter enabled
Dec 10 10:46:55 mobile-one-linux kernel: [   16.918289] ACPI: (supports S0 S1 S3 S4 S5)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.918329] ACPI: Using PIC for interrupt routing
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947028] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947541] PCI quirk: region 0800-083f claimed by PIIX4 ACPI
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947550] PCI quirk: region 0840-084f claimed by PIIX4 SMB
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947559] PIIX4 devres B PIO at 00e0-00e7
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947565] PIIX4 devres C PIO at 0850-085f
Dec 10 10:46:55 mobile-one-linux kernel: [   16.947975] PCI: Firmware left 0000:08:04.0 e100 interrupts enabled, disabling
Dec 10 10:46:55 mobile-one-linux kernel: [   16.994972] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.995211] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.995452] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
Dec 10 10:46:55 mobile-one-linux kernel: [   16.995687] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.995972] ACPI: Power Resource [PADA] (on)
Dec 10 10:46:55 mobile-one-linux kernel: [   16.995992] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 10 10:46:55 mobile-one-linux kernel: [   16.996020] pnp: PnP ACPI init
Dec 10 10:46:55 mobile-one-linux kernel: [   16.996046] ACPI: bus type pnp registered
Dec 10 10:46:55 mobile-one-linux kernel: [   17.062068] pnp: PnP ACPI: found 15 devices
Dec 10 10:46:55 mobile-one-linux kernel: [   17.062078] ACPI: ACPI bus type pnp unregistered
Dec 10 10:46:55 mobile-one-linux kernel: [   17.062090] PnPBIOS: Disabled by ACPI PNP
Dec 10 10:46:55 mobile-one-linux kernel: [   17.062230] PCI: Using ACPI for IRQ routing
Dec 10 10:46:55 mobile-one-linux kernel: [   17.062238] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074686] NET: Registered protocol family 8
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074692] NET: Registered protocol family 20
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074867] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074876] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074883] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074891] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074908] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074915] pnp: 00:02: ioport range 0x800-0x805 has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074922] pnp: 00:02: ioport range 0x808-0x80f has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074938] pnp: 00:03: ioport range 0x806-0x807 has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074945] pnp: 00:03: ioport range 0x850-0x853 has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074952] pnp: 00:03: ioport range 0x856-0x85f has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074959] pnp: 00:03: ioport range 0x810-0x83f has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074966] pnp: 00:03: ioport range 0x840-0x84f has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074973] pnp: 00:03: ioport range 0x600-0x67f has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074981] pnp: 00:03: ioport range 0x680-0x6ff has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.074995] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075003] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075010] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075017] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075025] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075032] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075039] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075047] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075055] pnp: 00:04: iomem range 0xed000000-0xedffffff has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075074] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
Dec 10 10:46:55 mobile-one-linux kernel: [   17.075276] Time: tsc clocksource has been installed.
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105870] PCI: Bridge: 0000:00:01.0
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105879]   IO window: e000-efff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105887]   MEM window: fd000000-feffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105895]   PREFETCH window: f4000000-f7ffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105903] PCI: Bus 9, cardbus bridge: 0000:00:03.0
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105909]   IO window: 00001000-000010ff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105917]   IO window: 00001400-000014ff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105924]   PREFETCH window: 20000000-23ffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105932]   MEM window: 24000000-27ffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105939] PCI: Bus 13, cardbus bridge: 0000:00:03.1
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105944]   IO window: 00001800-000018ff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105951]   IO window: 00001c00-00001cff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105958]   PREFETCH window: 28000000-2bffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105966]   MEM window: 2c000000-2fffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105973] PCI: Bridge: 0000:00:10.0
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105978]   IO window: d000-dfff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105986]   MEM window: fb000000-fcffffff
Dec 10 10:46:55 mobile-one-linux kernel: [   17.105993]   PREFETCH window: disabled.
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106026] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106439] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106454] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106478] PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106486] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec 10 10:46:55 mobile-one-linux kernel: [   17.106536] NET: Registered protocol family 2
Dec 10 10:46:55 mobile-one-linux kernel: [   17.143349] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.143457] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.143731] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.143932] TCP: Hash tables configured (established 8192 bind 8192)
Dec 10 10:46:55 mobile-one-linux kernel: [   17.143940] TCP reno registered
Dec 10 10:46:55 mobile-one-linux kernel: [   17.155575] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
Dec 10 10:46:55 mobile-one-linux kernel: [   17.816255]  it is
Dec 10 10:46:55 mobile-one-linux kernel: [   18.638053] Freeing initrd memory: 7057k freed
Dec 10 10:46:55 mobile-one-linux kernel: [   18.640300] audit: initializing netlink socket (disabled)
Dec 10 10:46:55 mobile-one-linux kernel: [   18.640331] audit(1197283559.568:1): initialized
Dec 10 10:46:55 mobile-one-linux kernel: [   18.645938] VFS: Disk quotas dquot_6.5.1
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646173] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646465] io scheduler noop registered
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646472] io scheduler anticipatory registered
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646478] io scheduler deadline registered
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646535] io scheduler cfq registered (default)
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646561] Limiting direct PCI/PCI transfers.
Dec 10 10:46:55 mobile-one-linux kernel: [   18.646999] isapnp: Scanning for PnP cards...
Dec 10 10:46:55 mobile-one-linux kernel: [   18.999581] isapnp: No Plug & Play device found
Dec 10 10:46:55 mobile-one-linux kernel: [   19.072564] Real Time Clock Driver v1.12ac
Dec 10 10:46:55 mobile-one-linux kernel: [   19.072777] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 10 10:46:55 mobile-one-linux kernel: [   19.072929] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 10 10:46:55 mobile-one-linux kernel: [   19.074837] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 10 10:46:55 mobile-one-linux kernel: [   19.076652] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 10 10:46:55 mobile-one-linux kernel: [   19.077196] input: Macintosh mouse button emulation as /class/input/input0
Dec 10 10:46:55 mobile-one-linux kernel: [   19.077400] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087027] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087042] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087488] mice: PS/2 mouse device common for all mice
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087771] EISA: Probing bus 0 at eisa.0
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087789] Cannot allocate resource for EISA slot 1
Dec 10 10:46:55 mobile-one-linux kernel: [   19.087818] EISA: Detected 0 cards.
Dec 10 10:46:55 mobile-one-linux kernel: [   19.088048] TCP cubic registered
Dec 10 10:46:55 mobile-one-linux kernel: [   19.088086] NET: Registered protocol family 1
Dec 10 10:46:55 mobile-one-linux kernel: [   19.088149] Using IPI No-Shortcut mode
Dec 10 10:46:55 mobile-one-linux kernel: [   19.088522]   Magic number: 3:84:780
Dec 10 10:46:55 mobile-one-linux kernel: [   19.088675]   hash matches device ptyq2
Dec 10 10:46:55 mobile-one-linux kernel: [   19.090016] Freeing unused kernel memory: 364k freed
Dec 10 10:46:55 mobile-one-linux kernel: [   19.117746] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 10 10:46:55 mobile-one-linux kernel: [   20.649932] AppArmor: AppArmor initialized<5>audit(1197283561.568:2):  type=1505 info="AppArmor initialized" pid=1187
Dec 10 10:46:55 mobile-one-linux kernel: [   20.667021] fuse init (API version 7.8)
Dec 10 10:46:55 mobile-one-linux kernel: [   20.683219] Failure registering capabilities with primary security module.
Dec 10 10:46:55 mobile-one-linux kernel: [   20.718771] ACPI: CPU0 (power states: C1[C1] C2[C2])
Dec 10 10:46:55 mobile-one-linux kernel: [   20.745092] ACPI: Thermal Zone [THM] (32 C)
Dec 10 10:46:55 mobile-one-linux kernel: [   22.280155] SCSI subsystem initialized
Dec 10 10:46:55 mobile-one-linux kernel: [   22.317159] scsi0 : ata_piix
Dec 10 10:46:55 mobile-one-linux kernel: [   22.317260] scsi1 : ata_piix
Dec 10 10:46:55 mobile-one-linux kernel: [   22.319022] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00010860 irq 14
Dec 10 10:46:55 mobile-one-linux kernel: [   22.319032] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00010868 irq 15
Dec 10 10:46:55 mobile-one-linux kernel: [   22.429732] usbcore: registered new interface driver usbfs
Dec 10 10:46:55 mobile-one-linux kernel: [   22.429806] usbcore: registered new interface driver hub
Dec 10 10:46:55 mobile-one-linux kernel: [   22.429867] usbcore: registered new device driver usb
Dec 10 10:46:55 mobile-one-linux kernel: [   22.433467] USB Universal Host Controller Interface driver v3.0
Dec 10 10:46:55 mobile-one-linux kernel: [   22.483307] ata1.00: ATA-5: HITACHI_DK23EA-60, 00K2A0A3, max UDMA/100
Dec 10 10:46:55 mobile-one-linux kernel: [   22.483319] ata1.00: 117210240 sectors, multi 8: LBA 
Dec 10 10:46:55 mobile-one-linux kernel: [   22.491291] ata1.00: configured for UDMA/33
Dec 10 10:46:55 mobile-one-linux kernel: [   22.509760] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Dec 10 10:46:55 mobile-one-linux kernel: [   22.509769] e100: Copyright(c) 1999-2006 Intel Corporation
Dec 10 10:46:55 mobile-one-linux kernel: [   22.802276] Floppy drive(s): fd0 is 1.44M
Dec 10 10:46:55 mobile-one-linux kernel: [   22.810907] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324S, U303, max UDMA/33
Dec 10 10:46:55 mobile-one-linux kernel: [   22.887571] FDC 0 is a post-1991 82077
Dec 10 10:46:55 mobile-one-linux kernel: [    6.964000] Marking TSC unstable due to: possible TSC halt in C2.
Dec 10 10:46:55 mobile-one-linux kernel: [    6.968000] Time: acpi_pm clocksource has been installed.
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] ata2.00: configured for UDMA/33
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23EA-6 00K2 PQ: 0 ANSI: 5
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324S U303 PQ: 0 ANSI: 5
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] uhci_hcd 0000:00:07.2: UHCI Host Controller
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Dec 10 10:46:55 mobile-one-linux kernel: [    6.980000] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000cce0
Dec 10 10:46:55 mobile-one-linux kernel: [    6.984000] usb usb1: configuration #1 chosen from 1 choice
Dec 10 10:46:55 mobile-one-linux kernel: [    6.984000] hub 1-0:1.0: USB hub found
Dec 10 10:46:55 mobile-one-linux kernel: [    6.984000] hub 1-0:1.0: 2 ports detected
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 10 10:46:55 mobile-one-linux kernel: [    7.028000]  sda: sda1 sda2 sda3
Dec 10 10:46:55 mobile-one-linux kernel: [    7.080000] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 10 10:46:55 mobile-one-linux kernel: [    7.088000] ACPI: PCI Interrupt 0000:08:04.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec 10 10:46:55 mobile-one-linux kernel: [    7.096000] Clocksource tsc unstable (delta = -143984735 ns)
Dec 10 10:46:55 mobile-one-linux kernel: [    7.108000] e100: eth0: e100_probe: addr 0xfbfff000, irq 11, MAC addr 00:20:E0:66:54:55
Dec 10 10:46:55 mobile-one-linux kernel: [    7.116000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 10 10:46:55 mobile-one-linux kernel: [    7.116000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Dec 10 10:46:55 mobile-one-linux kernel: [    7.136000] sr0: scsi3-mmc drive: 5x/24x writer cd/rw xa/form2 cdda tray
Dec 10 10:46:55 mobile-one-linux kernel: [    7.136000] Uniform CD-ROM driver Revision: 3.20
Dec 10 10:46:55 mobile-one-linux kernel: [    7.620000] Attempting manual resume
Dec 10 10:46:55 mobile-one-linux kernel: [    7.692000] kjournald starting.  Commit interval 5 seconds
Dec 10 10:46:55 mobile-one-linux kernel: [    7.692000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 10 10:46:55 mobile-one-linux kernel: [   21.012000] Yenta: CardBus bridge found at 0000:00:03.0 [1028:00b0]
Dec 10 10:46:55 mobile-one-linux kernel: [   21.012000] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 10 10:46:55 mobile-one-linux kernel: [   21.012000] Yenta: Routing CardBus interrupts to PCI
Dec 10 10:46:55 mobile-one-linux kernel: [   21.012000] Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x64
Dec 10 10:46:55 mobile-one-linux kernel: [   21.032000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Socket status: 30000006
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Yenta: CardBus bridge found at 0000:00:03.1 [1028:00b0]
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Yenta: Routing CardBus interrupts to PCI
Dec 10 10:46:56 mobile-one-linux kernel: [   21.244000] Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x64
Dec 10 10:46:56 mobile-one-linux kernel: [   21.476000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Dec 10 10:46:56 mobile-one-linux kernel: [   21.476000] Socket status: 30000006
Dec 10 10:46:56 mobile-one-linux kernel: [   21.492000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 10 10:46:56 mobile-one-linux kernel: [   21.492000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
Dec 10 10:46:56 mobile-one-linux kernel: [   22.052000] Linux agpgart interface v0.102 (c) Dave Jones
Dec 10 10:46:56 mobile-one-linux kernel: [   22.084000] agpgart: Detected an Intel 440BX Chipset.
Dec 10 10:46:56 mobile-one-linux kernel: [   22.088000] agpgart: AGP aperture is 64M @ 0xf0000000
Dec 10 10:46:56 mobile-one-linux kernel: [   23.452000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
Dec 10 10:46:56 mobile-one-linux kernel: [   23.668000] input: PC Speaker as /class/input/input3
Dec 10 10:46:56 mobile-one-linux kernel: [   23.840000] parport_pc 00:0e: reported by Plug and Play ACPI
Dec 10 10:46:56 mobile-one-linux kernel: [   23.840000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Dec 10 10:46:56 mobile-one-linux kernel: [   24.324000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Dec 10 10:46:56 mobile-one-linux kernel: [   24.324000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0x3e0-0x4ff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0x820-0x8ff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0xa00-0xaff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.576000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
Dec 10 10:46:56 mobile-one-linux kernel: [   24.580000] cs: IO port probe 0x3e0-0x4ff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.580000] cs: IO port probe 0x820-0x8ff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.580000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   24.580000] cs: IO port probe 0xa00-0xaff: clean.
Dec 10 10:46:56 mobile-one-linux kernel: [   25.436000] lp0: using parport0 (interrupt-driven).
Dec 10 10:46:56 mobile-one-linux kernel: [   25.540000] Adding 3478064k swap on /dev/sda3.  Priority:-1 extents:1 across:3478064k
Dec 10 10:46:56 mobile-one-linux kernel: [   26.028000] EXT3 FS on sda2, internal journal
Dec 10 10:46:56 mobile-one-linux kernel: [   53.548000] ACPI: ACPI Dock Station Driver 
Dec 10 10:46:56 mobile-one-linux kernel: [   53.596000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Dec 10 10:46:56 mobile-one-linux kernel: [   53.708000] input: Lid Switch as /class/input/input4
Dec 10 10:46:56 mobile-one-linux kernel: [   53.708000] ACPI: Lid Switch [LID]
Dec 10 10:46:56 mobile-one-linux kernel: [   53.740000] input: Power Button (CM) as /class/input/input5
Dec 10 10:46:56 mobile-one-linux kernel: [   53.740000] ACPI: Power Button (CM) [PBTN]
Dec 10 10:46:56 mobile-one-linux kernel: [   53.756000] input: Sleep Button (CM) as /class/input/input6
Dec 10 10:46:56 mobile-one-linux kernel: [   53.756000] ACPI: Sleep Button (CM) [SBTN]
Dec 10 10:46:56 mobile-one-linux kernel: [   54.048000] ACPI: AC Adapter [AC] (on-line)
Dec 10 10:46:56 mobile-one-linux kernel: [   54.656000] ACPI: Battery Slot [BAT0] (battery present)
Dec 10 10:46:56 mobile-one-linux kernel: [   54.656000] ACPI: Battery Slot [BAT1] (battery absent)
Dec 10 10:46:57 mobile-one-linux kernel: [   59.880000] ppdev: user-space parallel port driver
Dec 10 10:46:57 mobile-one-linux kernel: [   59.908000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Dec 10 10:46:58 mobile-one-linux kernel: [   60.876000] audit(1197254818.251:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4515 profile="/usr/sbin/cupsd"
Dec 10 10:46:58 mobile-one-linux kernel: [   60.964000] Dell Inspiron machine detected. Enabling interrupts during APM calls.
Dec 10 10:46:58 mobile-one-linux kernel: [   60.964000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 10 10:46:58 mobile-one-linux kernel: [   60.964000] apm: overridden by ACPI.
Dec 10 10:46:59 mobile-one-linux kernel: [   61.244000] ondemand governor failed to load due to too long transition latency
Dec 10 10:46:59 mobile-one-linux kernel: [   61.476000] Failure registering capabilities with primary security module.
Dec 10 10:46:59 mobile-one-linux dhcdbd: Started up.
Dec 10 10:46:59 mobile-one-linux kernel: [   62.024000] Bluetooth: Core ver 2.11
Dec 10 10:46:59 mobile-one-linux kernel: [   62.024000] NET: Registered protocol family 31
Dec 10 10:46:59 mobile-one-linux kernel: [   62.024000] Bluetooth: HCI device and connection manager initialized
Dec 10 10:46:59 mobile-one-linux kernel: [   62.024000] Bluetooth: HCI socket layer initialized
Dec 10 10:46:59 mobile-one-linux kernel: [   62.092000] Bluetooth: L2CAP ver 2.8
Dec 10 10:46:59 mobile-one-linux kernel: [   62.092000] Bluetooth: L2CAP socket layer initialized
Dec 10 10:47:00 mobile-one-linux kernel: [   62.440000] Bluetooth: RFCOMM socket layer initialized
Dec 10 10:47:00 mobile-one-linux kernel: [   62.440000] Bluetooth: RFCOMM TTY layer initialized
Dec 10 10:47:00 mobile-one-linux kernel: [   62.440000] Bluetooth: RFCOMM ver 1.8
Dec 10 10:47:01 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 10 10:47:04 mobile-one-linux kernel: [   66.416000] NET: Registered protocol family 17
Dec 10 10:47:06 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 10 10:47:06 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 10 10:47:06 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 10 10:47:06 mobile-one-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 10 10:47:08 mobile-one-linux kernel: [   70.284000] NET: Registered protocol family 10
Dec 10 10:47:08 mobile-one-linux kernel: [   70.284000] lo: Disabled Privacy Extensions
Dec 10 10:47:32 mobile-one-linux kernel: [   94.648000] ondemand governor failed to load due to too long transition latency
Dec 10 10:49:36 mobile-one-linux kernel: [  218.724000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 10:58:52 mobile-one-linux kernel: [  774.848000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 10:59:26 mobile-one-linux kernel: [  808.952000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec 10 11:01:57 mobile-one-linux kernel: [  960.052000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 11:21:25 mobile-one-linux kernel: [ 2126.932000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 11:22:03 mobile-one-linux kernel: [ 2166.012000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 11:27:02 mobile-one-linux kernel: [ 2464.268000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 11:30:41 mobile-one-linux kernel: [ 2683.596000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 11:34:04 mobile-one-linux kernel: [ 2886.064000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 11:34:29 mobile-one-linux kernel: [ 2911.876000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 11:34:42 mobile-one-linux kernel: [ 2924.368000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec 10 11:35:03 mobile-one-linux kernel: [ 2945.320000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec 10 11:46:56 mobile-one-linux -- MARK --
Dec 10 12:06:59 mobile-one-linux -- MARK --
Dec 10 12:26:59 mobile-one-linux -- MARK --
Dec 10 12:47:00 mobile-one-linux -- MARK --
Dec 10 13:07:00 mobile-one-linux -- MARK --
Dec 10 13:27:00 mobile-one-linux -- MARK --
Dec 10 13:47:00 mobile-one-linux -- MARK --
Dec 10 14:07:00 mobile-one-linux -- MARK --
Dec 10 14:27:00 mobile-one-linux -- MARK --
Dec 10 14:47:00 mobile-one-linux -- MARK --
Dec 10 15:07:00 mobile-one-linux -- MARK --
Dec 10 15:27:00 mobile-one-linux -- MARK --
Dec 10 15:38:32 mobile-one-linux kernel: [17554.488000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 15:50:59 mobile-one-linux kernel: [18301.368000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec 10 16:03:48 mobile-one-linux kernel: [19070.136000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Dec 10 16:05:47 mobile-one-linux kernel: [19188.828000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec 10 16:22:22 mobile-one-linux kernel: [20184.348000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.


Is it the "lo: Disabled Privacy Extensions"  Which is the problem?

---

