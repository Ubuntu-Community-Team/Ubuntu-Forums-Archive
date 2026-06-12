---
title: "KUBUNTU 7.04 startup Problem"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by armaud on 2007-05-11
I have installed Kununtu 7.04 and it is my first experience with Linux. I don't know why but booting takes nearly 5 minutes and the kubuntu startup screen does not appear. As soon as i select kubuntu from grub loader, my screen goes blank and after 5 minutes, the login appears. after this Kubuntu runs fine. My system is P4 2.4, 512MB ram and harddisk i am using for kubuntu has 5.1GB space.

---

### Post by ghostboy on 2007-05-11
> **armaud said:**
> I have installed Kununtu 7.04 and it is my first experience with Linux. I don't know why but booting takes nearly 5 minutes and the kubuntu startup screen does not appear. As soon as i select kubuntu from grub loader, my screen goes blank and after 5 minutes, the login appears. after this Kubuntu runs fine. My system is P4 2.4, 512MB ram and harddisk i am using for kubuntu has 5.1GB space.

It sounds like maybe part of your installation is corrupted.  Did you use the LiveCD to install?  Or did you do an install from the Internet?  If you used a LiveCD, boot to the CD and perform an installation repair.  Hope this helps.

---

### Post by armaud on 2007-05-13
I installed it again but the problem still persists. I even tried installing Ubuntu 7.04 but the same problem appears in it. I forgot to mention that i installed with a live cd and booting with live cd has the same problem although i thought it was due to booting from the cd.

---

### Post by mejy on 2007-05-13
Try running 'sudo gedit /boot/grub/menu.lst' and adding ' vga=791' to the line that begins 'defoptions'.  The fact that it takes to long makes it seem very likey that a network connection is timing out.  Do you have a wireless card?

---

### Post by armaud on 2007-05-14
I will definitely try your tip. I was trying to install it on my personal home pc and it does not connect to any network. The vga card on my pc is nothing special and works perfectly on kubuntu 6.06. What worries me is the booting time as 5min are simply unbearable.

---

### Post by wolf354 on 2007-05-21
Hello,
wit me it was happning the same...
After a week of wandering, formating, etc... I went into Boot Up Manager and found that start up and power off scripts where disabled.
After enabling this option it took some time for the PC tp turn off but afterwards everything became fine.

Best regards

---

### Post by armaud on 2007-05-25
Thanks
      I am preparing for exams right now and i havent got the Kubuntu 7.04 cd. As soon as i finish with my exams i will get the cd from a friend and try your tip.

---

### Post by armaud on 2007-05-28
Can you please tell me how to go to the boot manager and enable the scripts. I really have no idea how to modify the settings. Please keep in mind that i have been using linux only for a month now.

---

### Post by armaud on 2007-05-29
Hello
   I tries adding the vga=791 line but it does not help. I could not get hold of the Kubuntu 7.04 cd so i installed ubuntu 7.04 cd. It is having exactly the same problem. The time for shutting the computer is about 10 to 20 seconds so it is ok. The boot time and the blank screen are dissappointing for me though.

---

### Post by armaud on 2007-05-29
Hello
     I just went to my system log after my computer booted. Although i am no expert but it did seem to me that the ubuntu os kept restarting behind the scenes. The system log is 101 pages long in microsoft office. I copied the system log right after computer boot. Please see if you can find the problem.
I am dividing it so that i can post it


May 28 15:37:35 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 28 15:37:37 maud-desktop gconfd (root-6494): starting (version 2.18.0.1), pid 6494 user 'root' 
May 28 15:37:37 maud-desktop gconfd (root-6494): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 15:37:37 maud-desktop gconfd (root-6494): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 28 15:37:37 maud-desktop gconfd (root-6494): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 15:37:37 maud-desktop gconfd (root-6494): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 15:37:37 maud-desktop gconfd (root-6494): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 15:39:07 maud-desktop gconfd (root-6494): GConf server is not in use, shutting down. 
May 28 15:39:07 maud-desktop gconfd (root-6494): Exiting 
May 28 15:40:46 maud-desktop gconfd (root-6707): starting (version 2.18.0.1), pid 6707 user 'root' 
May 28 15:40:46 maud-desktop gconfd (root-6707): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 15:40:46 maud-desktop gconfd (root-6707): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 28 15:40:46 maud-desktop gconfd (root-6707): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 15:40:46 maud-desktop gconfd (root-6707): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 15:40:46 maud-desktop gconfd (root-6707): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 15:40:46 maud-desktop kernel: [  991.019034] NTFS driver 2.1.28 [Flags: R/O MODULE]. 
May 28 15:40:47 maud-desktop kernel: [  991.071979] NTFS volume version 3.1. 
May 28 15:41:16 maud-desktop gconfd (root-6707): GConf server is not in use, shutting down. 
May 28 15:41:16 maud-desktop gconfd (root-6707): Exiting 
May 28 15:41:33 maud-desktop gconfd (armaud-5459): Exiting 
May 28 15:41:33 maud-desktop gconfd (armaud-6825): starting (version 2.18.0.1), pid 6825 user 'armaud' 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): starting (version 2.18.0.1), pid 6827 user 'armaud' 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 15:41:33 maud-desktop gconfd (armaud-6827): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 15:41:33 maud-desktop gconfd (armaud-6825): Failed to get lock for daemon, exiting: Failed to lock '/tmp/gconfd-armaud/lock/ior': probably another process has the lock, or your operating system has NFS file locking misconfigured (Resource temporarily unavailable) 
May 28 15:41:44 maud-desktop exiting on signal 15 
May 28 18:50:45 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 28 18:50:45 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 28 18:50:45 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 28 18:50:45 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 28 18:50:45 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.  
May 28 18:50:45 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 28 18:50:45 maud-desktop kernel: [    0.000000] sanitize start 
May 28 18:50:45 maud-desktop kernel: [    0.000000] sanitize end 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 28 18:50:45 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 28 18:50:45 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 28 18:50:45 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 28 18:50:45 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 28 18:50:45 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 28 18:50:45 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 28 18:50:45 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 28 18:50:45 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 28 18:50:45 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 28 18:50:45 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 28 18:50:45 maud-desktop kernel: [    0.000000] Detected 2400.210 MHz processor. 
May 28 18:50:45 maud-desktop kernel: [   14.275601] Built 1 zonelists.  Total pages: 129604 
May 28 18:50:45 maud-desktop kernel: [   14.275607] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 28 18:50:45 maud-desktop kernel: [   14.275809] Enabling fast FPU save and restore... done. 
May 28 18:50:45 maud-desktop kernel: [   14.275812] Enabling unmasked SIMD FPU exception support... done. 
May 28 18:50:45 maud-desktop kernel: [   14.275827] Initializing CPU#0 
May 28 18:50:45 maud-desktop kernel: [   14.275921] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.277361] Console: colour VGA+ 80x25 
May 28 18:50:45 maud-desktop kernel: [   14.277779] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.278124] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.288393] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 28 18:50:45 maud-desktop kernel: [   14.288405] virtual kernel memory layout: 
May 28 18:50:45 maud-desktop kernel: [   14.288406]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 28 18:50:45 maud-desktop kernel: [   14.288408]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 28 18:50:45 maud-desktop kernel: [   14.288409]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 28 18:50:45 maud-desktop kernel: [   14.288410]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 28 18:50:45 maud-desktop kernel: [   14.288411]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 28 18:50:45 maud-desktop kernel: [   14.288413]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 28 18:50:45 maud-desktop kernel: [   14.288414]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 28 18:50:45 maud-desktop kernel: [   14.288418] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 28 18:50:45 maud-desktop kernel: [   14.367785] Calibrating delay using timer specific routine.. 4804.13 BogoMIPS (lpj=9608268) 
May 28 18:50:45 maud-desktop kernel: [   14.367838] Security Framework v1.0.0 initialized 
May 28 18:50:45 maud-desktop kernel: [   14.367843] SELinux:  Disabled at boot. 
May 28 18:50:45 maud-desktop kernel: [   14.367862] Mount-cache hash table entries: 512 
May 28 18:50:45 maud-desktop kernel: [   14.368027] monitor/mwait feature present. 
May 28 18:50:45 maud-desktop kernel: [   14.368029] using mwait in idle threads. 
May 28 18:50:45 maud-desktop kernel: [   14.368037] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 28 18:50:45 maud-desktop kernel: [   14.368041] CPU: L2 cache: 1024K 
May 28 18:50:45 maud-desktop kernel: [   14.368044] CPU: Hyper-Threading is disabled 
May 28 18:50:45 maud-desktop kernel: [   14.368059] Compat vDSO mapped to ffffe000. 
May 28 18:50:45 maud-desktop kernel: [   14.368063] Remapping vsyscall page to ffffe000 
May 28 18:50:45 maud-desktop kernel: [   14.368082] Checking 'hlt' instruction... OK. 
May 28 18:50:45 maud-desktop kernel: [   14.383864] SMP alternatives: switching to UP code 
May 28 18:50:45 maud-desktop kernel: [   14.384037] Freeing SMP alternatives: 11k freed 
May 28 18:50:45 maud-desktop kernel: [   14.384265] Early unpacking initramfs... done 
May 28 18:50:45 maud-desktop kernel: [   14.734361] ACPI: Core revision 20060707 
May 28 18:50:45 maud-desktop kernel: [   14.734534] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 28 18:50:45 maud-desktop kernel: [   14.737120] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 28 18:50:45 maud-desktop kernel: [   14.737167] Total of 1 processors activated (4804.13 BogoMIPS). 
May 28 18:50:45 maud-desktop kernel: [   14.737303] ENABLING IO-APIC IRQs 
May 28 18:50:45 maud-desktop kernel: [   14.737495] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 28 18:50:45 maud-desktop kernel: [   14.883038] Brought up 1 CPUs 
May 28 18:50:45 maud-desktop kernel: [   14.883318] Booting paravirtualized kernel on bare hardware 
May 28 18:50:45 maud-desktop kernel: [   14.883397] Time: 18:47:56  Date: 04/28/107 
May 28 18:50:45 maud-desktop kernel: [   14.883430] NET: Registered protocol family 16 
May 28 18:50:45 maud-desktop kernel: [   14.883534] EISA bus registered 
May 28 18:50:45 maud-desktop kernel: [   14.883540] ACPI: bus type pci registered 
May 28 18:50:45 maud-desktop kernel: [   14.883613] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 28 18:50:45 maud-desktop kernel: [   14.883617] PCI: Using configuration type 1 
May 28 18:50:45 maud-desktop kernel: [   14.883619] Setting up standard PCI resources 
May 28 18:50:45 maud-desktop kernel: [   14.897898] ACPI: Interpreter enabled 
May 28 18:50:45 maud-desktop kernel: [   14.897902] ACPI: Using IOAPIC for interrupt routing 
May 28 18:50:45 maud-desktop kernel: [   14.898306] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 28 18:50:45 maud-desktop kernel: [   14.898939] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 28 18:50:45 maud-desktop kernel: [   14.898941] * this clock source is slow. If you are sure your timer does not have 
May 28 18:50:45 maud-desktop kernel: [   14.898943] * this bug, please use "acpi_pm_good" to disable the workaround 
May 28 18:50:45 maud-desktop kernel: [   14.899003] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 28 18:50:45 maud-desktop kernel: [   14.899007] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 28 18:50:45 maud-desktop kernel: [   14.899250] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 28 18:50:45 maud-desktop kernel: [   14.899327] PCI: Transparent bridge - 0000:00:1e.0 
May 28 18:50:45 maud-desktop kernel: [   14.903333] ACPI: Power Resource [URP1] (off) 
May 28 18:50:45 maud-desktop kernel: [   14.903415] ACPI: Power Resource [FDDP] (off) 
May 28 18:50:45 maud-desktop kernel: [   14.903500] ACPI: Power Resource [LPTP] (off) 
May 28 18:50:45 maud-desktop kernel: [   14.906431] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.906860] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.907319] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.907740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.908159] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.908575] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 18:50:45 maud-desktop kernel: [   14.908991] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 18:50:45 maud-desktop kernel: [   14.909413] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 28 18:50:45 maud-desktop kernel: [   14.909821] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 28 18:50:45 maud-desktop kernel: [   14.909838] pnp: PnP ACPI init 
May 28 18:50:45 maud-desktop kernel: [   14.914352] pnp: PnP ACPI: found 13 devices 
May 28 18:50:45 maud-desktop kernel: [   14.914359] PnPBIOS: Disabled by ACPI PNP 
May 28 18:50:45 maud-desktop kernel: [   14.914415] PCI: Using ACPI for IRQ routing 
May 28 18:50:45 maud-desktop kernel: [   14.914419] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 28 18:50:45 maud-desktop kernel: [   14.917326] NET: Registered protocol family 8 
May 28 18:50:45 maud-desktop kernel: [   14.917329] NET: Registered protocol family 20 
May 28 18:50:45 maud-desktop kernel: [   14.918641] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 28 18:50:45 maud-desktop kernel: [   14.918645] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 28 18:50:45 maud-desktop kernel: [   14.918649] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 28 18:50:45 maud-desktop kernel: [   14.919039] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 28 18:50:45 maud-desktop kernel: [   14.919050] PCI: Bridge: 0000:00:1e.0 
May 28 18:50:45 maud-desktop kernel: [   14.919054]   IO window: d000-dfff 
May 28 18:50:45 maud-desktop kernel: [   14.919060]   MEM window: ff800000-ff8fffff 
May 28 18:50:45 maud-desktop kernel: [   14.919065]   PREFETCH window: eaa00000-eaafffff 
May 28 18:50:45 maud-desktop kernel: [   14.919109] NET: Registered protocol family 2 
May 28 18:50:45 maud-desktop kernel: [   14.958960] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.959053] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.959162] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 28 18:50:45 maud-desktop kernel: [   14.959214] TCP: Hash tables configured (established 16384 bind 8192) 
May 28 18:50:45 maud-desktop kernel: [   14.959217] TCP reno registered 
May 28 18:50:45 maud-desktop kernel: [   14.971000] checking if image is initramfs... it is 
May 28 18:50:45 maud-desktop kernel: [   15.658658] Freeing initrd memory: 7005k freed 
May 28 18:50:45 maud-desktop kernel: [   15.659281] audit: initializing netlink socket (disabled) 
May 28 18:50:45 maud-desktop kernel: [   15.659301] audit(1180378077.464:1): initialized 
May 28 18:50:45 maud-desktop kernel: [   15.659449] VFS: Disk quotas dquot_6.5.1 
May 28 18:50:45 maud-desktop kernel: [   15.659474] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 28 18:50:45 maud-desktop kernel: [   15.659536] io scheduler noop registered 
May 28 18:50:45 maud-desktop kernel: [   15.659539] io scheduler anticipatory registered 
May 28 18:50:45 maud-desktop kernel: [   15.659542] io scheduler deadline registered 
May 28 18:50:45 maud-desktop kernel: [   15.659553] io scheduler cfq registered (default) 
May 28 18:50:45 maud-desktop kernel: [   15.659847] isapnp: Scanning for PnP cards... 
May 28 18:50:45 maud-desktop kernel: [   16.011397] isapnp: No Plug & Play device found 
May 28 18:50:45 maud-desktop kernel: [   16.041878] Real Time Clock Driver v1.12ac 
May 28 18:50:45 maud-desktop kernel: [   16.041944] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 28 18:50:45 maud-desktop kernel: [   16.042070] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 18:50:45 maud-desktop kernel: [   16.042869] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 18:50:45 maud-desktop kernel: [   16.043162] mice: PS/2 mouse device common for all mice 
May 28 18:50:45 maud-desktop kernel: [   16.043876] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 28 18:50:45 maud-desktop kernel: [   16.044168] input: Macintosh mouse button emulation as /class/input/input0 
May 28 18:50:45 maud-desktop kernel: [   16.044218] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 28 18:50:45 maud-desktop kernel: [   16.044223] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 28 18:50:45 maud-desktop kernel: [   16.044486] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 28 18:50:45 maud-desktop kernel: [   16.048102] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 28 18:50:45 maud-desktop kernel: [   16.048110] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 28 18:50:45 maud-desktop kernel: [   16.048280] EISA: Probing bus 0 at eisa.0 
May 28 18:50:45 maud-desktop kernel: [   16.048321] EISA: Detected 0 cards. 
May 28 18:50:45 maud-desktop kernel: [   16.078371] TCP cubic registered 
May 28 18:50:45 maud-desktop kernel: [   16.078380] NET: Registered protocol family 1 
May 28 18:50:45 maud-desktop kernel: [   16.078405] Using IPI No-Shortcut mode 
May 28 18:50:45 maud-desktop kernel: [   16.078480] ACPI: (supports S0 S1 S4 S5) 
May 28 18:50:45 maud-desktop kernel: [   16.078528]   Magic number: 7:244:798 
May 28 18:50:45 maud-desktop kernel: [   16.078672]   hash matches device ptyr6 
May 28 18:50:45 maud-desktop kernel: [   16.079029] Freeing unused kernel memory: 328k freed 
May 28 18:50:45 maud-desktop kernel: [   16.081148] Time: tsc clocksource has been installed. 
May 28 18:50:45 maud-desktop kernel: [   16.097218] input: AT Translated Set 2 keyboard as /class/input/input1 
May 28 18:50:45 maud-desktop kernel: [   17.423097] Capability LSM initialized 
May 28 18:50:45 maud-desktop kernel: [   17.766273] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 28 18:50:45 maud-desktop kernel: [   17.766285] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 28 18:50:45 maud-desktop kernel: [   27.226212] usbcore: registered new interface driver usbfs 
May 28 18:50:45 maud-desktop kernel: [   27.226242] usbcore: registered new interface driver hub 
May 28 18:50:45 maud-desktop kernel: [   27.226272] usbcore: registered new device driver usb 
May 28 18:50:45 maud-desktop kernel: [   27.227431] USB Universal Host Controller Interface driver v3.0 
May 28 18:50:45 maud-desktop kernel: [   27.227492] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 28 18:50:45 maud-desktop kernel: [   27.227512] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 28 18:50:45 maud-desktop kernel: [   27.227721] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 28 18:50:45 maud-desktop kernel: [   27.227750] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 28 18:50:45 maud-desktop kernel: [   27.227876] usb usb1: configuration #1 chosen from 1 choice 
May 28 18:50:45 maud-desktop kernel: [   27.227908] hub 1-0:1.0: USB hub found 
May 28 18:50:45 maud-desktop kernel: [   27.227915] hub 1-0:1.0: 2 ports detected 
May 28 18:50:45 maud-desktop kernel: [   27.268288] SCSI subsystem initialized 
May 28 18:50:45 maud-desktop kernel: [   27.331570] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 28 18:50:45 maud-desktop kernel: [   27.331590] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 28 18:50:45 maud-desktop kernel: [   27.331617] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 28 18:50:45 maud-desktop kernel: [   27.331647] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 28 18:50:45 maud-desktop kernel: [   27.331747] usb usb2: configuration #1 chosen from 1 choice 
May 28 18:50:45 maud-desktop kernel: [   27.331785] hub 2-0:1.0: USB hub found 
May 28 18:50:45 maud-desktop kernel: [   27.331794] hub 2-0:1.0: 2 ports detected 
May 28 18:50:45 maud-desktop kernel: [   27.415547] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 28 18:50:45 maud-desktop kernel: [   27.415552] e100: Copyright(c) 1999-2006 Intel Corporation 
May 28 18:50:45 maud-desktop kernel: [   27.435372] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 28 18:50:45 maud-desktop kernel: [   27.435392] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 28 18:50:45 maud-desktop kernel: [   27.435420] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 28 18:50:45 maud-desktop kernel: [   27.435450] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 28 18:50:45 maud-desktop kernel: [   27.435553] usb usb3: configuration #1 chosen from 1 choice 
May 28 18:50:45 maud-desktop kernel: [   27.435585] hub 3-0:1.0: USB hub found 
May 28 18:50:45 maud-desktop kernel: [   27.435594] hub 3-0:1.0: 2 ports detected 
May 28 18:50:45 maud-desktop kernel: [   27.542282] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 28 18:50:45 maud-desktop kernel: [   27.542289] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 28 18:50:45 maud-desktop kernel: [   27.542370] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 28 18:50:45 maud-desktop kernel: [   27.542408] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 28 18:50:45 maud-desktop kernel: [   27.542432] scsi0 : ata_piix 
May 28 18:50:45 maud-desktop kernel: [   27.715133] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 18:50:45 maud-desktop kernel: [   27.715139] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 28 18:50:45 maud-desktop kernel: [   27.715143] ata1.00: 78165360 sectors, multi 16: LBA  
May 28 18:50:45 maud-desktop kernel: [   27.715147] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 28 18:50:45 maud-desktop kernel: [   27.715151] ata1.01: 10018890 sectors, multi 16: LBA  
May 28 18:50:45 maud-desktop kernel: [   27.715158] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 28 18:50:45 maud-desktop kernel: [   27.727159] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 18:50:45 maud-desktop kernel: [   27.727165] ata1.00: configured for UDMA/33 
May 28 18:50:45 maud-desktop kernel: [   27.738986] ata1.01: configured for UDMA/33 
May 28 18:50:45 maud-desktop kernel: [   27.739004] scsi1 : ata_piix 
May 28 18:50:45 maud-desktop kernel: [   28.058479] ata2.00: ATAPI, max UDMA/33 
May 28 18:50:45 maud-desktop kernel: [   28.222210] ata2.00: configured for UDMA/33 
May 28 18:50:45 maud-desktop kernel: [   28.226009] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5 
May 28 18:50:45 maud-desktop kernel: [   28.230001] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 28 18:50:45 maud-desktop kernel: [   28.230935] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 28 18:50:45 maud-desktop kernel: [   28.232510] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 19 
May 28 18:50:45 maud-desktop kernel: [   28.252180] e100: eth0: e100_probe: addr 0xff8ff000, irq 19, MAC addr 00:11:11:56:8B:A4 
May 28 18:50:45 maud-desktop kernel: [   28.252268] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20 
May 28 18:50:45 maud-desktop kernel: [   28.252284] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 28 18:50:45 maud-desktop kernel: [   28.252318] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 28 18:50:45 maud-desktop kernel: [   28.252358] ehci_hcd 0000:00:1d.7: debug port 1 
May 28 18:50:45 maud-desktop kernel: [   28.252377] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa7fc00 
May 28 18:50:45 maud-desktop kernel: [   28.256266] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 28 18:50:45 maud-desktop kernel: [   28.256362] usb usb4: configuration #1 chosen from 1 choice 
May 28 18:50:45 maud-desktop kernel: [   28.256396] hub 4-0:1.0: USB hub found 
May 28 18:50:45 maud-desktop kernel: [   28.256405] hub 4-0:1.0: 6 ports detected 
May 28 18:50:45 maud-desktop kernel: [   28.553503] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 18:50:45 maud-desktop kernel: [   28.553963] sda: Write Protect is off 
May 28 18:50:45 maud-desktop kernel: [   28.557942] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 18:50:45 maud-desktop kernel: [   28.561931] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 18:50:45 maud-desktop kernel: [   28.565452] sda: Write Protect is off 
May 28 18:50:45 maud-desktop kernel: [   28.569464] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 18:50:45 maud-desktop kernel: [   28.569468]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 28 18:50:45 maud-desktop kernel: [   28.646543] sd 0:0:0:0: Attached scsi disk sda 
May 28 18:50:45 maud-desktop kernel: [   28.649797] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 28 18:50:45 maud-desktop kernel: [   28.653316] sdb: Write Protect is off 
May 28 18:50:45 maud-desktop kernel: [   28.653342] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 18:50:45 maud-desktop kernel: [   28.653388] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB)

---

### Post by armaud on 2007-05-29
May 28 18:50:45 maud-desktop kernel: [   28.653400] sdb: Write Protect is off 
May 28 18:50:45 maud-desktop kernel: [   28.653424] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 18:50:45 maud-desktop kernel: [   28.653427]  sdb: sdb1 sdb2 < sdb5 > 
May 28 18:50:45 maud-desktop kernel: [   28.700276] sd 0:0:1:0: Attached scsi disk sdb 
May 28 18:50:45 maud-desktop kernel: [   28.705322] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 28 18:50:45 maud-desktop kernel: [   28.705350] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 28 18:50:45 maud-desktop kernel: [   28.705373] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 28 18:50:45 maud-desktop kernel: [   28.712978] sr0: scsi3-mmc drive: 66x/52x writer cd/rw xa/form2 cdda tray 
May 28 18:50:45 maud-desktop kernel: [   28.712984] Uniform CD-ROM driver Revision: 3.20 
May 28 18:50:45 maud-desktop kernel: [   30.700590] Attempting manual resume 
May 28 18:50:45 maud-desktop kernel: [   31.313155] kjournald starting.  Commit interval 5 seconds 
May 28 18:50:45 maud-desktop kernel: [   31.313168] EXT3-fs: mounted filesystem with ordered data mode. 
May 28 18:50:45 maud-desktop kernel: [  159.718655] NET: Registered protocol family 17 
May 28 18:50:45 maud-desktop kernel: [  168.041918] Linux agpgart interface v0.102 (c) Dave Jones 
May 28 18:50:45 maud-desktop kernel: [  168.089629] agpgart: Detected an Intel 845G Chipset. 
May 28 18:50:45 maud-desktop kernel: [  168.089892] agpgart: Detected 892K stolen memory. 
May 28 18:50:45 maud-desktop kernel: [  168.104418] agpgart: AGP aperture is 128M @ 0xf0000000 
May 28 18:50:45 maud-desktop kernel: [  168.151882] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 28 18:50:45 maud-desktop kernel: [  168.388694] intel_rng: Firmware space is locked read-only. If you can't or 
May 28 18:50:45 maud-desktop kernel: [  168.388697] intel_rng: don't want to disable this in firmware setup, and if 
May 28 18:50:45 maud-desktop kernel: [  168.388699] intel_rng: you are certain that your system has a functional 
May 28 18:50:45 maud-desktop kernel: [  168.388701] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 28 18:50:45 maud-desktop kernel: [  168.491907] iTCO_vendor_support: vendor-support=0 
May 28 18:50:45 maud-desktop kernel: [  168.494362] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 28 18:50:45 maud-desktop kernel: [  168.494475] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 28 18:50:45 maud-desktop kernel: [  168.494527] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 28 18:50:45 maud-desktop kernel: [  168.955951] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 28 18:50:45 maud-desktop kernel: [  168.969426] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 28 18:50:45 maud-desktop kernel: [  169.177920] input: PC Speaker as /class/input/input2 
May 28 18:50:45 maud-desktop kernel: [  169.271453] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 28 18:50:45 maud-desktop kernel: [  169.482091] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 28 18:50:45 maud-desktop kernel: [  169.799023] intel8x0_measure_ac97_clock: measured 55170 usecs 
May 28 18:50:45 maud-desktop kernel: [  169.799028] intel8x0: clocking to 48000 
May 28 18:50:45 maud-desktop kernel: [  169.868324] parport: PnPBIOS parport detected. 
May 28 18:50:45 maud-desktop kernel: [  169.868351] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 28 18:50:45 maud-desktop kernel: [  172.786543] fuse init (API version 7.8) 
May 28 18:50:45 maud-desktop kernel: [  172.907843] lp0: using parport0 (interrupt-driven). 
May 28 18:50:45 maud-desktop kernel: [  172.937194] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 28 18:50:45 maud-desktop kernel: [  173.748802] EXT3 FS on sdb1, internal journal 
May 28 18:50:45 maud-desktop kernel: [  182.468553] input: Power Button (FF) as /class/input/input4 
May 28 18:50:45 maud-desktop kernel: [  182.473302] ACPI: Power Button (FF) [PWRF] 
May 28 18:50:45 maud-desktop kernel: [  182.509019] input: Sleep Button (CM) as /class/input/input5 
May 28 18:50:45 maud-desktop kernel: [  182.513725] ACPI: Sleep Button (CM) [SLPB] 
May 28 18:50:45 maud-desktop kernel: [  182.528405] No dock devices found. 
May 28 18:50:45 maud-desktop kernel: [  182.626890] Using specific hotkey driver 
May 28 18:50:45 maud-desktop kernel: [  182.746368] pcc_acpi: loading... 
May 28 18:50:49 maud-desktop dhcdbd: Started up. 
May 28 18:50:50 maud-desktop kernel: [  188.333676] ppdev: user-space parallel port driver 
May 28 18:50:51 maud-desktop kernel: [  189.700613] [drm] Initialized drm 1.1.0 20060810 
May 28 18:50:51 maud-desktop kernel: [  189.730458] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 28 18:50:51 maud-desktop kernel: [  189.731133] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 28 18:50:52 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 28 18:50:53 maud-desktop kernel: [  191.244987] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
May 28 18:50:53 maud-desktop kernel: [  191.244993] apm: overridden by ACPI. 
May 28 18:50:53 maud-desktop kernel: [  191.460105] Bluetooth: Core ver 2.11 
May 28 18:50:53 maud-desktop kernel: [  191.460170] NET: Registered protocol family 31 
May 28 18:50:53 maud-desktop kernel: [  191.460173] Bluetooth: HCI device and connection manager initialized 
May 28 18:50:53 maud-desktop kernel: [  191.460177] Bluetooth: HCI socket layer initialized 
May 28 18:50:53 maud-desktop kernel: [  191.505939] Bluetooth: L2CAP ver 2.8 
May 28 18:50:53 maud-desktop kernel: [  191.505945] Bluetooth: L2CAP socket layer initialized 
May 28 18:50:53 maud-desktop kernel: [  191.664440] Bluetooth: RFCOMM socket layer initialized 
May 28 18:50:53 maud-desktop kernel: [  191.664455] Bluetooth: RFCOMM TTY layer initialized 
May 28 18:50:53 maud-desktop kernel: [  191.664458] Bluetooth: RFCOMM ver 1.8 
May 28 18:51:01 maud-desktop kernel: [  199.666596] NET: Registered protocol family 10 
May 28 18:51:01 maud-desktop kernel: [  199.666713] lo: Disabled Privacy Extensions 
May 28 18:51:01 maud-desktop kernel: [  199.666781] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): starting (version 2.18.0.1), pid 5334 user 'armaud' 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 18:51:15 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0 
May 28 18:53:06 maud-desktop gconfd (root-5548): starting (version 2.18.0.1), pid 5548 user 'root' 
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 18:53:06 maud-desktop gconfd (root-5548): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 18:53:36 maud-desktop gconfd (root-5548): GConf server is not in use, shutting down. 
May 28 18:53:36 maud-desktop gconfd (root-5548): Exiting 
May 28 18:56:06 maud-desktop gconfd (armaud-5334): Failed to send buffer 
May 28 18:56:29 maud-desktop gconfd (root-5777): starting (version 2.18.0.1), pid 5777 user 'root' 
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 18:57:29 maud-desktop gconfd (root-5777): GConf server is not in use, shutting down. 
May 28 18:57:29 maud-desktop gconfd (root-5777): Exiting 
May 28 18:57:40 maud-desktop gconfd (root-5856): starting (version 2.18.0.1), pid 5856 user 'root' 
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 19:03:10 maud-desktop gconfd (root-5856): GConf server is not in use, shutting down. 
May 28 19:03:10 maud-desktop gconfd (root-5856): Exiting 
May 28 19:03:16 maud-desktop gconfd (armaud-5334): Exiting 
May 28 19:03:25 maud-desktop exiting on signal 15 
May 28 19:06:39 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 28 19:06:40 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 28 19:06:40 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 28 19:06:40 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 28 19:06:40 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.  
May 28 19:06:40 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 28 19:06:40 maud-desktop kernel: [    0.000000] sanitize start 
May 28 19:06:40 maud-desktop kernel: [    0.000000] sanitize end 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 28 19:06:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 28 19:06:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 28 19:06:40 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 28 19:06:40 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 28 19:06:40 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 28 19:06:40 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 28 19:06:40 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 28 19:06:40 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 28 19:06:40 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 28 19:06:40 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 28 19:06:40 maud-desktop kernel: [    0.000000] Detected 2400.100 MHz processor. 
May 28 19:06:40 maud-desktop kernel: [   15.062914] Built 1 zonelists.  Total pages: 129604 
May 28 19:06:40 maud-desktop kernel: [   15.062920] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 28 19:06:40 maud-desktop kernel: [   15.063122] Enabling fast FPU save and restore... done. 
May 28 19:06:40 maud-desktop kernel: [   15.063126] Enabling unmasked SIMD FPU exception support... done. 
May 28 19:06:40 maud-desktop kernel: [   15.063141] Initializing CPU#0 
May 28 19:06:40 maud-desktop kernel: [   15.063234] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.064673] Console: colour VGA+ 80x25 
May 28 19:06:40 maud-desktop kernel: [   15.065089] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.065430] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.075744] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 28 19:06:40 maud-desktop kernel: [   15.075756] virtual kernel memory layout: 
May 28 19:06:40 maud-desktop kernel: [   15.075758]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 28 19:06:40 maud-desktop kernel: [   15.075759]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 28 19:06:40 maud-desktop kernel: [   15.075760]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 28 19:06:40 maud-desktop kernel: [   15.075762]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 28 19:06:40 maud-desktop kernel: [   15.075763]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 28 19:06:40 maud-desktop kernel: [   15.075764]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 28 19:06:40 maud-desktop kernel: [   15.075766]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 28 19:06:40 maud-desktop kernel: [   15.075769] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 28 19:06:40 maud-desktop kernel: [   15.155098] Calibrating delay using timer specific routine.. 4804.10 BogoMIPS (lpj=9608208) 
May 28 19:06:40 maud-desktop kernel: [   15.155149] Security Framework v1.0.0 initialized 
May 28 19:06:40 maud-desktop kernel: [   15.155154] SELinux:  Disabled at boot. 
May 28 19:06:40 maud-desktop kernel: [   15.155174] Mount-cache hash table entries: 512 
May 28 19:06:40 maud-desktop kernel: [   15.155339] monitor/mwait feature present. 
May 28 19:06:40 maud-desktop kernel: [   15.155342] using mwait in idle threads. 
May 28 19:06:40 maud-desktop kernel: [   15.155349] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 28 19:06:40 maud-desktop kernel: [   15.155353] CPU: L2 cache: 1024K 
May 28 19:06:40 maud-desktop kernel: [   15.155356] CPU: Hyper-Threading is disabled 
May 28 19:06:40 maud-desktop kernel: [   15.155371] Compat vDSO mapped to ffffe000. 
May 28 19:06:40 maud-desktop kernel: [   15.155376] Remapping vsyscall page to ffffe000 
May 28 19:06:40 maud-desktop kernel: [   15.155393] Checking 'hlt' instruction... OK. 
May 28 19:06:40 maud-desktop kernel: [   15.171178] SMP alternatives: switching to UP code 
May 28 19:06:40 maud-desktop kernel: [   15.171356] Freeing SMP alternatives: 11k freed 
May 28 19:06:40 maud-desktop kernel: [   15.171585] Early unpacking initramfs... done 
May 28 19:06:40 maud-desktop kernel: [   15.521669] ACPI: Core revision 20060707 
May 28 19:06:40 maud-desktop kernel: [   15.521841] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 28 19:06:40 maud-desktop kernel: [   15.524412] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 28 19:06:40 maud-desktop kernel: [   15.524459] Total of 1 processors activated (4804.10 BogoMIPS). 
May 28 19:06:40 maud-desktop kernel: [   15.524595] ENABLING IO-APIC IRQs 
May 28 19:06:40 maud-desktop kernel: [   15.524787] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 28 19:06:40 maud-desktop kernel: [   15.670350] Brought up 1 CPUs 
May 28 19:06:40 maud-desktop kernel: [   15.670632] Booting paravirtualized kernel on bare hardware 
May 28 19:06:40 maud-desktop kernel: [   15.670711] Time: 19:03:51  Date: 04/28/107 
May 28 19:06:40 maud-desktop kernel: [   15.670744] NET: Registered protocol family 16 
May 28 19:06:40 maud-desktop kernel: [   15.670847] EISA bus registered 
May 28 19:06:40 maud-desktop kernel: [   15.670852] ACPI: bus type pci registered 
May 28 19:06:40 maud-desktop kernel: [   15.670926] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 28 19:06:40 maud-desktop kernel: [   15.670928] PCI: Using configuration type 1 
May 28 19:06:40 maud-desktop kernel: [   15.670931] Setting up standard PCI resources 
May 28 19:06:40 maud-desktop kernel: [   15.685150] ACPI: Interpreter enabled 
May 28 19:06:40 maud-desktop kernel: [   15.685154] ACPI: Using IOAPIC for interrupt routing 
May 28 19:06:40 maud-desktop kernel: [   15.685559] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 28 19:06:40 maud-desktop kernel: [   15.686191] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 28 19:06:40 maud-desktop kernel: [   15.686193] * this clock source is slow. If you are sure your timer does not have 
May 28 19:06:40 maud-desktop kernel: [   15.686195] * this bug, please use "acpi_pm_good" to disable the workaround 
May 28 19:06:40 maud-desktop kernel: [   15.686244] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 28 19:06:40 maud-desktop kernel: [   15.686248] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 28 19:06:40 maud-desktop kernel: [   15.686501] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 28 19:06:40 maud-desktop kernel: [   15.686578] PCI: Transparent bridge - 0000:00:1e.0 
May 28 19:06:40 maud-desktop kernel: [   15.690813] ACPI: Power Resource [URP1] (off) 
May 28 19:06:40 maud-desktop kernel: [   15.690896] ACPI: Power Resource [FDDP] (off) 
May 28 19:06:40 maud-desktop kernel: [   15.690980] ACPI: Power Resource [LPTP] (off) 
May 28 19:06:40 maud-desktop kernel: [   15.693916] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.694386] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.694805] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.695226] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.695644] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.696063] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 19:06:40 maud-desktop kernel: [   15.696481] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 19:06:40 maud-desktop kernel: [   15.696903] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 28 19:06:40 maud-desktop kernel: [   15.697307] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 28 19:06:40 maud-desktop kernel: [   15.697325] pnp: PnP ACPI init 
May 28 19:06:40 maud-desktop kernel: [   15.701814] pnp: PnP ACPI: found 13 devices 
May 28 19:06:40 maud-desktop kernel: [   15.701821] PnPBIOS: Disabled by ACPI PNP 
May 28 19:06:40 maud-desktop kernel: [   15.701876] PCI: Using ACPI for IRQ routing 
May 28 19:06:40 maud-desktop kernel: [   15.701880] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 28 19:06:40 maud-desktop kernel: [   15.704819] NET: Registered protocol family 8 
May 28 19:06:40 maud-desktop kernel: [   15.704822] NET: Registered protocol family 20 
May 28 19:06:40 maud-desktop kernel: [   15.706136] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 28 19:06:40 maud-desktop kernel: [   15.706140] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 28 19:06:40 maud-desktop kernel: [   15.706144] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 28 19:06:40 maud-desktop kernel: [   15.706536] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 28 19:06:40 maud-desktop kernel: [   15.706547] PCI: Bridge: 0000:00:1e.0 
May 28 19:06:40 maud-desktop kernel: [   15.706551]   IO window: d000-dfff 
May 28 19:06:40 maud-desktop kernel: [   15.706557]   MEM window: ff800000-ff8fffff 
May 28 19:06:40 maud-desktop kernel: [   15.706562]   PREFETCH window: eaa00000-eaafffff 
May 28 19:06:40 maud-desktop kernel: [   15.706605] NET: Registered protocol family 2 
May 28 19:06:40 maud-desktop kernel: [   15.746280] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.746376] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.746484] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 28 19:06:40 maud-desktop kernel: [   15.746536] TCP: Hash tables configured (established 16384 bind 8192) 
May 28 19:06:40 maud-desktop kernel: [   15.746539] TCP reno registered 
May 28 19:06:40 maud-desktop kernel: [   15.758314] checking if image is initramfs... it is 
May 28 19:06:40 maud-desktop kernel: [   16.444867] Freeing initrd memory: 7005k freed 
May 28 19:06:40 maud-desktop kernel: [   16.445515] audit: initializing netlink socket (disabled) 
May 28 19:06:40 maud-desktop kernel: [   16.445534] audit(1180379031.464:1): initialized 
May 28 19:06:40 maud-desktop kernel: [   16.445681] VFS: Disk quotas dquot_6.5.1 
May 28 19:06:40 maud-desktop kernel: [   16.445706] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 28 19:06:40 maud-desktop kernel: [   16.445766] io scheduler noop registered 
May 28 19:06:40 maud-desktop kernel: [   16.445770] io scheduler anticipatory registered 
May 28 19:06:40 maud-desktop kernel: [   16.445773] io scheduler deadline registered 
May 28 19:06:40 maud-desktop kernel: [   16.445784] io scheduler cfq registered (default) 
May 28 19:06:40 maud-desktop kernel: [   16.446072] isapnp: Scanning for PnP cards... 
May 28 19:06:40 maud-desktop kernel: [   16.797616] isapnp: No Plug & Play device found 
May 28 19:06:40 maud-desktop kernel: [   16.828253] Real Time Clock Driver v1.12ac 
May 28 19:06:40 maud-desktop kernel: [   16.828318] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 28 19:06:40 maud-desktop kernel: [   16.828447] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 19:06:40 maud-desktop kernel: [   16.829289] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 19:06:40 maud-desktop kernel: [   16.829577] mice: PS/2 mouse device common for all mice 
May 28 19:06:40 maud-desktop kernel: [   16.830280] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 28 19:06:40 maud-desktop kernel: [   16.830575] input: Macintosh mouse button emulation as /class/input/input0 
May 28 19:06:40 maud-desktop kernel: [   16.830624] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 28 19:06:40 maud-desktop kernel: [   16.830629] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 28 19:06:40 maud-desktop kernel: [   16.830894] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 28 19:06:40 maud-desktop kernel: [   16.834559] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 28 19:06:40 maud-desktop kernel: [   16.834568] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 28 19:06:40 maud-desktop kernel: [   16.834738] EISA: Probing bus 0 at eisa.0 
May 28 19:06:40 maud-desktop kernel: [   16.834778] EISA: Detected 0 cards. 
May 28 19:06:40 maud-desktop kernel: [   16.864833] TCP cubic registered 
May 28 19:06:40 maud-desktop kernel: [   16.864842] NET: Registered protocol family 1 
May 28 19:06:40 maud-desktop kernel: [   16.864868] Using IPI No-Shortcut mode 
May 28 19:06:40 maud-desktop kernel: [   16.864944] ACPI: (supports S0 S1 S4 S5) 
May 28 19:06:40 maud-desktop kernel: [   16.864994]   Magic number: 7:626:92 
May 28 19:06:40 maud-desktop kernel: [   16.865512] Freeing unused kernel memory: 328k freed 
May 28 19:06:40 maud-desktop kernel: [   16.868462] Time: tsc clocksource has been installed. 
May 28 19:06:40 maud-desktop kernel: [   16.885619] input: AT Translated Set 2 keyboard as /class/input/input1 
May 28 19:06:40 maud-desktop kernel: [   18.202423] Capability LSM initialized 
May 28 19:06:40 maud-desktop kernel: [   18.545648] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 28 19:06:40 maud-desktop kernel: [   18.545660] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 28 19:06:40 maud-desktop kernel: [   28.386188] usbcore: registered new interface driver usbfs 
May 28 19:06:40 maud-desktop kernel: [   28.386216] usbcore: registered new interface driver hub 
May 28 19:06:40 maud-desktop kernel: [   28.386245] usbcore: registered new device driver usb 
May 28 19:06:40 maud-desktop kernel: [   28.387286] USB Universal Host Controller Interface driver v3.0 
May 28 19:06:40 maud-desktop kernel: [   28.387344] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 28 19:06:40 maud-desktop kernel: [   28.387363] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 28 19:06:40 maud-desktop kernel: [   28.387542] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 28 19:06:40 maud-desktop kernel: [   28.387570] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 28 19:06:40 maud-desktop kernel: [   28.387687] usb usb1: configuration #1 chosen from 1 choice 
May 28 19:06:40 maud-desktop kernel: [   28.387718] hub 1-0:1.0: USB hub found 
May 28 19:06:40 maud-desktop kernel: [   28.387726] hub 1-0:1.0: 2 ports detected 
May 28 19:06:40 maud-desktop kernel: [   28.494273] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 28 19:06:40 maud-desktop kernel: [   28.494293] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 28 19:06:40 maud-desktop kernel: [   28.494320] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 28 19:06:40 maud-desktop kernel: [   28.494352] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 28 19:06:40 maud-desktop kernel: [   28.494451] usb usb2: configuration #1 chosen from 1 choice 
May 28 19:06:40 maud-desktop kernel: [   28.494489] hub 2-0:1.0: USB hub found 
May 28 19:06:40 maud-desktop kernel: [   28.494498] hub 2-0:1.0: 2 ports detected 
May 28 19:06:40 maud-desktop kernel: [   28.598141] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 28 19:06:40 maud-desktop kernel: [   28.598161] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 28 19:06:40 maud-desktop kernel: [   28.598189] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 28 19:06:40 maud-desktop kernel: [   28.598218] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 28 19:06:40 maud-desktop kernel: [   28.598323] usb usb3: configuration #1 chosen from 1 choice 
May 28 19:06:40 maud-desktop kernel: [   28.598362] hub 3-0:1.0: USB hub found 
May 28 19:06:40 maud-desktop kernel: [   28.598372] hub 3-0:1.0: 2 ports detected 
May 28 19:06:40 maud-desktop kernel: [   28.684096] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 28 19:06:40 maud-desktop kernel: [   28.684101] e100: Copyright(c) 1999-2006 Intel Corporation 
May 28 19:06:40 maud-desktop kernel: [   28.702463] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19 
May 28 19:06:40 maud-desktop kernel: [   28.702486] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 28 19:06:40 maud-desktop kernel: [   28.702518] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 28 19:06:40 maud-desktop kernel: [   28.702560] ehci_hcd 0000:00:1d.7: debug port 1 
May 28 19:06:40 maud-desktop kernel: [   28.702579] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00 
May 28 19:06:40 maud-desktop kernel: [   28.706468] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 28 19:06:40 maud-desktop kernel: [   28.706554] usb usb4: configuration #1 chosen from 1 choice 
May 28 19:06:40 maud-desktop kernel: [   28.706587] hub 4-0:1.0: USB hub found 
May 28 19:06:40 maud-desktop kernel: [   28.706597] hub 4-0:1.0: 6 ports detected 
May 28 19:06:40 maud-desktop kernel: [   28.814030] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20 
May 28 19:06:40 maud-desktop kernel: [   28.833691] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:11:11:56:8B:A4 
May 28 19:06:40 maud-desktop kernel: [   28.860409] SCSI subsystem initialized 
May 28 19:06:40 maud-desktop kernel: [   28.871089] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 28 19:06:40 maud-desktop kernel: [   28.871097] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 28 19:06:40 maud-desktop kernel: [   28.871182] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 28 19:06:40 maud-desktop kernel: [   28.871220] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 28 19:06:40 maud-desktop kernel: [   28.871242] scsi0 : ata_piix 
May 28 19:06:40 maud-desktop kernel: [   29.045584] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 19:06:40 maud-desktop kernel: [   29.045590] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 28 19:06:40 maud-desktop kernel: [   29.045594] ata1.00: 78165360 sectors, multi 16: LBA  
May 28 19:06:40 maud-desktop kernel: [   29.045598] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 28 19:06:40 maud-desktop kernel: [   29.045602] ata1.01: 10018890 sectors, multi 16: LBA  
May 28 19:06:40 maud-desktop kernel: [   29.045608] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 28 19:06:40 maud-desktop kernel: [   29.057612] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 19:06:40 maud-desktop kernel: [   29.057618] ata1.00: configured for UDMA/33 
May 28 19:06:40 maud-desktop kernel: [   29.069429] ata1.01: configured for UDMA/33 
May 28 19:06:40 maud-desktop kernel: [   29.069445] scsi1 : ata_piix 
May 28 19:06:40 maud-desktop kernel: [   29.388961] ata2.00: ATAPI, max UDMA/33 
May 28 19:06:40 maud-desktop kernel: [   29.556686] ata2.00: configured for UDMA/33 
May 28 19:06:40 maud-desktop kernel: [   29.560468] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5

---

### Post by armaud on 2007-05-29
May 28 19:06:40 maud-desktop kernel: [   29.564452] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 28 19:06:40 maud-desktop kernel: [   29.565410] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 28 19:06:40 maud-desktop kernel: [   29.943874] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 19:06:40 maud-desktop kernel: [   29.944333] sda: Write Protect is off 
May 28 19:06:40 maud-desktop kernel: [   29.948334] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 19:06:40 maud-desktop kernel: [   29.952316] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 19:06:40 maud-desktop kernel: [   29.955816] sda: Write Protect is off 
May 28 19:06:40 maud-desktop kernel: [   29.959814] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 19:06:40 maud-desktop kernel: [   29.959818]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 28 19:06:40 maud-desktop kernel: [   30.035702] sd 0:0:0:0: Attached scsi disk sda 
May 28 19:06:40 maud-desktop kernel: [   30.039686] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 28 19:06:40 maud-desktop kernel: [   30.040179] sdb: Write Protect is off 
May 28 19:06:40 maud-desktop kernel: [   30.043692] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 19:06:40 maud-desktop kernel: [   30.043733] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 28 19:06:40 maud-desktop kernel: [   30.043746] sdb: Write Protect is off 
May 28 19:06:40 maud-desktop kernel: [   30.043770] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 19:06:40 maud-desktop kernel: [   30.043773]  sdb: sdb1 sdb2 < sdb5 > 
May 28 19:06:40 maud-desktop kernel: [   30.080673] sd 0:0:1:0: Attached scsi disk sdb 
May 28 19:06:40 maud-desktop kernel: [   30.086159] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 28 19:06:40 maud-desktop kernel: [   30.086290] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 28 19:06:40 maud-desktop kernel: [   30.086423] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 28 19:06:40 maud-desktop kernel: [   30.091736] sr0: scsi3-mmc drive: 66x/52x writer cd/rw xa/form2 cdda tray 
May 28 19:06:40 maud-desktop kernel: [   30.091743] Uniform CD-ROM driver Revision: 3.20 
May 28 19:06:40 maud-desktop kernel: [   31.951174] Attempting manual resume 
May 28 19:06:40 maud-desktop kernel: [   32.563750] kjournald starting.  Commit interval 5 seconds 
May 28 19:06:40 maud-desktop kernel: [   32.563763] EXT3-fs: mounted filesystem with ordered data mode. 
May 28 19:06:40 maud-desktop kernel: [  160.580854] NET: Registered protocol family 17 
May 28 19:06:40 maud-desktop kernel: [  169.005095] Linux agpgart interface v0.102 (c) Dave Jones 
May 28 19:06:40 maud-desktop kernel: [  169.019362] agpgart: Detected an Intel 845G Chipset. 
May 28 19:06:40 maud-desktop kernel: [  169.019611] agpgart: Detected 892K stolen memory. 
May 28 19:06:40 maud-desktop kernel: [  169.034289] agpgart: AGP aperture is 128M @ 0xf0000000 
May 28 19:06:40 maud-desktop kernel: [  169.329629] intel_rng: Firmware space is locked read-only. If you can't or 
May 28 19:06:40 maud-desktop kernel: [  169.329632] intel_rng: don't want to disable this in firmware setup, and if 
May 28 19:06:40 maud-desktop kernel: [  169.329634] intel_rng: you are certain that your system has a functional 
May 28 19:06:40 maud-desktop kernel: [  169.329636] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 28 19:06:40 maud-desktop kernel: [  169.394552] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 28 19:06:40 maud-desktop kernel: [  169.438554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 28 19:06:40 maud-desktop kernel: [  169.451971] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 28 19:06:40 maud-desktop kernel: [  169.533455] iTCO_vendor_support: vendor-support=0 
May 28 19:06:40 maud-desktop kernel: [  169.535948] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 28 19:06:40 maud-desktop kernel: [  169.536062] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 28 19:06:40 maud-desktop kernel: [  169.536111] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 28 19:06:40 maud-desktop kernel: [  169.917715] input: PC Speaker as /class/input/input2 
May 28 19:06:40 maud-desktop kernel: [  170.585776] parport: PnPBIOS parport detected. 
May 28 19:06:40 maud-desktop kernel: [  170.585803] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 28 19:06:40 maud-desktop kernel: [  170.892356] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 28 19:06:40 maud-desktop kernel: [  171.118347] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 28 19:06:40 maud-desktop kernel: [  171.209376] intel8x0_measure_ac97_clock: measured 55181 usecs
May 28 19:06:40 maud-desktop kernel: [  171.209381] intel8x0: clocking to 48000 
May 28 19:06:40 maud-desktop kernel: [  173.965262] fuse init (API version 7.8) 
May 28 19:06:40 maud-desktop kernel: [  173.983159] lp0: using parport0 (interrupt-driven). 
May 28 19:06:40 maud-desktop kernel: [  174.012452] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 28 19:06:40 maud-desktop kernel: [  174.719815] EXT3 FS on sdb1, internal journal 
May 28 19:06:40 maud-desktop kernel: [  183.253938] input: Power Button (FF) as /class/input/input4 
May 28 19:06:40 maud-desktop kernel: [  183.258677] ACPI: Power Button (FF) [PWRF] 
May 28 19:06:40 maud-desktop kernel: [  183.294519] input: Sleep Button (CM) as /class/input/input5 
May 28 19:06:40 maud-desktop kernel: [  183.299215] ACPI: Sleep Button (CM) [SLPB] 
May 28 19:06:40 maud-desktop kernel: [  183.313977] No dock devices found. 
May 28 19:06:40 maud-desktop kernel: [  183.423249] Using specific hotkey driver 
May 28 19:06:40 maud-desktop kernel: [  183.542594] pcc_acpi: loading... 
May 28 19:06:43 maud-desktop dhcdbd: Started up. 
May 28 19:06:44 maud-desktop kernel: [  188.806224] ppdev: user-space parallel port driver 
May 28 19:06:45 maud-desktop kernel: [  189.703627] [drm] Initialized drm 1.1.0 20060810 
May 28 19:06:45 maud-desktop kernel: [  189.711306] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
May 28 19:06:45 maud-desktop kernel: [  189.711992] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 28 19:06:46 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 28 19:06:47 maud-desktop kernel: [  191.549969] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
May 28 19:06:47 maud-desktop kernel: [  191.549976] apm: overridden by ACPI. 
May 28 19:06:47 maud-desktop kernel: [  191.765127] Bluetooth: Core ver 2.11 
May 28 19:06:47 maud-desktop kernel: [  191.765191] NET: Registered protocol family 31 
May 28 19:06:47 maud-desktop kernel: [  191.765194] Bluetooth: HCI device and connection manager initialized 
May 28 19:06:47 maud-desktop kernel: [  191.765198] Bluetooth: HCI socket layer initialized 
May 28 19:06:47 maud-desktop kernel: [  191.811130] Bluetooth: L2CAP ver 2.8 
May 28 19:06:47 maud-desktop kernel: [  191.811135] Bluetooth: L2CAP socket layer initialized 
May 28 19:06:47 maud-desktop kernel: [  191.947127] Bluetooth: RFCOMM socket layer initialized 
May 28 19:06:47 maud-desktop kernel: [  191.947140] Bluetooth: RFCOMM TTY layer initialized 
May 28 19:06:47 maud-desktop kernel: [  191.947143] Bluetooth: RFCOMM ver 1.8 
May 28 19:07:00 maud-desktop kernel: [  204.208835] NET: Registered protocol family 10 
May 28 19:07:00 maud-desktop kernel: [  204.208955] lo: Disabled Privacy Extensions 
May 28 19:07:00 maud-desktop kernel: [  204.209022] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): starting (version 2.18.0.1), pid 5350 user 'armaud' 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 19:11:13 maud-desktop gconfd (armaud-5350): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 19:11:21 maud-desktop gconfd (armaud-5350): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0 
May 28 19:19:24 maud-desktop gconfd (armaud-5350): Exiting 
May 28 19:19:34 maud-desktop exiting on signal 15 
May 28 21:33:17 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 28 21:33:17 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 28 21:33:17 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 28 21:33:17 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 28 21:33:17 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.  
May 28 21:33:17 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 28 21:33:17 maud-desktop kernel: [    0.000000] sanitize start 
May 28 21:33:17 maud-desktop kernel: [    0.000000] sanitize end 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 28 21:33:17 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 28 21:33:17 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 28 21:33:17 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 28 21:33:17 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 28 21:33:17 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 28 21:33:17 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 28 21:33:17 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 28 21:33:17 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 28 21:33:17 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 28 21:33:17 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 28 21:33:17 maud-desktop kernel: [    0.000000] Detected 2400.202 MHz processor. 
May 28 21:33:17 maud-desktop kernel: [   24.179498] Built 1 zonelists.  Total pages: 129604 
May 28 21:33:17 maud-desktop kernel: [   24.179503] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 28 21:33:17 maud-desktop kernel: [   24.179706] Enabling fast FPU save and restore... done. 
May 28 21:33:17 maud-desktop kernel: [   24.179709] Enabling unmasked SIMD FPU exception support... done. 
May 28 21:33:17 maud-desktop kernel: [   24.179725] Initializing CPU#0 
May 28 21:33:17 maud-desktop kernel: [   24.179818] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 28 21:33:17 maud-desktop kernel: [   24.181253] Console: colour VGA+ 80x25 
May 28 21:33:17 maud-desktop kernel: [   24.181666] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 28 21:33:17 maud-desktop kernel: [   24.182003] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 28 21:33:17 maud-desktop kernel: [   24.192295] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 28 21:33:17 maud-desktop kernel: [   24.192307] virtual kernel memory layout: 
May 28 21:33:17 maud-desktop kernel: [   24.192308]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 28 21:33:17 maud-desktop kernel: [   24.192310]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 28 21:33:17 maud-desktop kernel: [   24.192311]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 28 21:33:17 maud-desktop kernel: [   24.192313]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 28 21:33:17 maud-desktop kernel: [   24.192314]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 28 21:33:17 maud-desktop kernel: [   24.192315]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 28 21:33:17 maud-desktop kernel: [   24.192317]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 28 21:33:17 maud-desktop kernel: [   24.192320] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 28 21:33:17 maud-desktop kernel: [   24.271682] Calibrating delay using timer specific routine.. 4804.09 BogoMIPS (lpj=9608192) 
May 28 21:33:17 maud-desktop kernel: [   24.271732] Security Framework v1.0.0 initialized 
May 28 21:33:17 maud-desktop kernel: [   24.271738] SELinux:  Disabled at boot. 
May 28 21:33:17 maud-desktop kernel: [   24.271758] Mount-cache hash table entries: 512 
May 28 21:33:17 maud-desktop kernel: [   24.271924] monitor/mwait feature present. 
May 28 21:33:17 maud-desktop kernel: [   24.271926] using mwait in idle threads. 
May 28 21:33:17 maud-desktop kernel: [   24.271934] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 28 21:33:17 maud-desktop kernel: [   24.271938] CPU: L2 cache: 1024K 
May 28 21:33:17 maud-desktop kernel: [   24.271941] CPU: Hyper-Threading is disabled 
May 28 21:33:17 maud-desktop kernel: [   24.271956] Compat vDSO mapped to ffffe000. 
May 28 21:33:17 maud-desktop kernel: [   24.271960] Remapping vsyscall page to ffffe000 
May 28 21:33:17 maud-desktop kernel: [   24.271978] Checking 'hlt' instruction... OK. 
May 28 21:33:17 maud-desktop kernel: [   24.287761] SMP alternatives: switching to UP code 
May 28 21:33:17 maud-desktop kernel: [   24.287934] Freeing SMP alternatives: 11k freed 
May 28 21:33:17 maud-desktop kernel: [   24.288162] Early unpacking initramfs... done 
May 28 21:33:17 maud-desktop kernel: [   24.638655] ACPI: Core revision 20060707 
May 28 21:33:17 maud-desktop kernel: [   24.638829] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 28 21:33:17 maud-desktop kernel: [   24.641650] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 28 21:33:17 maud-desktop kernel: [   24.641698] Total of 1 processors activated (4804.09 BogoMIPS). 
May 28 21:33:17 maud-desktop kernel: [   24.641833] ENABLING IO-APIC IRQs 
May 28 21:33:17 maud-desktop kernel: [   24.642025] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 28 21:33:17 maud-desktop kernel: [   24.786934] Brought up 1 CPUs 
May 28 21:33:17 maud-desktop kernel: [   24.787213] Booting paravirtualized kernel on bare hardware 
May 28 21:33:17 maud-desktop kernel: [   24.787291] Time: 21:30:28  Date: 04/28/107 
May 28 21:33:17 maud-desktop kernel: [   24.787321] NET: Registered protocol family 16 
May 28 21:33:17 maud-desktop kernel: [   24.787422] EISA bus registered 
May 28 21:33:17 maud-desktop kernel: [   24.787429] ACPI: bus type pci registered 
May 28 21:33:17 maud-desktop kernel: [   24.787502] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 28 21:33:17 maud-desktop kernel: [   24.787505] PCI: Using configuration type 1 
May 28 21:33:17 maud-desktop kernel: [   24.787507] Setting up standard PCI resources 
May 28 21:33:17 maud-desktop kernel: [   24.802008] ACPI: Interpreter enabled 
May 28 21:33:17 maud-desktop kernel: [   24.802012] ACPI: Using IOAPIC for interrupt routing 
May 28 21:33:17 maud-desktop kernel: [   24.802417] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 28 21:33:17 maud-desktop kernel: [   24.803061] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 28 21:33:17 maud-desktop kernel: [   24.803063] * this clock source is slow. If you are sure your timer does not have 
May 28 21:33:17 maud-desktop kernel: [   24.803065] * this bug, please use "acpi_pm_good" to disable the workaround 
May 28 21:33:17 maud-desktop kernel: [   24.803114] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 28 21:33:17 maud-desktop kernel: [   24.803118] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 28 21:33:17 maud-desktop kernel: [   24.803360] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 28 21:33:17 maud-desktop kernel: [   24.803437] PCI: Transparent bridge - 0000:00:1e.0 
May 28 21:33:17 maud-desktop kernel: [   24.807458] ACPI: Power Resource [URP1] (off) 
May 28 21:33:17 maud-desktop kernel: [   24.807541] ACPI: Power Resource [FDDP] (off) 
May 28 21:33:17 maud-desktop kernel: [   24.807625] ACPI: Power Resource [LPTP] (off) 
May 28 21:33:17 maud-desktop kernel: [   24.810556] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.811026] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.811444] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.811862] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.812279] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.812694] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 21:33:17 maud-desktop kernel: [   24.813111] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 28 21:33:17 maud-desktop kernel: [   24.813533] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 28 21:33:17 maud-desktop kernel: [   24.813938] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 28 21:33:17 maud-desktop kernel: [   24.813955] pnp: PnP ACPI init 
May 28 21:33:17 maud-desktop kernel: [   24.818453] pnp: PnP ACPI: found 13 devices 
May 28 21:33:17 maud-desktop kernel: [   24.818460] PnPBIOS: Disabled by ACPI PNP 
May 28 21:33:17 maud-desktop kernel: [   24.818517] PCI: Using ACPI for IRQ routing 
May 28 21:33:17 maud-desktop kernel: [   24.818521] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 28 21:33:17 maud-desktop kernel: [   24.821425] NET: Registered protocol family 8 
May 28 21:33:17 maud-desktop kernel: [   24.821428] NET: Registered protocol family 20 
May 28 21:33:17 maud-desktop kernel: [   24.822739] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 28 21:33:17 maud-desktop kernel: [   24.822743] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 28 21:33:17 maud-desktop kernel: [   24.822746] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 28 21:33:17 maud-desktop kernel: [   24.823140] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 28 21:33:17 maud-desktop kernel: [   24.823151] PCI: Bridge: 0000:00:1e.0 
May 28 21:33:17 maud-desktop kernel: [   24.823155]   IO window: d000-dfff 
May 28 21:33:17 maud-desktop kernel: [   24.823161]   MEM window: ff800000-ff8fffff 
May 28 21:33:17 maud-desktop kernel: [   24.823166]   PREFETCH window: eaa00000-eaafffff 
May 28 21:33:17 maud-desktop kernel: [   24.823208] NET: Registered protocol family 2 
May 28 21:33:17 maud-desktop kernel: [   24.862864] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 28 21:33:17 maud-desktop kernel: [   24.862963] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 28 21:33:17 maud-desktop kernel: [   24.863075] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 28 21:33:17 maud-desktop kernel: [   24.863129] TCP: Hash tables configured (established 16384 bind 8192) 
May 28 21:33:17 maud-desktop kernel: [   24.863132] TCP reno registered 
May 28 21:33:17 maud-desktop kernel: [   24.874903] checking if image is initramfs... it is 
May 28 21:33:17 maud-desktop kernel: [   25.562051] Freeing initrd memory: 7005k freed 
May 28 21:33:17 maud-desktop kernel: [   25.562674] audit: initializing netlink socket (disabled) 
May 28 21:33:17 maud-desktop kernel: [   25.562694] audit(1180387829.464:1): initialized 
May 28 21:33:17 maud-desktop kernel: [   25.562841] VFS: Disk quotas dquot_6.5.1 
May 28 21:33:17 maud-desktop kernel: [   25.562865] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 28 21:33:17 maud-desktop kernel: [   25.562924] io scheduler noop registered 
May 28 21:33:17 maud-desktop kernel: [   25.562928] io scheduler anticipatory registered 
May 28 21:33:17 maud-desktop kernel: [   25.562931] io scheduler deadline registered 
May 28 21:33:17 maud-desktop kernel: [   25.562941] io scheduler cfq registered (default) 
May 28 21:33:17 maud-desktop kernel: [   25.563234] isapnp: Scanning for PnP cards... 
May 28 21:33:17 maud-desktop kernel: [   25.914789] isapnp: No Plug & Play device found 
May 28 21:33:17 maud-desktop kernel: [   25.945685] Real Time Clock Driver v1.12ac 
May 28 21:33:17 maud-desktop kernel: [   25.945750] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 28 21:33:17 maud-desktop kernel: [   25.945878] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 21:33:17 maud-desktop kernel: [   25.946668] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 28 21:33:17 maud-desktop kernel: [   25.946951] mice: PS/2 mouse device common for all mice 
May 28 21:33:17 maud-desktop kernel: [   25.947666] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 28 21:33:17 maud-desktop kernel: [   25.947958] input: Macintosh mouse button emulation as /class/input/input0 
May 28 21:33:17 maud-desktop kernel: [   25.948006] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 28 21:33:17 maud-desktop kernel: [   25.948011] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 28 21:33:17 maud-desktop kernel: [   25.948278] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 28 21:33:17 maud-desktop kernel: [   25.951311] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 28 21:33:17 maud-desktop kernel: [   25.951318] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 28 21:33:17 maud-desktop kernel: [   25.951464] EISA: Probing bus 0 at eisa.0 
May 28 21:33:17 maud-desktop kernel: [   25.951505] EISA: Detected 0 cards. 
May 28 21:33:17 maud-desktop kernel: [   25.981558] TCP cubic registered 
May 28 21:33:17 maud-desktop kernel: [   25.981566] NET: Registered protocol family 1 
May 28 21:33:17 maud-desktop kernel: [   25.981592] Using IPI No-Shortcut mode 
May 28 21:33:17 maud-desktop kernel: [   25.981671] ACPI: (supports S0 S1 S4 S5) 
May 28 21:33:17 maud-desktop kernel: [   25.981720]   Magic number: 7:803:551 
May 28 21:33:17 maud-desktop kernel: [   25.982260] Freeing unused kernel memory: 328k freed 
May 28 21:33:17 maud-desktop kernel: [   25.985046] Time: tsc clocksource has been installed. 
May 28 21:33:17 maud-desktop kernel: [   26.001311] input: AT Translated Set 2 keyboard as /class/input/input1 
May 28 21:33:17 maud-desktop kernel: [   27.323152] Capability LSM initialized 
May 28 21:33:17 maud-desktop kernel: [   27.666349] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 28 21:33:17 maud-desktop kernel: [   27.666362] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 28 21:33:17 maud-desktop kernel: [   36.914211] usbcore: registered new interface driver usbfs 
May 28 21:33:17 maud-desktop kernel: [   36.914238] usbcore: registered new interface driver hub 
May 28 21:33:17 maud-desktop kernel: [   36.914265] usbcore: registered new device driver usb 
May 28 21:33:17 maud-desktop kernel: [   36.915298] USB Universal Host Controller Interface driver v3.0 
May 28 21:33:17 maud-desktop kernel: [   36.915355] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 28 21:33:17 maud-desktop kernel: [   36.915373] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 28 21:33:17 maud-desktop kernel: [   36.915528] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 28 21:33:17 maud-desktop kernel: [   36.915555] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 28 21:33:17 maud-desktop kernel: [   36.915670] usb usb1: configuration #1 chosen from 1 choice 
May 28 21:33:17 maud-desktop kernel: [   36.915704] hub 1-0:1.0: USB hub found 
May 28 21:33:17 maud-desktop kernel: [   36.915712] hub 1-0:1.0: 2 ports detected 
May 28 21:33:17 maud-desktop kernel: [   37.016521] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 28 21:33:17 maud-desktop kernel: [   37.016542] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 28 21:33:17 maud-desktop kernel: [   37.016573] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 28 21:33:17 maud-desktop kernel: [   37.016605] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 28 21:33:17 maud-desktop kernel: [   37.016708] usb usb2: configuration #1 chosen from 1 choice 
May 28 21:33:17 maud-desktop kernel: [   37.016738] hub 2-0:1.0: USB hub found 
May 28 21:33:17 maud-desktop kernel: [   37.016748] hub 2-0:1.0: 2 ports detected 
May 28 21:33:17 maud-desktop kernel: [   37.071171] SCSI subsystem initialized 
May 28 21:33:17 maud-desktop kernel: [   37.120372] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 28 21:33:17 maud-desktop kernel: [   37.120393] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 28 21:33:17 maud-desktop kernel: [   37.120421] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 28 21:33:17 maud-desktop kernel: [   37.120451] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 28 21:33:17 maud-desktop kernel: [   37.120559] usb usb3: configuration #1 chosen from 1 choice 
May 28 21:33:17 maud-desktop kernel: [   37.120590] hub 3-0:1.0: USB hub found 
May 28 21:33:17 maud-desktop kernel: [   37.120598] hub 3-0:1.0: 2 ports detected 
May 28 21:33:17 maud-desktop kernel: [   37.224749] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19 
May 28 21:33:17 maud-desktop kernel: [   37.224774] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 28 21:33:17 maud-desktop kernel: [   37.224809] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 28 21:33:17 maud-desktop kernel: [   37.224852] ehci_hcd 0000:00:1d.7: debug port 1 
May 28 21:33:17 maud-desktop kernel: [   37.224870] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00 
May 28 21:33:17 maud-desktop kernel: [   37.228747] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 28 21:33:17 maud-desktop kernel: [   37.228836] usb usb4: configuration #1 chosen from 1 choice 
May 28 21:33:17 maud-desktop kernel: [   37.228870] hub 4-0:1.0: USB hub found 
May 28 21:33:17 maud-desktop kernel: [   37.228880] hub 4-0:1.0: 6 ports detected 
May 28 21:33:17 maud-desktop kernel: [   37.334624] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 28 21:33:17 maud-desktop kernel: [   37.334633] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 28 21:33:17 maud-desktop kernel: [   37.334714] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 28 21:33:17 maud-desktop kernel: [   37.334750] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 28 21:33:17 maud-desktop kernel: [   37.334774] scsi0 : ata_piix 
May 28 21:33:17 maud-desktop kernel: [   37.503985] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 21:33:17 maud-desktop kernel: [   37.503990] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 28 21:33:17 maud-desktop kernel: [   37.503994] ata1.00: 78165360 sectors, multi 16: LBA  
May 28 21:33:17 maud-desktop kernel: [   37.503999] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 28 21:33:17 maud-desktop kernel: [   37.504002] ata1.01: 10018890 sectors, multi 16: LBA  
May 28 21:33:17 maud-desktop kernel: [   37.504009] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 28 21:33:17 maud-desktop kernel: [   37.512003] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 28 21:33:17 maud-desktop kernel: [   37.512009] ata1.00: configured for UDMA/33 
May 28 21:33:17 maud-desktop kernel: [   37.519851] ata1.01: configured for UDMA/33 
May 28 21:33:17 maud-desktop kernel: [   37.519870] scsi1 : ata_piix 
May 28 21:33:17 maud-desktop kernel: [   37.526693] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 28 21:33:17 maud-desktop kernel: [   37.526697] e100: Copyright(c) 1999-2006 Intel Corporation 
May 28 21:33:17 maud-desktop kernel: [   37.839344] ata2.00: ATAPI, max UDMA/33 
May 28 21:33:17 maud-desktop kernel: [   38.003115] ata2.00: configured for UDMA/33 
May 28 21:33:17 maud-desktop kernel: [   38.006907] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5 
May 28 21:33:17 maud-desktop kernel: [   38.010890] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 28 21:33:17 maud-desktop kernel: [   38.011849] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 28 21:33:17 maud-desktop kernel: [   38.013597] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20 
May 28 21:33:17 maud-desktop kernel: [   38.033290] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:11:11:56:8B:A4 
May 28 21:33:17 maud-desktop kernel: [   38.461845] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 21:33:17 maud-desktop kernel: [   38.462187] sda: Write Protect is off 
May 28 21:33:17 maud-desktop kernel: [   38.466211] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 21:33:17 maud-desktop kernel: [   38.470174] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 28 21:33:17 maud-desktop kernel: [   38.473815] sda: Write Protect is off 
May 28 21:33:17 maud-desktop kernel: [   38.477814] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 21:33:17 maud-desktop kernel: [   38.477818]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 28 21:33:17 maud-desktop kernel: [   38.562828] sd 0:0:0:0: Attached scsi disk sda 
May 28 21:33:17 maud-desktop kernel: [   38.566041] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 28 21:33:17 maud-desktop kernel: [   38.569679] sdb: Write Protect is off 
May 28 21:33:17 maud-desktop kernel: [   38.573714] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 21:33:17 maud-desktop kernel: [   38.577657] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 28 21:33:17 maud-desktop kernel: [   38.578008] sdb: Write Protect is off 
May 28 21:33:17 maud-desktop kernel: [   38.582031] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 28 21:33:17 maud-desktop kernel: [   38.582035]  sdb: sdb1 sdb2 < sdb5 > 
May 28 21:33:17 maud-desktop kernel: [   38.621752] sd 0:0:1:0: Attached scsi disk sdb 
May 28 21:33:17 maud-desktop kernel: [   38.628270] sr0: scsi3-mmc drive: 64x/52x writer cd/rw xa/form2 cdda tray 
May 28 21:33:17 maud-desktop kernel: [   38.628277] Uniform CD-ROM driver Revision: 3.20 
May 28 21:33:17 maud-desktop kernel: [   38.631732] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 28 21:33:17 maud-desktop kernel: [   38.631875] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 28 21:33:17 maud-desktop kernel: [   38.632004] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 28 21:33:17 maud-desktop kernel: [   40.577472] Attempting manual resume 
May 28 21:33:17 maud-desktop kernel: [   41.190088] kjournald starting.  Commit interval 5 seconds 
May 28 21:33:17 maud-desktop kernel: [   41.190101] EXT3-fs: mounted filesystem with ordered data mode. 
May 28 21:33:17 maud-desktop kernel: [  168.835993] NET: Registered protocol family 17 
May 28 21:33:17 maud-desktop kernel: [  177.613821] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 28 21:33:17 maud-desktop kernel: [  177.870047] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 28 21:33:17 maud-desktop kernel: [  177.883544] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 28 21:33:17 maud-desktop kernel: [  177.973253] Linux agpgart interface v0.102 (c) Dave Jones 
May 28 21:33:17 maud-desktop kernel: [  177.987535] agpgart: Detected an Intel 845G Chipset. 
May 28 21:33:17 maud-desktop kernel: [  177.987781] agpgart: Detected 892K stolen memory. 
May 28 21:33:17 maud-desktop kernel: [  178.002368] agpgart: AGP aperture is 128M @ 0xf0000000 
May 28 21:33:17 maud-desktop kernel: [  178.420597] intel_rng: Firmware space is locked read-only. If you can't or 
May 28 21:33:17 maud-desktop kernel: [  178.420600] intel_rng: don't want to disable this in firmware setup, and if 
May 28 21:33:17 maud-desktop kernel: [  178.420602] intel_rng: you are certain that your system has a functional 
May 28 21:33:17 maud-desktop kernel: [  178.420604] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 28 21:33:17 maud-desktop kernel: [  178.691333] iTCO_vendor_support: vendor-support=0 
May 28 21:33:17 maud-desktop kernel: [  178.693826] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 28 21:33:17 maud-desktop kernel: [  178.693937] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 28 21:33:17 maud-desktop kernel: [  178.693985] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 28 21:33:17 maud-desktop kernel: [  178.796218] input: PC Speaker as /class/input/input2 
May 28 21:33:17 maud-desktop kernel: [  179.195851] parport: PnPBIOS parport detected. 
May 28 21:33:17 maud-desktop kernel: [  179.195878] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 28 21:33:17 maud-desktop kernel: [  179.424446] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 28 21:33:17 maud-desktop kernel: [  179.744173] intel8x0_measure_ac97_clock: measured 59178 usecs 
May 28 21:33:17 maud-desktop kernel: [  179.744178] intel8x0: clocking to 48000 
May 28 21:33:17 maud-desktop kernel: [  180.009465] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 28 21:33:17 maud-desktop kernel: [  182.388406] fuse init (API version 7.8) 
May 28 21:33:17 maud-desktop kernel: [  182.514088] lp0: using parport0 (interrupt-driven). 
May 28 21:33:17 maud-desktop kernel: [  182.543485] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 28 21:33:17 maud-desktop kernel: [  183.350721] EXT3 FS on sdb1, internal journal 
May 28 21:33:17 maud-desktop kernel: [  192.184680] input: Power Button (FF) as /class/input/input4 
May 28 21:33:17 maud-desktop kernel: [  192.189417] ACPI: Power Button (FF) [PWRF] 
May 28 21:33:17 maud-desktop kernel: [  192.224884] input: Sleep Button (CM) as /class/input/input5 
May 28 21:33:17 maud-desktop kernel: [  192.229589] ACPI: Sleep Button (CM) [SLPB] 
May 28 21:33:17 maud-desktop kernel: [  192.244194] No dock devices found. 
May 28 21:33:17 maud-desktop kernel: [  192.354008] Using specific hotkey driver 
May 28 21:33:17 maud-desktop kernel: [  192.473293] pcc_acpi: loading... 
May 28 21:33:21 maud-desktop dhcdbd: Started up. 
May 28 21:33:22 maud-desktop kernel: [  197.947716] ppdev: user-space parallel port driver 
May 28 21:33:23 maud-desktop kernel: [  199.146826] [drm] Initialized drm 1.1.0 20060810 
May 28 21:33:23 maud-desktop kernel: [  199.176665] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 28 21:33:23 maud-desktop kernel: [  199.177334] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 28 21:33:24 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 28 21:33:25 maud-desktop kernel: [  200.724341] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

---

### Post by armaud on 2007-05-29
May 28 21:33:25 maud-desktop kernel: [  200.724348] apm: overridden by ACPI. 
May 28 21:33:25 maud-desktop kernel: [  200.939456] Bluetooth: Core ver 2.11 
May 28 21:33:25 maud-desktop kernel: [  200.939522] NET: Registered protocol family 31 
May 28 21:33:25 maud-desktop kernel: [  200.939525] Bluetooth: HCI device and connection manager initialized
May 28 21:33:25 maud-desktop kernel: [  200.939529] Bluetooth: HCI socket layer initialized 
May 28 21:33:25 maud-desktop kernel: [  200.985137] Bluetooth: L2CAP ver 2.8 
May 28 21:33:25 maud-desktop kernel: [  200.985143] Bluetooth: L2CAP socket layer initialized 
May 28 21:33:25 maud-desktop kernel: [  201.132593] Bluetooth: RFCOMM socket layer initialized 
May 28 21:33:25 maud-desktop kernel: [  201.132607] Bluetooth: RFCOMM TTY layer initialized 
May 28 21:33:25 maud-desktop kernel: [  201.132610] Bluetooth: RFCOMM ver 1.8 
May 28 21:33:33 maud-desktop kernel: [  209.422130] NET: Registered protocol family 10 
May 28 21:33:33 maud-desktop kernel: [  209.422244] lo: Disabled Privacy Extensions 
May 28 21:33:33 maud-desktop kernel: [  209.422309] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): starting (version 2.18.0.1), pid 5348 user 'armaud' 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 28 21:33:52 maud-desktop gconfd (armaud-5348): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 28 21:34:00 maud-desktop gconfd (armaud-5348): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0 
May 28 21:48:13 maud-desktop gconfd (armaud-5348): Exiting 
May 28 21:48:23 maud-desktop exiting on signal 15 
May 29 14:03:40 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 29 14:03:40 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 29 14:03:40 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 29 14:03:40 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 29 14:03:40 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.
May 29 14:03:40 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 29 14:03:40 maud-desktop kernel: [    0.000000] sanitize start 
May 29 14:03:40 maud-desktop kernel: [    0.000000] sanitize end 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 29 14:03:40 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 29 14:03:40 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 29 14:03:40 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 29 14:03:40 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 29 14:03:40 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 29 14:03:40 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 29 14:03:40 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 29 14:03:40 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 29 14:03:40 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 29 14:03:40 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 29 14:03:40 maud-desktop kernel: [    0.000000] Detected 2400.162 MHz processor. 
May 29 14:03:40 maud-desktop kernel: [   23.632944] Built 1 zonelists.  Total pages: 129604 
May 29 14:03:40 maud-desktop kernel: [   23.632949] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 29 14:03:40 maud-desktop kernel: [   23.633152] Enabling fast FPU save and restore... done. 
May 29 14:03:40 maud-desktop kernel: [   23.633156] Enabling unmasked SIMD FPU exception support... done. 
May 29 14:03:40 maud-desktop kernel: [   23.633171] Initializing CPU#0 
May 29 14:03:40 maud-desktop kernel: [   23.633264] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 29 14:03:40 maud-desktop kernel: [   23.634704] Console: colour VGA+ 80x25 
May 29 14:03:40 maud-desktop kernel: [   23.635097] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 29 14:03:40 maud-desktop kernel: [   23.635423] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 29 14:03:40 maud-desktop kernel: [   23.645716] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 29 14:03:40 maud-desktop kernel: [   23.645728] virtual kernel memory layout: 
May 29 14:03:40 maud-desktop kernel: [   23.645729]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 29 14:03:40 maud-desktop kernel: [   23.645731]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 29 14:03:40 maud-desktop kernel: [   23.645732]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 29 14:03:40 maud-desktop kernel: [   23.645734]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 29 14:03:40 maud-desktop kernel: [   23.645735]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 29 14:03:40 maud-desktop kernel: [   23.645736]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 29 14:03:40 maud-desktop kernel: [   23.645738]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 29 14:03:40 maud-desktop kernel: [   23.645741] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 29 14:03:40 maud-desktop kernel: [   23.725129] Calibrating delay using timer specific routine.. 4804.08 BogoMIPS (lpj=9608167) 
May 29 14:03:40 maud-desktop kernel: [   23.725180] Security Framework v1.0.0 initialized 
May 29 14:03:40 maud-desktop kernel: [   23.725185] SELinux:  Disabled at boot. 
May 29 14:03:40 maud-desktop kernel: [   23.725204] Mount-cache hash table entries: 512 
May 29 14:03:40 maud-desktop kernel: [   23.725368] monitor/mwait feature present. 
May 29 14:03:40 maud-desktop kernel: [   23.725371] using mwait in idle threads. 
May 29 14:03:40 maud-desktop kernel: [   23.725378] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 29 14:03:40 maud-desktop kernel: [   23.725382] CPU: L2 cache: 1024K 
May 29 14:03:40 maud-desktop kernel: [   23.725385] CPU: Hyper-Threading is disabled 
May 29 14:03:40 maud-desktop kernel: [   23.725400] Compat vDSO mapped to ffffe000. 
May 29 14:03:40 maud-desktop kernel: [   23.725404] Remapping vsyscall page to ffffe000 
May 29 14:03:40 maud-desktop kernel: [   23.725423] Checking 'hlt' instruction... OK. 
May 29 14:03:40 maud-desktop kernel: [   23.741209] SMP alternatives: switching to UP code 
May 29 14:03:40 maud-desktop kernel: [   23.741386] Freeing SMP alternatives: 11k freed 
May 29 14:03:40 maud-desktop kernel: [   23.741616] Early unpacking initramfs... done 
May 29 14:03:40 maud-desktop kernel: [   24.092010] ACPI: Core revision 20060707 
May 29 14:03:40 maud-desktop kernel: [   24.092182] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 29 14:03:40 maud-desktop kernel: [   24.094770] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 29 14:03:40 maud-desktop kernel: [   24.094818] Total of 1 processors activated (4804.08 BogoMIPS). 
May 29 14:03:40 maud-desktop kernel: [   24.094954] ENABLING IO-APIC IRQs 
May 29 14:03:40 maud-desktop kernel: [   24.095147] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 29 14:03:40 maud-desktop kernel: [   24.240382] Brought up 1 CPUs 
May 29 14:03:40 maud-desktop kernel: [   24.240662] Booting paravirtualized kernel on bare hardware 
May 29 14:03:40 maud-desktop kernel: [   24.240740] Time: 14:00:52  Date: 04/29/107 
May 29 14:03:40 maud-desktop kernel: [   24.240772] NET: Registered protocol family 16 
May 29 14:03:40 maud-desktop kernel: [   24.240874] EISA bus registered 
May 29 14:03:40 maud-desktop kernel: [   24.240880] ACPI: bus type pci registered 
May 29 14:03:40 maud-desktop kernel: [   24.240954] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 29 14:03:40 maud-desktop kernel: [   24.240957] PCI: Using configuration type 1 
May 29 14:03:40 maud-desktop kernel: [   24.240959] Setting up standard PCI resources 
May 29 14:03:40 maud-desktop kernel: [   24.255193] ACPI: Interpreter enabled 
May 29 14:03:40 maud-desktop kernel: [   24.255197] ACPI: Using IOAPIC for interrupt routing 
May 29 14:03:40 maud-desktop kernel: [   24.255602] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 29 14:03:40 maud-desktop kernel: [   24.256232] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 29 14:03:40 maud-desktop kernel: [   24.256234] * this clock source is slow. If you are sure your timer does not have 
May 29 14:03:40 maud-desktop kernel: [   24.256236] * this bug, please use "acpi_pm_good" to disable the workaround 
May 29 14:03:40 maud-desktop kernel: [   24.256284] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 29 14:03:40 maud-desktop kernel: [   24.256288] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 29 14:03:40 maud-desktop kernel: [   24.256543] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 29 14:03:40 maud-desktop kernel: [   24.256619] PCI: Transparent bridge - 0000:00:1e.0 
May 29 14:03:40 maud-desktop kernel: [   24.260630] ACPI: Power Resource [URP1] (off) 
May 29 14:03:40 maud-desktop kernel: [   24.260712] ACPI: Power Resource [FDDP] (off) 
May 29 14:03:40 maud-desktop kernel: [   24.260797] ACPI: Power Resource [LPTP] (off) 
May 29 14:03:40 maud-desktop kernel: [   24.263726] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.264150] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.264609] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.265029] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.265446] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.265860] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 14:03:40 maud-desktop kernel: [   24.266271] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 14:03:40 maud-desktop kernel: [   24.266690] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 29 14:03:40 maud-desktop kernel: [   24.267096] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 29 14:03:40 maud-desktop kernel: [   24.267115] pnp: PnP ACPI init 
May 29 14:03:40 maud-desktop kernel: [   24.271600] pnp: PnP ACPI: found 13 devices 
May 29 14:03:40 maud-desktop kernel: [   24.271607] PnPBIOS: Disabled by ACPI PNP 
May 29 14:03:40 maud-desktop kernel: [   24.271663] PCI: Using ACPI for IRQ routing 
May 29 14:03:40 maud-desktop kernel: [   24.271666] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 29 14:03:40 maud-desktop kernel: [   24.274579] NET: Registered protocol family 8 
May 29 14:03:40 maud-desktop kernel: [   24.274582] NET: Registered protocol family 20 
May 29 14:03:40 maud-desktop kernel: [   24.275882] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 29 14:03:40 maud-desktop kernel: [   24.275886] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 29 14:03:40 maud-desktop kernel: [   24.275889] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 29 14:03:40 maud-desktop kernel: [   24.276246] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 29 14:03:40 maud-desktop kernel: [   24.276257] PCI: Bridge: 0000:00:1e.0 
May 29 14:03:40 maud-desktop kernel: [   24.276261]   IO window: d000-dfff 
May 29 14:03:40 maud-desktop kernel: [   24.276267]   MEM window: ff800000-ff8fffff 
May 29 14:03:40 maud-desktop kernel: [   24.276273]   PREFETCH window: eaa00000-eaafffff 
May 29 14:03:41 maud-desktop kernel: [   24.276347] NET: Registered protocol family 2 
May 29 14:03:41 maud-desktop kernel: [   24.316309] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
May 29 14:03:41 maud-desktop kernel: [   24.316400] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 29 14:03:41 maud-desktop kernel: [   24.316510] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 29 14:03:41 maud-desktop kernel: [   24.316565] TCP: Hash tables configured (established 16384 bind 8192) 
May 29 14:03:41 maud-desktop kernel: [   24.316568] TCP reno registered 
May 29 14:03:41 maud-desktop kernel: [   24.328351] checking if image is initramfs... it is 
May 29 14:03:41 maud-desktop kernel: [   25.015430] Freeing initrd memory: 7005k freed 
May 29 14:03:41 maud-desktop kernel: [   25.016052] audit: initializing netlink socket (disabled) 
May 29 14:03:41 maud-desktop kernel: [   25.016072] audit(1180447252.464:1): initialized 
May 29 14:03:41 maud-desktop kernel: [   25.016224] VFS: Disk quotas dquot_6.5.1 
May 29 14:03:41 maud-desktop kernel: [   25.016248] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 29 14:03:41 maud-desktop kernel: [   25.016308] io scheduler noop registered 
May 29 14:03:41 maud-desktop kernel: [   25.016312] io scheduler anticipatory registered 
May 29 14:03:41 maud-desktop kernel: [   25.016314] io scheduler deadline registered 
May 29 14:03:41 maud-desktop kernel: [   25.016325] io scheduler cfq registered (default) 
May 29 14:03:41 maud-desktop kernel: [   25.016617] isapnp: Scanning for PnP cards... 
May 29 14:03:41 maud-desktop kernel: [   25.368140] isapnp: No Plug & Play device found 
May 29 14:03:41 maud-desktop kernel: [   25.398854] Real Time Clock Driver v1.12ac 
May 29 14:03:41 maud-desktop kernel: [   25.398918] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 29 14:03:41 maud-desktop kernel: [   25.399045] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 14:03:41 maud-desktop kernel: [   25.399866] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 14:03:41 maud-desktop kernel: [   25.400161] mice: PS/2 mouse device common for all mice 
May 29 14:03:41 maud-desktop kernel: [   25.400875] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 29 14:03:41 maud-desktop kernel: [   25.401168] input: Macintosh mouse button emulation as /class/input/input0 
May 29 14:03:41 maud-desktop kernel: [   25.401217] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 29 14:03:41 maud-desktop kernel: [   25.401222] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 29 14:03:41 maud-desktop kernel: [   25.401485] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 29 14:03:41 maud-desktop kernel: [   25.405099] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 29 14:03:41 maud-desktop kernel: [   25.405108] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 29 14:03:41 maud-desktop kernel: [   25.405277] EISA: Probing bus 0 at eisa.0 
May 29 14:03:41 maud-desktop kernel: [   25.405318] EISA: Detected 0 cards. 
May 29 14:03:41 maud-desktop kernel: [   25.435371] TCP cubic registered 
May 29 14:03:41 maud-desktop kernel: [   25.435379] NET: Registered protocol family 1 
May 29 14:03:41 maud-desktop kernel: [   25.435404] Using IPI No-Shortcut mode 
May 29 14:03:41 maud-desktop kernel: [   25.435482] ACPI: (supports S0 S1 S4 S5) 
May 29 14:03:41 maud-desktop kernel: [   25.435531]   Magic number: 7:618:31 
May 29 14:03:41 maud-desktop kernel: [   25.435543]   hash matches device ttyde 
May 29 14:03:41 maud-desktop kernel: [   25.436053] Freeing unused kernel memory: 328k freed 
May 29 14:03:41 maud-desktop kernel: [   25.438492] Time: tsc clocksource has been installed. 
May 29 14:03:41 maud-desktop kernel: [   25.455569] input: AT Translated Set 2 keyboard as /class/input/input1 
May 29 14:03:41 maud-desktop kernel: [   26.772620] Capability LSM initialized

---

### Post by armaud on 2007-05-29
May 29 14:03:41 maud-desktop kernel: [   27.115885] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 29 14:03:41 maud-desktop kernel: [   27.115897] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 29 14:03:41 maud-desktop kernel: [   36.954729] usbcore: registered new interface driver usbfs 
May 29 14:03:41 maud-desktop kernel: [   36.954756] usbcore: registered new interface driver hub 
May 29 14:03:41 maud-desktop kernel: [   36.954783] usbcore: registered new device driver usb 
May 29 14:03:41 maud-desktop kernel: [   36.955814] USB Universal Host Controller Interface driver v3.0 
May 29 14:03:41 maud-desktop kernel: [   36.955872] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 14:03:41 maud-desktop kernel: [   36.955890] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 29 14:03:41 maud-desktop kernel: [   36.956071] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 29 14:03:41 maud-desktop kernel: [   36.956099] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 29 14:03:41 maud-desktop kernel: [   36.956214] usb usb1: configuration #1 chosen from 1 choice 
May 29 14:03:41 maud-desktop kernel: [   36.956245] hub 1-0:1.0: USB hub found 
May 29 14:03:41 maud-desktop kernel: [   36.956254] hub 1-0:1.0: 2 ports detected 
May 29 14:03:41 maud-desktop kernel: [   37.057079] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 29 14:03:41 maud-desktop kernel: [   37.057099] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 29 14:03:41 maud-desktop kernel: [   37.057133] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 29 14:03:41 maud-desktop kernel: [   37.057165] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 29 14:03:41 maud-desktop kernel: [   37.057270] usb usb2: configuration #1 chosen from 1 choice 
May 29 14:03:41 maud-desktop kernel: [   37.057301] hub 2-0:1.0: USB hub found 
May 29 14:03:41 maud-desktop kernel: [   37.057311] hub 2-0:1.0: 2 ports detected 
May 29 14:03:41 maud-desktop kernel: [   37.112861] SCSI subsystem initialized 
May 29 14:03:41 maud-desktop kernel: [   37.160963] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 29 14:03:41 maud-desktop kernel: [   37.160983] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 29 14:03:41 maud-desktop kernel: [   37.161012] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 29 14:03:41 maud-desktop kernel: [   37.161044] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 29 14:03:41 maud-desktop kernel: [   37.161154] usb usb3: configuration #1 chosen from 1 choice 
May 29 14:03:41 maud-desktop kernel: [   37.161185] hub 3-0:1.0: USB hub found 
May 29 14:03:41 maud-desktop kernel: [   37.161193] hub 3-0:1.0: 2 ports detected 
May 29 14:03:41 maud-desktop kernel: [   37.265538] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19 
May 29 14:03:41 maud-desktop kernel: [   37.265561] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 29 14:03:41 maud-desktop kernel: [   37.265598] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 29 14:03:41 maud-desktop kernel: [   37.265642] ehci_hcd 0000:00:1d.7: debug port 1 
May 29 14:03:41 maud-desktop kernel: [   37.265661] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00 
May 29 14:03:41 maud-desktop kernel: [   37.269548] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 29 14:03:41 maud-desktop kernel: [   37.269642] usb usb4: configuration #1 chosen from 1 choice 
May 29 14:03:41 maud-desktop kernel: [   37.269676] hub 4-0:1.0: USB hub found 
May 29 14:03:41 maud-desktop kernel: [   37.269685] hub 4-0:1.0: 6 ports detected 
May 29 14:03:41 maud-desktop kernel: [   37.272012] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 29 14:03:41 maud-desktop kernel: [   37.272015] e100: Copyright(c) 1999-2006 Intel Corporation 
May 29 14:03:41 maud-desktop kernel: [   37.375207] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 29 14:03:41 maud-desktop kernel: [   37.375215] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 29 14:03:41 maud-desktop kernel: [   37.375298] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 29 14:03:41 maud-desktop kernel: [   37.375335] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 29 14:03:41 maud-desktop kernel: [   37.375357] scsi0 : ata_piix 
May 29 14:03:41 maud-desktop kernel: [   37.544538] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 14:03:41 maud-desktop kernel: [   37.544544] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 29 14:03:41 maud-desktop kernel: [   37.544548] ata1.00: 78165360 sectors, multi 16: LBA  
May 29 14:03:41 maud-desktop kernel: [   37.544552] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 29 14:03:41 maud-desktop kernel: [   37.544556] ata1.01: 10018890 sectors, multi 16: LBA  
May 29 14:03:41 maud-desktop kernel: [   37.544562] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 29 14:03:41 maud-desktop kernel: [   37.552557] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 14:03:41 maud-desktop kernel: [   37.552561] ata1.00: configured for UDMA/33 
May 29 14:03:41 maud-desktop kernel: [   37.560411] ata1.01: configured for UDMA/33 
May 29 14:03:41 maud-desktop kernel: [   37.560432] scsi1 : ata_piix 
May 29 14:03:41 maud-desktop kernel: [   37.879915] ata2.00: ATAPI, max UDMA/33 
May 29 14:03:41 maud-desktop kernel: [   38.043692] ata2.00: configured for UDMA/33 
May 29 14:03:41 maud-desktop kernel: [   38.047497] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5 
May 29 14:03:41 maud-desktop kernel: [   38.051455] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 29 14:03:41 maud-desktop kernel: [   38.052415] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 29 14:03:41 maud-desktop kernel: [   38.054015] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20 
May 29 14:03:41 maud-desktop kernel: [   38.073705] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:11:11:56:8B:A4 
May 29 14:03:41 maud-desktop kernel: [   38.506403] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 14:03:41 maud-desktop kernel: [   38.506755] sda: Write Protect is off 
May 29 14:03:41 maud-desktop kernel: [   38.510736] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 14:03:41 maud-desktop kernel: [   38.514744] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 14:03:41 maud-desktop kernel: [   38.518369] sda: Write Protect is off 
May 29 14:03:41 maud-desktop kernel: [   38.522376] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 14:03:41 maud-desktop kernel: [   38.522380]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 29 14:03:41 maud-desktop kernel: [   38.610101] sd 0:0:0:0: Attached scsi disk sda 
May 29 14:03:41 maud-desktop kernel: [   38.614211] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 14:03:41 maud-desktop kernel: [   38.614596] sdb: Write Protect is off 
May 29 14:03:41 maud-desktop kernel: [   38.618594] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 14:03:41 maud-desktop kernel: [   38.622560] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 14:03:41 maud-desktop kernel: [   38.626185] sdb: Write Protect is off 
May 29 14:03:41 maud-desktop kernel: [   38.630179] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 14:03:41 maud-desktop kernel: [   38.630183]  sdb: sdb1 sdb2 < sdb5 > 
May 29 14:03:41 maud-desktop kernel: [   38.671615] sd 0:0:1:0: Attached scsi disk sdb 
May 29 14:03:41 maud-desktop kernel: [   38.677093] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 29 14:03:41 maud-desktop kernel: [   38.677223] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 29 14:03:41 maud-desktop kernel: [   38.677356] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 29 14:03:41 maud-desktop kernel: [   38.682616] sr0: scsi3-mmc drive: 64x/52x writer cd/rw xa/form2 cdda tray 
May 29 14:03:41 maud-desktop kernel: [   38.682623] Uniform CD-ROM driver Revision: 3.20 
May 29 14:03:41 maud-desktop kernel: [   40.014954] Attempting manual resume 
May 29 14:03:41 maud-desktop kernel: [   40.627545] kjournald starting.  Commit interval 5 seconds 
May 29 14:03:41 maud-desktop kernel: [   40.627558] EXT3-fs: mounted filesystem with ordered data mode. 
May 29 14:03:41 maud-desktop kernel: [  168.879275] NET: Registered protocol family 17 
May 29 14:03:41 maud-desktop kernel: [  177.356231] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 29 14:03:41 maud-desktop kernel: [  177.391482] Linux agpgart interface v0.102 (c) Dave Jones 
May 29 14:03:41 maud-desktop kernel: [  177.405778] agpgart: Detected an Intel 845G Chipset. 
May 29 14:03:41 maud-desktop kernel: [  177.406025] agpgart: Detected 892K stolen memory. 
May 29 14:03:41 maud-desktop kernel: [  177.420667] agpgart: AGP aperture is 128M @ 0xf0000000 
May 29 14:03:41 maud-desktop kernel: [  177.458913] intel_rng: Firmware space is locked read-only. If you can't or 
May 29 14:03:41 maud-desktop kernel: [  177.458916] intel_rng: don't want to disable this in firmware setup, and if 
May 29 14:03:41 maud-desktop kernel: [  177.458918] intel_rng: you are certain that your system has a functional 
May 29 14:03:41 maud-desktop kernel: [  177.458920] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 29 14:03:41 maud-desktop kernel: [  177.500679] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 29 14:03:41 maud-desktop kernel: [  177.514141] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 29 14:03:41 maud-desktop kernel: [  177.562086] iTCO_vendor_support: vendor-support=0 
May 29 14:03:41 maud-desktop kernel: [  177.564584] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 29 14:03:41 maud-desktop kernel: [  177.564690] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 29 14:03:41 maud-desktop kernel: [  177.564738] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 29 14:03:41 maud-desktop kernel: [  178.471576] input: PC Speaker as /class/input/input2 
May 29 14:03:41 maud-desktop kernel: [  178.943158] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 29 14:03:41 maud-desktop kernel: [  179.005358] parport: PnPBIOS parport detected. 
May 29 14:03:41 maud-desktop kernel: [  179.005384] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 29 14:03:41 maud-desktop kernel: [  179.026039] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 29 14:03:41 maud-desktop kernel: [  179.265516] intel8x0_measure_ac97_clock: measured 59184 usecs 
May 29 14:03:41 maud-desktop kernel: [  179.265521] intel8x0: clocking to 48000 
May 29 14:03:41 maud-desktop kernel: [  182.077517] fuse init (API version 7.8) 
May 29 14:03:41 maud-desktop kernel: [  182.200973] lp0: using parport0 (interrupt-driven). 
May 29 14:03:41 maud-desktop kernel: [  182.230420] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 29 14:03:41 maud-desktop kernel: [  183.039783] EXT3 FS on sdb1, internal journal 
May 29 14:03:41 maud-desktop kernel: [  191.257731] input: Power Button (FF) as /class/input/input4 
May 29 14:03:41 maud-desktop kernel: [  191.262482] ACPI: Power Button (FF) [PWRF] 
May 29 14:03:41 maud-desktop kernel: [  191.297992] input: Sleep Button (CM) as /class/input/input5 
May 29 14:03:41 maud-desktop kernel: [  191.302714] ACPI: Sleep Button (CM) [SLPB] 
May 29 14:03:41 maud-desktop kernel: [  191.317432] No dock devices found. 
May 29 14:03:41 maud-desktop kernel: [  191.427120] Using specific hotkey driver 
May 29 14:03:41 maud-desktop kernel: [  191.557637] pcc_acpi: loading... 
May 29 14:03:44 maud-desktop dhcdbd: Started up. 
May 29 14:03:45 maud-desktop kernel: [  196.742012] ppdev: user-space parallel port driver 
May 29 14:03:46 maud-desktop kernel: [  197.751236] [drm] Initialized drm 1.1.0 20060810 
May 29 14:03:46 maud-desktop kernel: [  197.781046] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 14:03:46 maud-desktop kernel: [  197.781818] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 29 14:03:46 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 29 14:03:47 maud-desktop kernel: [  199.284201] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
May 29 14:03:47 maud-desktop kernel: [  199.284207] apm: overridden by ACPI. 
May 29 14:03:48 maud-desktop kernel: [  199.499345] Bluetooth: Core ver 2.11 
May 29 14:03:48 maud-desktop kernel: [  199.499408] NET: Registered protocol family 31 
May 29 14:03:48 maud-desktop kernel: [  199.499411] Bluetooth: HCI device and connection manager initialized 
May 29 14:03:48 maud-desktop kernel: [  199.499415] Bluetooth: HCI socket layer initialized 
May 29 14:03:48 maud-desktop kernel: [  199.768472] Bluetooth: L2CAP ver 2.8 
May 29 14:03:48 maud-desktop kernel: [  199.768478] Bluetooth: L2CAP socket layer initialized 
May 29 14:03:48 maud-desktop kernel: [  199.804225] Bluetooth: RFCOMM socket layer initialized 
May 29 14:03:48 maud-desktop kernel: [  199.804241] Bluetooth: RFCOMM TTY layer initialized 
May 29 14:03:48 maud-desktop kernel: [  199.804243] Bluetooth: RFCOMM ver 1.8 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): starting (version 2.18.0.1), pid 5317 user 'armaud' 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 14:03:59 maud-desktop gconfd (armaud-5317): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 14:03:59 maud-desktop kernel: [  211.356069] NET: Registered protocol family 10 
May 29 14:03:59 maud-desktop kernel: [  211.356181] lo: Disabled Privacy Extensions 
May 29 14:03:59 maud-desktop kernel: [  211.356238] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 29 14:04:09 maud-desktop gconfd (armaud-5317): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0 
May 29 14:04:37 maud-desktop gconfd (root-5490): starting (version 2.18.0.1), pid 5490 user 'root' 
May 29 14:04:37 maud-desktop gconfd (root-5490): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 14:04:37 maud-desktop gconfd (root-5490): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 29 14:04:37 maud-desktop gconfd (root-5490): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 14:04:37 maud-desktop gconfd (root-5490): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 14:04:37 maud-desktop gconfd (root-5490): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 14:08:07 maud-desktop gconfd (root-5490): GConf server is not in use, shutting down. 
May 29 14:08:07 maud-desktop gconfd (root-5490): Exiting 
May 29 14:08:08 maud-desktop gconfd (root-5594): starting (version 2.18.0.1), pid 5594 user 'root' 
May 29 14:08:08 maud-desktop gconfd (root-5594): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 14:08:08 maud-desktop gconfd (root-5594): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 29 14:08:08 maud-desktop gconfd (root-5594): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 14:08:08 maud-desktop gconfd (root-5594): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 14:08:08 maud-desktop gconfd (root-5594): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 14:08:38 maud-desktop gconfd (root-5594): GConf server is not in use, shutting down. 
May 29 14:08:38 maud-desktop gconfd (root-5594): Exiting 
May 29 14:10:33 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 29 14:12:04 maud-desktop gconfd (armaud-5317): Exiting 
May 29 14:12:13 maud-desktop exiting on signal 15 
May 29 18:02:31 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 29 18:02:31 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 29 18:02:31 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 29 18:02:31 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 29 18:02:31 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.  
May 29 18:02:31 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 29 18:02:31 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 29 18:02:31 maud-desktop kernel: [    0.000000] sanitize start 
May 29 18:02:31 maud-desktop kernel: [    0.000000] sanitize end 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 29 18:02:31 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 29 18:02:31 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 29 18:02:31 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 29 18:02:31 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 29 18:02:31 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 29 18:02:32 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 29 18:02:32 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 29 18:02:32 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 29 18:02:32 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 29 18:02:32 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 29 18:02:32 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 29 18:02:32 maud-desktop kernel: [    0.000000] Detected 2400.210 MHz processor. 
May 29 18:02:32 maud-desktop kernel: [   17.290753] Built 1 zonelists.  Total pages: 129604 
May 29 18:02:32 maud-desktop kernel: [   17.290759] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 29 18:02:32 maud-desktop kernel: [   17.290961] Enabling fast FPU save and restore... done. 
May 29 18:02:32 maud-desktop kernel: [   17.290964] Enabling unmasked SIMD FPU exception support... done. 
May 29 18:02:32 maud-desktop kernel: [   17.290979] Initializing CPU#0 
May 29 18:02:32 maud-desktop kernel: [   17.291071] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.292496] Console: colour VGA+ 80x25 
May 29 18:02:32 maud-desktop kernel: [   17.292894] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.293238] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.303678] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 29 18:02:32 maud-desktop kernel: [   17.303690] virtual kernel memory layout:

---

### Post by armaud on 2007-05-29
May 29 18:02:32 maud-desktop kernel: [   17.303692]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 29 18:02:32 maud-desktop kernel: [   17.303693]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 29 18:02:32 maud-desktop kernel: [   17.303694]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 29 18:02:32 maud-desktop kernel: [   17.303696]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 29 18:02:32 maud-desktop kernel: [   17.303697]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 29 18:02:32 maud-desktop kernel: [   17.303698]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 29 18:02:32 maud-desktop kernel: [   17.303700]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 29 18:02:32 maud-desktop kernel: [   17.303703] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 29 18:02:32 maud-desktop kernel: [   17.382935] Calibrating delay using timer specific routine.. 4804.14 BogoMIPS (lpj=9608288) 
May 29 18:02:32 maud-desktop kernel: [   17.382986] Security Framework v1.0.0 initialized 
May 29 18:02:32 maud-desktop kernel: [   17.382991] SELinux:  Disabled at boot. 
May 29 18:02:32 maud-desktop kernel: [   17.383011] Mount-cache hash table entries: 512 
May 29 18:02:32 maud-desktop kernel: [   17.383175] monitor/mwait feature present. 
May 29 18:02:32 maud-desktop kernel: [   17.383178] using mwait in idle threads. 
May 29 18:02:32 maud-desktop kernel: [   17.383185] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 29 18:02:32 maud-desktop kernel: [   17.383189] CPU: L2 cache: 1024K 
May 29 18:02:32 maud-desktop kernel: [   17.383192] CPU: Hyper-Threading is disabled 
May 29 18:02:32 maud-desktop kernel: [   17.383207] Compat vDSO mapped to ffffe000. 
May 29 18:02:32 maud-desktop kernel: [   17.383212] Remapping vsyscall page to ffffe000 
May 29 18:02:32 maud-desktop kernel: [   17.383230] Checking 'hlt' instruction... OK. 
May 29 18:02:32 maud-desktop kernel: [   17.399015] SMP alternatives: switching to UP code 
May 29 18:02:32 maud-desktop kernel: [   17.399192] Freeing SMP alternatives: 11k freed 
May 29 18:02:32 maud-desktop kernel: [   17.399422] Early unpacking initramfs... done 
May 29 18:02:32 maud-desktop kernel: [   17.749565] ACPI: Core revision 20060707 
May 29 18:02:32 maud-desktop kernel: [   17.749738] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 29 18:02:32 maud-desktop kernel: [   17.752303] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 29 18:02:32 maud-desktop kernel: [   17.752351] Total of 1 processors activated (4804.14 BogoMIPS). 
May 29 18:02:32 maud-desktop kernel: [   17.752485] ENABLING IO-APIC IRQs 
May 29 18:02:32 maud-desktop kernel: [   17.752677] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 29 18:02:32 maud-desktop kernel: [   17.898195] Brought up 1 CPUs 
May 29 18:02:32 maud-desktop kernel: [   17.898473] Booting paravirtualized kernel on bare hardware 
May 29 18:02:32 maud-desktop kernel: [   17.898551] Time: 17:59:42  Date: 04/29/107 
May 29 18:02:32 maud-desktop kernel: [   17.898584] NET: Registered protocol family 16 
May 29 18:02:32 maud-desktop kernel: [   17.898688] EISA bus registered 
May 29 18:02:32 maud-desktop kernel: [   17.898695] ACPI: bus type pci registered 
May 29 18:02:32 maud-desktop kernel: [   17.898768] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 29 18:02:32 maud-desktop kernel: [   17.898771] PCI: Using configuration type 1 
May 29 18:02:32 maud-desktop kernel: [   17.898773] Setting up standard PCI resources 
May 29 18:02:32 maud-desktop kernel: [   17.913013] ACPI: Interpreter enabled 
May 29 18:02:32 maud-desktop kernel: [   17.913017] ACPI: Using IOAPIC for interrupt routing 
May 29 18:02:32 maud-desktop kernel: [   17.913421] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 29 18:02:32 maud-desktop kernel: [   17.914052] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 29 18:02:32 maud-desktop kernel: [   17.914054] * this clock source is slow. If you are sure your timer does not have 
May 29 18:02:32 maud-desktop kernel: [   17.914056] * this bug, please use "acpi_pm_good" to disable the workaround 
May 29 18:02:32 maud-desktop kernel: [   17.914104] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 29 18:02:32 maud-desktop kernel: [   17.914108] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 29 18:02:32 maud-desktop kernel: [   17.914362] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 29 18:02:32 maud-desktop kernel: [   17.914439] PCI: Transparent bridge - 0000:00:1e.0 
May 29 18:02:32 maud-desktop kernel: [   17.918457] ACPI: Power Resource [URP1] (off) 
May 29 18:02:32 maud-desktop kernel: [   17.918541] ACPI: Power Resource [FDDP] (off) 
May 29 18:02:32 maud-desktop kernel: [   17.918625] ACPI: Power Resource [LPTP] (off) 
May 29 18:02:32 maud-desktop kernel: [   17.921555] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.921984] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.922445] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.922870] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.923288] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.923702] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 18:02:32 maud-desktop kernel: [   17.924118] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 18:02:32 maud-desktop kernel: [   17.924539] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 29 18:02:32 maud-desktop kernel: [   17.924947] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 29 18:02:32 maud-desktop kernel: [   17.924964] pnp: PnP ACPI init 
May 29 18:02:32 maud-desktop kernel: [   17.929474] pnp: PnP ACPI: found 13 devices 
May 29 18:02:32 maud-desktop kernel: [   17.929480] PnPBIOS: Disabled by ACPI PNP 
May 29 18:02:32 maud-desktop kernel: [   17.929536] PCI: Using ACPI for IRQ routing 
May 29 18:02:32 maud-desktop kernel: [   17.929540] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 29 18:02:32 maud-desktop kernel: [   17.932449] NET: Registered protocol family 8 
May 29 18:02:32 maud-desktop kernel: [   17.932452] NET: Registered protocol family 20 
May 29 18:02:32 maud-desktop kernel: [   17.933761] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 29 18:02:32 maud-desktop kernel: [   17.933765] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 29 18:02:32 maud-desktop kernel: [   17.933769] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 29 18:02:32 maud-desktop kernel: [   17.934158] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 29 18:02:32 maud-desktop kernel: [   17.934169] PCI: Bridge: 0000:00:1e.0 
May 29 18:02:32 maud-desktop kernel: [   17.934173]   IO window: d000-dfff 
May 29 18:02:32 maud-desktop kernel: [   17.934179]   MEM window: ff800000-ff8fffff 
May 29 18:02:32 maud-desktop kernel: [   17.934184]   PREFETCH window: eaa00000-eaafffff 
May 29 18:02:32 maud-desktop kernel: [   17.934229] NET: Registered protocol family 2 
May 29 18:02:32 maud-desktop kernel: [   17.974119] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.974212] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.974322] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 29 18:02:32 maud-desktop kernel: [   17.974374] TCP: Hash tables configured (established 16384 bind 8192) 
May 29 18:02:32 maud-desktop kernel: [   17.974377] TCP reno registered 
May 29 18:02:32 maud-desktop kernel: [   17.986157] checking if image is initramfs... it is 
May 29 18:02:32 maud-desktop kernel: [   18.673639] Freeing initrd memory: 7005k freed 
May 29 18:02:32 maud-desktop kernel: [   18.674249] audit: initializing netlink socket (disabled) 
May 29 18:02:32 maud-desktop kernel: [   18.674268] audit(1180461583.464:1): initialized 
May 29 18:02:32 maud-desktop kernel: [   18.674415] VFS: Disk quotas dquot_6.5.1 
May 29 18:02:32 maud-desktop kernel: [   18.674439] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 29 18:02:32 maud-desktop kernel: [   18.674497] io scheduler noop registered 
May 29 18:02:32 maud-desktop kernel: [   18.674500] io scheduler anticipatory registered 
May 29 18:02:32 maud-desktop kernel: [   18.674503] io scheduler deadline registered 
May 29 18:02:32 maud-desktop kernel: [   18.674514] io scheduler cfq registered (default) 
May 29 18:02:32 maud-desktop kernel: [   18.674805] isapnp: Scanning for PnP cards... 
May 29 18:02:32 maud-desktop kernel: [   19.026347] isapnp: No Plug & Play device found 
May 29 18:02:32 maud-desktop kernel: [   19.056784] Real Time Clock Driver v1.12ac 
May 29 18:02:32 maud-desktop kernel: [   19.056851] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 29 18:02:32 maud-desktop kernel: [   19.056981] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 18:02:32 maud-desktop kernel: [   19.057764] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 18:02:32 maud-desktop kernel: [   19.058059] mice: PS/2 mouse device common for all mice 
May 29 18:02:32 maud-desktop kernel: [   19.058768] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 29 18:02:32 maud-desktop kernel: [   19.059050] input: Macintosh mouse button emulation as /class/input/input0 
May 29 18:02:32 maud-desktop kernel: [   19.059099] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 29 18:02:32 maud-desktop kernel: [   19.059104] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 29 18:02:32 maud-desktop kernel: [   19.059367] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 29 18:02:32 maud-desktop kernel: [   19.063116] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 29 18:02:32 maud-desktop kernel: [   19.063125] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 29 18:02:32 maud-desktop kernel: [   19.063302] EISA: Probing bus 0 at eisa.0 
May 29 18:02:32 maud-desktop kernel: [   19.063344] EISA: Detected 0 cards. 
May 29 18:02:32 maud-desktop kernel: [   19.093397] TCP cubic registered 
May 29 18:02:32 maud-desktop kernel: [   19.093406] NET: Registered protocol family 1 
May 29 18:02:32 maud-desktop kernel: [   19.093432] Using IPI No-Shortcut mode 
May 29 18:02:32 maud-desktop kernel: [   19.093508] ACPI: (supports S0 S1 S4 S5) 
May 29 18:02:32 maud-desktop kernel: [   19.093558]   Magic number: 7:419:998 
May 29 18:02:32 maud-desktop kernel: [   19.093583]   hash matches device ttyae 
May 29 18:02:32 maud-desktop kernel: [   19.093745]   hash matches device 00:00 
May 29 18:02:32 maud-desktop kernel: [   19.094072] Freeing unused kernel memory: 328k freed 
May 29 18:02:32 maud-desktop kernel: [   19.096298] Time: tsc clocksource has been installed. 
May 29 18:02:32 maud-desktop kernel: [   19.113470] input: AT Translated Set 2 keyboard as /class/input/input1 
May 29 18:02:32 maud-desktop kernel: [   20.434277] Capability LSM initialized 
May 29 18:02:32 maud-desktop kernel: [   20.777359] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 29 18:02:32 maud-desktop kernel: [   20.777372] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 29 18:02:32 maud-desktop kernel: [   30.611808] usbcore: registered new interface driver usbfs 
May 29 18:02:32 maud-desktop kernel: [   30.611835] usbcore: registered new interface driver hub 
May 29 18:02:32 maud-desktop kernel: [   30.611862] usbcore: registered new device driver usb 
May 29 18:02:32 maud-desktop kernel: [   30.612894] USB Universal Host Controller Interface driver v3.0 
May 29 18:02:32 maud-desktop kernel: [   30.612954] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 18:02:32 maud-desktop kernel: [   30.612972] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 29 18:02:32 maud-desktop kernel: [   30.613163] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 29 18:02:32 maud-desktop kernel: [   30.613192] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 29 18:02:32 maud-desktop kernel: [   30.613311] usb usb1: configuration #1 chosen from 1 choice 
May 29 18:02:32 maud-desktop kernel: [   30.613343] hub 1-0:1.0: USB hub found 
May 29 18:02:32 maud-desktop kernel: [   30.613351] hub 1-0:1.0: 2 ports detected 
May 29 18:02:32 maud-desktop kernel: [   30.718117] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 29 18:02:32 maud-desktop kernel: [   30.718137] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 29 18:02:32 maud-desktop kernel: [   30.718170] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 29 18:02:32 maud-desktop kernel: [   30.718202] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 29 18:02:32 maud-desktop kernel: [   30.718305] usb usb2: configuration #1 chosen from 1 choice 
May 29 18:02:32 maud-desktop kernel: [   30.718338] hub 2-0:1.0: USB hub found 
May 29 18:02:32 maud-desktop kernel: [   30.718347] hub 2-0:1.0: 2 ports detected 
May 29 18:02:32 maud-desktop kernel: [   30.770197] SCSI subsystem initialized 
May 29 18:02:32 maud-desktop kernel: [   30.821964] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 29 18:02:32 maud-desktop kernel: [   30.821984] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 29 18:02:32 maud-desktop kernel: [   30.822012] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 29 18:02:32 maud-desktop kernel: [   30.822043] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 29 18:02:32 maud-desktop kernel: [   30.822156] usb usb3: configuration #1 chosen from 1 choice 
May 29 18:02:32 maud-desktop kernel: [   30.822187] hub 3-0:1.0: USB hub found 
May 29 18:02:32 maud-desktop kernel: [   30.822195] hub 3-0:1.0: 2 ports detected 
May 29 18:02:32 maud-desktop kernel: [   30.924037] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 29 18:02:32 maud-desktop kernel: [   30.924042] e100: Copyright(c) 1999-2006 Intel Corporation 
May 29 18:02:32 maud-desktop kernel: [   30.926557] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19 
May 29 18:02:32 maud-desktop kernel: [   30.926582] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 29 18:02:32 maud-desktop kernel: [   30.926617] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 29 18:02:32 maud-desktop kernel: [   30.926659] ehci_hcd 0000:00:1d.7: debug port 1 
May 29 18:02:32 maud-desktop kernel: [   30.926678] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00 
May 29 18:02:32 maud-desktop kernel: [   30.930567] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 29 18:02:32 maud-desktop kernel: [   30.930656] usb usb4: configuration #1 chosen from 1 choice 
May 29 18:02:32 maud-desktop kernel: [   30.930695] hub 4-0:1.0: USB hub found 
May 29 18:02:32 maud-desktop kernel: [   30.930705] hub 4-0:1.0: 6 ports detected 
May 29 18:02:32 maud-desktop kernel: [   31.040223] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 29 18:02:32 maud-desktop kernel: [   31.040232] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 29 18:02:32 maud-desktop kernel: [   31.040313] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 29 18:02:32 maud-desktop kernel: [   31.040352] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 29 18:02:32 maud-desktop kernel: [   31.040376] scsi0 : ata_piix 
May 29 18:02:32 maud-desktop kernel: [   31.213522] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 18:02:32 maud-desktop kernel: [   31.213529] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 29 18:02:32 maud-desktop kernel: [   31.213532] ata1.00: 78165360 sectors, multi 16: LBA  
May 29 18:02:32 maud-desktop kernel: [   31.213537] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 29 18:02:32 maud-desktop kernel: [   31.213541] ata1.01: 10018890 sectors, multi 16: LBA  
May 29 18:02:32 maud-desktop kernel: [   31.213548] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 29 18:02:32 maud-desktop kernel: [   31.225545] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 18:02:32 maud-desktop kernel: [   31.225551] ata1.00: configured for UDMA/33 
May 29 18:02:32 maud-desktop kernel: [   31.237400] ata1.01: configured for UDMA/33 
May 29 18:02:32 maud-desktop kernel: [   31.237418] scsi1 : ata_piix 
May 29 18:02:32 maud-desktop kernel: [   31.556861] ata2.00: ATAPI, max UDMA/33 
May 29 18:02:32 maud-desktop kernel: [   31.724633] ata2.00: configured for UDMA/33 
May 29 18:02:32 maud-desktop kernel: [   31.728408] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5 
May 29 18:02:32 maud-desktop kernel: [   31.732390] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 29 18:02:32 maud-desktop kernel: [   31.733371] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 29 18:02:32 maud-desktop kernel: [   31.734961] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20 
May 29 18:02:32 maud-desktop kernel: [   31.754634] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:11:11:56:8B:A4 
May 29 18:02:32 maud-desktop kernel: [   32.164206] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 18:02:32 maud-desktop kernel: [   32.167737] sda: Write Protect is off 
May 29 18:02:32 maud-desktop kernel: [   32.171694] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:02:32 maud-desktop kernel: [   32.175690] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 18:02:32 maud-desktop kernel: [   32.176167] sda: Write Protect is off 
May 29 18:02:32 maud-desktop kernel: [   32.180152] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:02:32 maud-desktop kernel: [   32.180156]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 29 18:02:32 maud-desktop kernel: [   32.260989] sd 0:0:0:0: Attached scsi disk sda 
May 29 18:02:32 maud-desktop kernel: [   32.263577] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 18:02:32 maud-desktop kernel: [   32.263591] sdb: Write Protect is off 
May 29 18:02:32 maud-desktop kernel: [   32.263616] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:02:32 maud-desktop kernel: [   32.263661] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 18:02:32 maud-desktop kernel: [   32.263674] sdb: Write Protect is off 
May 29 18:02:32 maud-desktop kernel: [   32.263697] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:02:32 maud-desktop kernel: [   32.263701]  sdb: sdb1 sdb2 < sdb5 > 
May 29 18:02:32 maud-desktop kernel: [   32.303075] sd 0:0:1:0: Attached scsi disk sdb 
May 29 18:02:32 maud-desktop kernel: [   32.308418] sr0: scsi3-mmc drive: 66x/52x writer cd/rw xa/form2 cdda tray 
May 29 18:02:32 maud-desktop kernel: [   32.308422] Uniform CD-ROM driver Revision: 3.20 
May 29 18:02:32 maud-desktop kernel: [   32.313789] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 29 18:02:32 maud-desktop kernel: [   32.313923] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 29 18:02:32 maud-desktop kernel: [   32.314054] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 29 18:02:32 maud-desktop kernel: [   34.390733] Attempting manual resume 
May 29 18:02:32 maud-desktop kernel: [   35.003260] kjournald starting.  Commit interval 5 seconds 
May 29 18:02:32 maud-desktop kernel: [   35.003273] EXT3-fs: mounted filesystem with ordered data mode. 
May 29 18:02:32 maud-desktop kernel: [  163.530487] NET: Registered protocol family 17 
May 29 18:02:32 maud-desktop kernel: [  171.819000] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 29 18:02:32 maud-desktop kernel: [  172.072595] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 29 18:02:32 maud-desktop kernel: [  172.086066] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 29 18:02:32 maud-desktop kernel: [  172.175758] Linux agpgart interface v0.102 (c) Dave Jones 
May 29 18:02:32 maud-desktop kernel: [  172.189995] agpgart: Detected an Intel 845G Chipset. 
May 29 18:02:32 maud-desktop kernel: [  172.190241] agpgart: Detected 892K stolen memory. 
May 29 18:02:32 maud-desktop kernel: [  172.204866] agpgart: AGP aperture is 128M @ 0xf0000000 
May 29 18:02:32 maud-desktop kernel: [  172.623126] intel_rng: Firmware space is locked read-only. If you can't or 
May 29 18:02:32 maud-desktop kernel: [  172.623130] intel_rng: don't want to disable this in firmware setup, and if 
May 29 18:02:32 maud-desktop kernel: [  172.623131] intel_rng: you are certain that your system has a functional 
May 29 18:02:32 maud-desktop kernel: [  172.623133] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 29 18:02:32 maud-desktop kernel: [  172.882676] iTCO_vendor_support: vendor-support=0 
May 29 18:02:32 maud-desktop kernel: [  172.885178] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 29 18:02:32 maud-desktop kernel: [  172.885282] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 29 18:02:32 maud-desktop kernel: [  172.885329] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 29 18:02:32 maud-desktop kernel: [  172.987583] input: PC Speaker as /class/input/input2 
May 29 18:02:32 maud-desktop kernel: [  173.398355] parport: PnPBIOS parport detected.

---

### Post by armaud on 2007-05-29
May 29 18:02:32 maud-desktop kernel: [  173.398382] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 29 18:02:32 maud-desktop kernel: [  173.615761] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 29 18:02:32 maud-desktop kernel: [  173.932410] intel8x0_measure_ac97_clock: measured 55163 usecs 
May 29 18:02:32 maud-desktop kernel: [  173.932414] intel8x0: clocking to 48000 
May 29 18:02:32 maud-desktop kernel: [  174.198775] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 29 18:02:32 maud-desktop kernel: [  176.576490] fuse init (API version 7.8) 
May 29 18:02:32 maud-desktop kernel: [  176.694186] lp0: using parport0 (interrupt-driven). 
May 29 18:02:32 maud-desktop kernel: [  176.723560] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 29 18:02:32 maud-desktop kernel: [  177.538733] EXT3 FS on sdb1, internal journal 
May 29 18:02:32 maud-desktop kernel: [  185.749859] input: Power Button (FF) as /class/input/input4 
May 29 18:02:32 maud-desktop kernel: [  185.754600] ACPI: Power Button (FF) [PWRF] 
May 29 18:02:32 maud-desktop kernel: [  185.790363] input: Sleep Button (CM) as /class/input/input5 
May 29 18:02:32 maud-desktop kernel: [  185.795088] ACPI: Sleep Button (CM) [SLPB] 
May 29 18:02:32 maud-desktop kernel: [  185.809769] No dock devices found. 
May 29 18:02:32 maud-desktop kernel: [  185.908119] Using specific hotkey driver 
May 29 18:02:32 maud-desktop kernel: [  186.038730] pcc_acpi: loading... 
May 29 18:02:35 maud-desktop dhcdbd: Started up. 
May 29 18:02:36 maud-desktop kernel: [  191.300598] ppdev: user-space parallel port driver 
May 29 18:02:37 maud-desktop kernel: [  192.298447] [drm] Initialized drm 1.1.0 20060810 
May 29 18:02:37 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 29 18:02:37 maud-desktop kernel: [  192.361896] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 18:02:37 maud-desktop kernel: [  192.362583] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 29 18:02:39 maud-desktop kernel: [  194.255937] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
May 29 18:02:39 maud-desktop kernel: [  194.255944] apm: overridden by ACPI. 
May 29 18:02:39 maud-desktop kernel: [  194.471010] Bluetooth: Core ver 2.11 
May 29 18:02:39 maud-desktop kernel: [  194.471075] NET: Registered protocol family 31 
May 29 18:02:39 maud-desktop kernel: [  194.471078] Bluetooth: HCI device and connection manager initialized 
May 29 18:02:39 maud-desktop kernel: [  194.471082] Bluetooth: HCI socket layer initialized 
May 29 18:02:39 maud-desktop kernel: [  194.517168] Bluetooth: L2CAP ver 2.8 
May 29 18:02:39 maud-desktop kernel: [  194.517174] Bluetooth: L2CAP socket layer initialized 
May 29 18:02:39 maud-desktop kernel: [  194.675303] Bluetooth: RFCOMM socket layer initialized 
May 29 18:02:39 maud-desktop kernel: [  194.675318] Bluetooth: RFCOMM TTY layer initialized 
May 29 18:02:39 maud-desktop kernel: [  194.675321] Bluetooth: RFCOMM ver 1.8 
May 29 18:02:48 maud-desktop kernel: [  203.309169] NET: Registered protocol family 10 
May 29 18:02:48 maud-desktop kernel: [  203.309273] lo: Disabled Privacy Extensions 
May 29 18:02:48 maud-desktop kernel: [  203.309332] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): starting (version 2.18.0.1), pid 5347 user 'armaud' 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 18:02:55 maud-desktop gconfd (armaud-5347): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 18:03:04 maud-desktop gconfd (armaud-5347): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0 
May 29 18:07:55 maud-desktop gconfd (root-5651): starting (version 2.18.0.1), pid 5651 user 'root' 
May 29 18:07:55 maud-desktop gconfd (root-5651): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 18:07:55 maud-desktop gconfd (root-5651): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1 
May 29 18:07:55 maud-desktop gconfd (root-5651): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 18:07:55 maud-desktop gconfd (root-5651): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 18:07:55 maud-desktop gconfd (root-5651): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 18:08:25 maud-desktop gconfd (root-5651): GConf server is not in use, shutting down. 
May 29 18:08:25 maud-desktop gconfd (root-5651): Exiting 
May 29 18:08:31 maud-desktop gconfd (armaud-5347): Exiting 
May 29 18:08:41 maud-desktop exiting on signal 15 
May 29 18:44:54 maud-desktop syslogd 1.4.1#20ubuntu4: restart. 
May 29 18:44:54 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic 
May 29 18:44:55 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic. 
May 29 18:44:55 maud-desktop kernel: Symbols match kernel version 2.6.20. 
May 29 18:44:55 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.  
May 29 18:44:55 maud-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 29 18:44:55 maud-desktop kernel: [    0.000000] sanitize start 
May 29 18:44:55 maud-desktop kernel: [    0.000000] sanitize end 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd40000 end: 000000001fe40000 type: 1 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe40000 size: 0000000000010000 end: 000000001fe50000 type: 3 
May 29 18:44:55 maud-desktop kernel: [    0.000000] copy_e820_map() start: 000000001fe50000 size: 00000000000b0000 end: 000000001ff00000 type: 4 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable) 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data) 
May 29 18:44:55 maud-desktop kernel: [    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] 0MB HIGHMEM available. 
May 29 18:44:55 maud-desktop kernel: [    0.000000] 510MB LOWMEM available. 
May 29 18:44:55 maud-desktop kernel: [    0.000000] found SMP MP-table at 000ff780 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Zone PFN ranges: 
May 29 18:44:55 maud-desktop kernel: [    0.000000]   DMA             0 ->     4096 
May 29 18:44:55 maud-desktop kernel: [    0.000000]   Normal       4096 ->   130624 
May 29 18:44:55 maud-desktop kernel: [    0.000000]   HighMem    130624 ->   130624 
May 29 18:44:55 maud-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges 
May 29 18:44:55 maud-desktop kernel: [    0.000000]     0:        0 ->   130624 
May 29 18:44:55 maud-desktop kernel: [    0.000000] DMI 2.3 present. 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Processor #0 15:4 APIC version 20 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1]) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1]) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000) 
May 29 18:44:55 maud-desktop kernel: [    0.000000] Detected 2400.150 MHz processor. 
May 29 18:44:55 maud-desktop kernel: [   22.357285] Built 1 zonelists.  Total pages: 129604 
May 29 18:44:55 maud-desktop kernel: [   22.357291] Kernel command line: root=UUID=26f348a8-8dfa-41c4-a4fa-f01bc32f963f ro quiet splash 
May 29 18:44:55 maud-desktop kernel: [   22.357493] Enabling fast FPU save and restore... done. 
May 29 18:44:55 maud-desktop kernel: [   22.357496] Enabling unmasked SIMD FPU exception support... done. 
May 29 18:44:55 maud-desktop kernel: [   22.357512] Initializing CPU#0 
May 29 18:44:55 maud-desktop kernel: [   22.357604] PID hash table entries: 2048 (order: 11, 8192 bytes) 
May 29 18:44:55 maud-desktop kernel: [   22.359027] Console: colour VGA+ 80x25 
May 29 18:44:55 maud-desktop kernel: [   22.359426] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
May 29 18:44:55 maud-desktop kernel: [   22.359752] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
May 29 18:44:55 maud-desktop kernel: [   22.370076] Memory: 506688k/522496k available (1992k kernel code, 15196k reserved, 893k data, 328k init, 0k highmem) 
May 29 18:44:55 maud-desktop kernel: [   22.370088] virtual kernel memory layout: 
May 29 18:44:55 maud-desktop kernel: [   22.370090]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
May 29 18:44:55 maud-desktop kernel: [   22.370091]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
May 29 18:44:55 maud-desktop kernel: [   22.370092]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
May 29 18:44:55 maud-desktop kernel: [   22.370094]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB) 
May 29 18:44:55 maud-desktop kernel: [   22.370095]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
May 29 18:44:55 maud-desktop kernel: [   22.370096]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
May 29 18:44:55 maud-desktop kernel: [   22.370098]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
May 29 18:44:55 maud-desktop kernel: [   22.370102] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
May 29 18:44:55 maud-desktop kernel: [   22.449468] Calibrating delay using timer specific routine.. 4804.10 BogoMIPS (lpj=9608208) 
May 29 18:44:55 maud-desktop kernel: [   22.449519] Security Framework v1.0.0 initialized 
May 29 18:44:55 maud-desktop kernel: [   22.449525] SELinux:  Disabled at boot. 
May 29 18:44:55 maud-desktop kernel: [   22.449544] Mount-cache hash table entries: 512 
May 29 18:44:55 maud-desktop kernel: [   22.449709] monitor/mwait feature present. 
May 29 18:44:55 maud-desktop kernel: [   22.449712] using mwait in idle threads. 
May 29 18:44:55 maud-desktop kernel: [   22.449719] CPU: Trace cache: 12K uops, L1 D cache: 16K 
May 29 18:44:55 maud-desktop kernel: [   22.449723] CPU: L2 cache: 1024K 
May 29 18:44:55 maud-desktop kernel: [   22.449726] CPU: Hyper-Threading is disabled 
May 29 18:44:55 maud-desktop kernel: [   22.449741] Compat vDSO mapped to ffffe000. 
May 29 18:44:55 maud-desktop kernel: [   22.449746] Remapping vsyscall page to ffffe000 
May 29 18:44:55 maud-desktop kernel: [   22.449764] Checking 'hlt' instruction... OK. 
May 29 18:44:55 maud-desktop kernel: [   22.465549] SMP alternatives: switching to UP code 
May 29 18:44:55 maud-desktop kernel: [   22.465727] Freeing SMP alternatives: 11k freed 
May 29 18:44:55 maud-desktop kernel: [   22.465956] Early unpacking initramfs... done 
May 29 18:44:55 maud-desktop kernel: [   22.816250] ACPI: Core revision 20060707 
May 29 18:44:55 maud-desktop kernel: [   22.816424] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
May 29 18:44:55 maud-desktop kernel: [   22.818995] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01 
May 29 18:44:55 maud-desktop kernel: [   22.819042] Total of 1 processors activated (4804.10 BogoMIPS). 
May 29 18:44:55 maud-desktop kernel: [   22.819179] ENABLING IO-APIC IRQs 
May 29 18:44:55 maud-desktop kernel: [   22.819370] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
May 29 18:44:55 maud-desktop kernel: [   22.964720] Brought up 1 CPUs 
May 29 18:44:55 maud-desktop kernel: [   22.964999] Booting paravirtualized kernel on bare hardware 
May 29 18:44:55 maud-desktop kernel: [   22.965079] Time: 18:42:05  Date: 04/29/107 
May 29 18:44:55 maud-desktop kernel: [   22.965110] NET: Registered protocol family 16 
May 29 18:44:55 maud-desktop kernel: [   22.965214] EISA bus registered 
May 29 18:44:55 maud-desktop kernel: [   22.965220] ACPI: bus type pci registered 
May 29 18:44:55 maud-desktop kernel: [   22.965293] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1 
May 29 18:44:55 maud-desktop kernel: [   22.965296] PCI: Using configuration type 1 
May 29 18:44:55 maud-desktop kernel: [   22.965298] Setting up standard PCI resources 
May 29 18:44:55 maud-desktop kernel: [   22.979534] ACPI: Interpreter enabled 
May 29 18:44:55 maud-desktop kernel: [   22.979538] ACPI: Using IOAPIC for interrupt routing 
May 29 18:44:55 maud-desktop kernel: [   22.979941] ACPI: PCI Root Bridge [PCI0] (0000:00) 
May 29 18:44:55 maud-desktop kernel: [   22.980573] * The chipset may have PM-Timer Bug. Due to workarounds for a bug, 
May 29 18:44:55 maud-desktop kernel: [   22.980575] * this clock source is slow. If you are sure your timer does not have 
May 29 18:44:55 maud-desktop kernel: [   22.980577] * this bug, please use "acpi_pm_good" to disable the workaround 
May 29 18:44:55 maud-desktop kernel: [   22.980626] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
May 29 18:44:55 maud-desktop kernel: [   22.980630] PCI quirk: region 0480-04bf claimed by ICH4 GPIO 
May 29 18:44:55 maud-desktop kernel: [   22.980884] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling 
May 29 18:44:55 maud-desktop kernel: [   22.980960] PCI: Transparent bridge - 0000:00:1e.0 
May 29 18:44:55 maud-desktop kernel: [   22.984982] ACPI: Power Resource [URP1] (off) 
May 29 18:44:55 maud-desktop kernel: [   22.985066] ACPI: Power Resource [FDDP] (off) 
May 29 18:44:55 maud-desktop kernel: [   22.985150] ACPI: Power Resource [LPTP] (off) 
May 29 18:44:55 maud-desktop kernel: [   22.988076] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.988503] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.988964] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.989385] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.989804] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.990220] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 18:44:55 maud-desktop kernel: [   22.990639] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
May 29 18:44:55 maud-desktop kernel: [   22.991060] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
May 29 18:44:55 maud-desktop kernel: [   22.991466] Linux Plug and Play Support v0.97 (c) Adam Belay 
May 29 18:44:55 maud-desktop kernel: [   22.991484] pnp: PnP ACPI init 
May 29 18:44:55 maud-desktop kernel: [   22.995988] pnp: PnP ACPI: found 13 devices 
May 29 18:44:55 maud-desktop kernel: [   22.995994] PnPBIOS: Disabled by ACPI PNP 
May 29 18:44:55 maud-desktop kernel: [   22.996051] PCI: Using ACPI for IRQ routing 
May 29 18:44:55 maud-desktop kernel: [   22.996055] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
May 29 18:44:55 maud-desktop kernel: [   22.998962] NET: Registered protocol family 8 
May 29 18:44:55 maud-desktop kernel: [   22.998965] NET: Registered protocol family 20 
May 29 18:44:55 maud-desktop kernel: [   23.000276] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved 
May 29 18:44:55 maud-desktop kernel: [   23.000281] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved 
May 29 18:44:55 maud-desktop kernel: [   23.000284] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved 
May 29 18:44:55 maud-desktop kernel: [   23.000671] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0 
May 29 18:44:55 maud-desktop kernel: [   23.000681] PCI: Bridge: 0000:00:1e.0 
May 29 18:44:55 maud-desktop kernel: [   23.000685]   IO window: d000-dfff 
May 29 18:44:55 maud-desktop kernel: [   23.000692]   MEM window: ff800000-ff8fffff 
May 29 18:44:55 maud-desktop kernel: [   23.000697]   PREFETCH window: eaa00000-eaafffff 
May 29 18:44:55 maud-desktop kernel: [   23.000740] NET: Registered protocol family 2 
May 29 18:44:55 maud-desktop kernel: [   23.040645] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
May 29 18:44:55 maud-desktop kernel: [   23.040736] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
May 29 18:44:55 maud-desktop kernel: [   23.040846] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
May 29 18:44:55 maud-desktop kernel: [   23.040896] TCP: Hash tables configured (established 16384 bind 8192) 
May 29 18:44:55 maud-desktop kernel: [   23.040899] TCP reno registered 
May 29 18:44:55 maud-desktop kernel: [   23.052686] checking if image is initramfs... it is 
May 29 18:44:55 maud-desktop kernel: [   23.739998] Freeing initrd memory: 7005k freed 
May 29 18:44:55 maud-desktop kernel: [   23.740603] audit: initializing netlink socket (disabled) 
May 29 18:44:55 maud-desktop kernel: [   23.740622] audit(1180464126.464:1): initialized 
May 29 18:44:55 maud-desktop kernel: [   23.740769] VFS: Disk quotas dquot_6.5.1 
May 29 18:44:55 maud-desktop kernel: [   23.740793] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
May 29 18:44:55 maud-desktop kernel: [   23.740852] io scheduler noop registered 
May 29 18:44:55 maud-desktop kernel: [   23.740856] io scheduler anticipatory registered 
May 29 18:44:55 maud-desktop kernel: [   23.740858] io scheduler deadline registered 
May 29 18:44:55 maud-desktop kernel: [   23.740869] io scheduler cfq registered (default) 
May 29 18:44:55 maud-desktop kernel: [   23.741157] isapnp: Scanning for PnP cards... 
May 29 18:44:55 maud-desktop kernel: [   24.092708] isapnp: No Plug & Play device found 
May 29 18:44:55 maud-desktop kernel: [   24.123704] Real Time Clock Driver v1.12ac 
May 29 18:44:55 maud-desktop kernel: [   24.123769] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
May 29 18:44:55 maud-desktop kernel: [   24.123895] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 18:44:55 maud-desktop kernel: [   24.124714] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
May 29 18:44:55 maud-desktop kernel: [   24.125010] mice: PS/2 mouse device common for all mice 
May 29 18:44:55 maud-desktop kernel: [   24.125721] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
May 29 18:44:55 maud-desktop kernel: [   24.126004] input: Macintosh mouse button emulation as /class/input/input0 
May 29 18:44:55 maud-desktop kernel: [   24.126052] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
May 29 18:44:55 maud-desktop kernel: [   24.126057] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
May 29 18:44:55 maud-desktop kernel: [   24.126321] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
May 29 18:44:55 maud-desktop kernel: [   24.129934] serio: i8042 KBD port at 0x60,0x64 irq 1 
May 29 18:44:55 maud-desktop kernel: [   24.129942] serio: i8042 AUX port at 0x60,0x64 irq 12 
May 29 18:44:55 maud-desktop kernel: [   24.130113] EISA: Probing bus 0 at eisa.0 
May 29 18:44:55 maud-desktop kernel: [   24.130154] EISA: Detected 0 cards. 
May 29 18:44:55 maud-desktop kernel: [   24.160207] TCP cubic registered

---

### Post by armaud on 2007-05-29
May 29 18:44:55 maud-desktop kernel: [   24.160216] NET: Registered protocol family 1 
May 29 18:44:55 maud-desktop kernel: [   24.160242] Using IPI No-Shortcut mode 
May 29 18:44:55 maud-desktop kernel: [   24.160319] ACPI: (supports S0 S1 S4 S5) 
May 29 18:44:55 maud-desktop kernel: [   24.160368]   Magic number: 7:766:747 
May 29 18:44:55 maud-desktop kernel: [   24.160890] Freeing unused kernel memory: 328k freed 
May 29 18:44:55 maud-desktop kernel: [   24.162831] Time: tsc clocksource has been installed. 
May 29 18:44:55 maud-desktop kernel: [   24.180857] input: AT Translated Set 2 keyboard as /class/input/input1 
May 29 18:44:55 maud-desktop kernel: [   25.500817] Capability LSM initialized 
May 29 18:44:55 maud-desktop kernel: [   25.843881] ACPI: Processor [CPU1] (supports 8 throttling states) 
May 29 18:44:55 maud-desktop kernel: [   25.843893] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
May 29 18:44:55 maud-desktop kernel: [   35.678453] usbcore: registered new interface driver usbfs 
May 29 18:44:55 maud-desktop kernel: [   35.678481] usbcore: registered new interface driver hub 
May 29 18:44:55 maud-desktop kernel: [   35.678509] usbcore: registered new device driver usb 
May 29 18:44:55 maud-desktop kernel: [   35.679536] USB Universal Host Controller Interface driver v3.0 
May 29 18:44:55 maud-desktop kernel: [   35.679593] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 18:44:55 maud-desktop kernel: [   35.679611] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
May 29 18:44:55 maud-desktop kernel: [   35.679786] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
May 29 18:44:55 maud-desktop kernel: [   35.679814] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800 
May 29 18:44:55 maud-desktop kernel: [   35.679932] usb usb1: configuration #1 chosen from 1 choice 
May 29 18:44:55 maud-desktop kernel: [   35.679963] hub 1-0:1.0: USB hub found 
May 29 18:44:55 maud-desktop kernel: [   35.679971] hub 1-0:1.0: 2 ports detected 
May 29 18:44:55 maud-desktop kernel: [   35.784646] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17 
May 29 18:44:55 maud-desktop kernel: [   35.784666] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
May 29 18:44:55 maud-desktop kernel: [   35.784698] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
May 29 18:44:55 maud-desktop kernel: [   35.784729] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880 
May 29 18:44:55 maud-desktop kernel: [   35.784835] usb usb2: configuration #1 chosen from 1 choice 
May 29 18:44:55 maud-desktop kernel: [   35.784866] hub 2-0:1.0: USB hub found 
May 29 18:44:55 maud-desktop kernel: [   35.784874] hub 2-0:1.0: 2 ports detected 
May 29 18:44:55 maud-desktop kernel: [   35.836621] SCSI subsystem initialized 
May 29 18:44:55 maud-desktop kernel: [   35.888462] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
May 29 18:44:55 maud-desktop kernel: [   35.888482] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
May 29 18:44:55 maud-desktop kernel: [   35.888512] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
May 29 18:44:55 maud-desktop kernel: [   35.888542] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00 
May 29 18:44:55 maud-desktop kernel: [   35.888653] usb usb3: configuration #1 chosen from 1 choice 
May 29 18:44:55 maud-desktop kernel: [   35.888685] hub 3-0:1.0: USB hub found 
May 29 18:44:55 maud-desktop kernel: [   35.888695] hub 3-0:1.0: 2 ports detected 
May 29 18:44:55 maud-desktop kernel: [   35.990457] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI 
May 29 18:44:55 maud-desktop kernel: [   35.990462] e100: Copyright(c) 1999-2006 Intel Corporation 
May 29 18:44:55 maud-desktop kernel: [   35.993072] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19 
May 29 18:44:55 maud-desktop kernel: [   35.993095] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
May 29 18:44:55 maud-desktop kernel: [   35.993131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
May 29 18:44:55 maud-desktop kernel: [   35.993176] ehci_hcd 0000:00:1d.7: debug port 1 
May 29 18:44:55 maud-desktop kernel: [   35.993196] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00 
May 29 18:44:55 maud-desktop kernel: [   35.997066] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
May 29 18:44:55 maud-desktop kernel: [   35.997157] usb usb4: configuration #1 chosen from 1 choice 
May 29 18:44:55 maud-desktop kernel: [   35.997196] hub 4-0:1.0: USB hub found 
May 29 18:44:55 maud-desktop kernel: [   35.997207] hub 4-0:1.0: 6 ports detected 
May 29 18:44:55 maud-desktop kernel: [   36.024171] usb 1-1: new full speed USB device using uhci_hcd and address 2 
May 29 18:44:55 maud-desktop kernel: [   36.106754] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
May 29 18:44:55 maud-desktop kernel: [   36.106761] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18 
May 29 18:44:55 maud-desktop kernel: [   36.106844] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
May 29 18:44:55 maud-desktop kernel: [   36.106882] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
May 29 18:44:55 maud-desktop kernel: [   36.106904] scsi0 : ata_piix 
May 29 18:44:55 maud-desktop kernel: [   36.280045] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 18:44:55 maud-desktop kernel: [   36.280051] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100 
May 29 18:44:55 maud-desktop kernel: [   36.280055] ata1.00: 78165360 sectors, multi 16: LBA  
May 29 18:44:55 maud-desktop kernel: [   36.280059] ata1.01: ATA-4: QUANTUM FIREBALL EL5.1A, A08.1100, max UDMA/33 
May 29 18:44:55 maud-desktop kernel: [   36.280063] ata1.01: 10018890 sectors, multi 16: LBA  
May 29 18:44:55 maud-desktop kernel: [   36.280069] ata1.00: limited to UDMA/33 due to 40-wire cable 
May 29 18:44:55 maud-desktop kernel: [   36.292078] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360 
May 29 18:44:55 maud-desktop kernel: [   36.292085] ata1.00: configured for UDMA/33 
May 29 18:44:55 maud-desktop kernel: [   36.303927] ata1.01: configured for UDMA/33 
May 29 18:44:55 maud-desktop kernel: [   36.303948] scsi1 : ata_piix 
May 29 18:44:55 maud-desktop kernel: [   36.623388] ata2.00: ATAPI, max UDMA/33 
May 29 18:44:55 maud-desktop kernel: [   36.779056] usb 1-1: new full speed USB device using uhci_hcd and address 3 
May 29 18:44:55 maud-desktop kernel: [   36.787156] ata2.00: configured for UDMA/33 
May 29 18:44:55 maud-desktop kernel: [   36.790940] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5 
May 29 18:44:55 maud-desktop kernel: [   36.794923] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A08. PQ: 0 ANSI: 5 
May 29 18:44:55 maud-desktop kernel: [   36.795908] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS58 PQ: 0 ANSI: 5 
May 29 18:44:55 maud-desktop kernel: [   36.797514] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20 
May 29 18:44:55 maud-desktop kernel: [   36.817193] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:11:11:56:8B:A4 
May 29 18:44:55 maud-desktop kernel: [   37.002886] usb 1-1: configuration #1 chosen from 2 choices 
May 29 18:44:55 maud-desktop kernel: [   37.234225] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 18:44:55 maud-desktop kernel: [   37.234708] sda: Write Protect is off 
May 29 18:44:55 maud-desktop kernel: [   37.238740] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:44:55 maud-desktop kernel: [   37.242699] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB) 
May 29 18:44:55 maud-desktop kernel: [   37.246218] sda: Write Protect is off 
May 29 18:44:55 maud-desktop kernel: [   37.250193] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:44:55 maud-desktop kernel: [   37.250197]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > 
May 29 18:44:55 maud-desktop kernel: [   37.329178] sd 0:0:0:0: Attached scsi disk sda 
May 29 18:44:55 maud-desktop kernel: [   37.330076] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 18:44:55 maud-desktop kernel: [   37.330093] sdb: Write Protect is off 
May 29 18:44:55 maud-desktop kernel: [   37.330117] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:44:55 maud-desktop kernel: [   37.330162] SCSI device sdb: 10018890 512-byte hdwr sectors (5130 MB) 
May 29 18:44:55 maud-desktop kernel: [   37.330175] sdb: Write Protect is off 
May 29 18:44:55 maud-desktop kernel: [   37.330199] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
May 29 18:44:55 maud-desktop kernel: [   37.330202]  sdb: sdb1 sdb2 < sdb5 > 
May 29 18:44:55 maud-desktop kernel: [   37.360249] sd 0:0:1:0: Attached scsi disk sdb 
May 29 18:44:55 maud-desktop kernel: [   37.365566] sr0: scsi3-mmc drive: 66x/52x writer cd/rw xa/form2 cdda tray 
May 29 18:44:55 maud-desktop kernel: [   37.365571] Uniform CD-ROM driver Revision: 3.20 
May 29 18:44:55 maud-desktop kernel: [   37.370189] sd 0:0:0:0: Attached scsi generic sg0 type 0 
May 29 18:44:55 maud-desktop kernel: [   37.370215] sd 0:0:1:0: Attached scsi generic sg1 type 0 
May 29 18:44:55 maud-desktop kernel: [   37.370242] sr 1:0:0:0: Attached scsi generic sg2 type 5 
May 29 18:44:55 maud-desktop kernel: [   39.141715] Attempting manual resume 
May 29 18:44:55 maud-desktop kernel: [   39.754267] kjournald starting.  Commit interval 5 seconds 
May 29 18:44:55 maud-desktop kernel: [   39.754279] EXT3-fs: mounted filesystem with ordered data mode. 
May 29 18:44:55 maud-desktop kernel: [  167.701328] NET: Registered protocol family 17 
May 29 18:44:55 maud-desktop kernel: [  176.503709] i810_smbus 0000:00:02.0: i810/i815 i2c device found. 
May 29 18:44:55 maud-desktop kernel: [  176.572521] Linux agpgart interface v0.102 (c) Dave Jones 
May 29 18:44:55 maud-desktop kernel: [  176.586795] agpgart: Detected an Intel 845G Chipset. 
May 29 18:44:55 maud-desktop kernel: [  176.587040] agpgart: Detected 892K stolen memory. 
May 29 18:44:55 maud-desktop kernel: [  176.601608] agpgart: AGP aperture is 128M @ 0xf0000000 
May 29 18:44:55 maud-desktop kernel: [  176.994889] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
May 29 18:44:55 maud-desktop kernel: [  177.008263] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
May 29 18:44:55 maud-desktop kernel: [  177.019989] intel_rng: Firmware space is locked read-only. If you can't or 
May 29 18:44:55 maud-desktop kernel: [  177.019992] intel_rng: don't want to disable this in firmware setup, and if 
May 29 18:44:55 maud-desktop kernel: [  177.019993] intel_rng: you are certain that your system has a functional 
May 29 18:44:55 maud-desktop kernel: [  177.019995] intel_rng: RNG, try using the 'no_fwh_detect' option. 
May 29 18:44:55 maud-desktop kernel: [  177.089669] iTCO_vendor_support: vendor-support=0 
May 29 18:44:55 maud-desktop kernel: [  177.092121] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
May 29 18:44:55 maud-desktop kernel: [  177.092229] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460) 
May 29 18:44:55 maud-desktop kernel: [  177.092277] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
May 29 18:44:55 maud-desktop kernel: [  177.518620] input: PC Speaker as /class/input/input2 
May 29 18:44:55 maud-desktop kernel: [  177.862518] parport: PnPBIOS parport detected. 
May 29 18:44:55 maud-desktop kernel: [  177.862544] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 29 18:44:55 maud-desktop kernel: [  178.036549] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
May 29 18:44:55 maud-desktop kernel: [  178.538072] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21 
May 29 18:44:55 maud-desktop kernel: [  178.855162] intel8x0_measure_ac97_clock: measured 55149 usecs 
May 29 18:44:55 maud-desktop kernel: [  178.855167] intel8x0: clocking to 48000 
May 29 18:44:55 maud-desktop kernel: [  181.075918] fuse init (API version 7.8) 
May 29 18:44:55 maud-desktop kernel: [  181.192805] lp0: using parport0 (interrupt-driven). 
May 29 18:44:55 maud-desktop kernel: [  181.222213] Adding 265032k swap on /dev/disk/by-uuid/a026fb52-8618-42ff-b153-9d0e92f618a2.  Priority:-1 extents:1 across:265032k 
May 29 18:44:55 maud-desktop kernel: [  182.038174] EXT3 FS on sdb1, internal journal 
May 29 18:44:55 maud-desktop kernel: [  190.663984] input: Power Button (FF) as /class/input/input4 
May 29 18:44:55 maud-desktop kernel: [  190.668745] ACPI: Power Button (FF) [PWRF] 
May 29 18:44:55 maud-desktop kernel: [  190.704236] input: Sleep Button (CM) as /class/input/input5 
May 29 18:44:55 maud-desktop kernel: [  190.708966] ACPI: Sleep Button (CM) [SLPB] 
May 29 18:44:55 maud-desktop kernel: [  190.723660] No dock devices found. 
May 29 18:44:55 maud-desktop kernel: [  190.833723] Using specific hotkey driver 
May 29 18:44:55 maud-desktop kernel: [  190.942003] pcc_acpi: loading... 
May 29 18:44:58 maud-desktop dhcdbd: Started up. 
May 29 18:44:59 maud-desktop kernel: [  196.239101] ppdev: user-space parallel port driver 
May 29 18:45:01 maud-desktop hpiod: 1.7.3 accepting connections at 2208...  
May 29 18:45:01 maud-desktop kernel: [  198.187297] [drm] Initialized drm 1.1.0 20060810 
May 29 18:45:01 maud-desktop kernel: [  198.284219] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
May 29 18:45:01 maud-desktop kernel: [  198.284808] [drm] Initialized i915 1.6.0 20060119 on minor 0 
May 29 18:45:02 maud-desktop kernel: [  199.631840] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
May 29 18:45:02 maud-desktop kernel: [  199.631847] apm: overridden by ACPI. 
May 29 18:45:03 maud-desktop kernel: [  199.902164] Bluetooth: Core ver 2.11 
May 29 18:45:03 maud-desktop kernel: [  199.902234] NET: Registered protocol family 31 
May 29 18:45:03 maud-desktop kernel: [  199.902237] Bluetooth: HCI device and connection manager initialized 
May 29 18:45:03 maud-desktop kernel: [  199.902241] Bluetooth: HCI socket layer initialized 
May 29 18:45:03 maud-desktop kernel: [  199.947993] Bluetooth: L2CAP ver 2.8 
May 29 18:45:03 maud-desktop kernel: [  199.947998] Bluetooth: L2CAP socket layer initialized 
May 29 18:45:03 maud-desktop kernel: [  200.139987] Bluetooth: RFCOMM socket layer initialized 
May 29 18:45:03 maud-desktop kernel: [  200.140003] Bluetooth: RFCOMM TTY layer initialized 
May 29 18:45:03 maud-desktop kernel: [  200.140005] Bluetooth: RFCOMM ver 1.8 
May 29 18:45:14 maud-desktop kernel: [  211.358103] NET: Registered protocol family 10 
May 29 18:45:14 maud-desktop kernel: [  211.358218] lo: Disabled Privacy Extensions 
May 29 18:45:14 maud-desktop kernel: [  211.358277] ADDRCONF(NETDEV_UP): eth0: link is not ready 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): starting (version 2.18.0.1), pid 5369 user 'armaud' 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 29 18:46:30 maud-desktop gconfd (armaud-5369): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 29 18:46:39 maud-desktop gconfd (armaud-5369): Resolved address "xml:readwrite:/home/ar

---

### Post by armaud on 2007-05-29
As you can see it seems that the kernel restarts 2 to 3 times. If you can find the problem then please do reply here. Thanks for going through the log anyway. I dont know if it should be so long right after boot up.

---

### Post by santy_kushwaha on 2007-05-29
hey what i will do is tha try to reinstal because when i was trying to instal i faced pretty much same problems that it takes time to load and don't detect network connections i reinstal and then tried  i might work 

hope for the best

---

