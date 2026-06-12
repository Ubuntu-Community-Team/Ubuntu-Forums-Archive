---
title: "Grabadora de DVD Sony no abre"
date: 2007-10-14
forum: Argentina Team
---

### Post by margori on 2007-10-14
Hola amigos:
Espero me puedan ayudar con mi problemilla:
La cosa es que tengo Ubuntu 7.04 instalado, con Kernel actuaiizado 2.6.20-16-generic, Pero luego no me reconoce la grabadora de dvd. No se como buscar mas especificamente el problema ya que en el log de sistema sale las siguientes lineas:

[ 3645.452000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 3645.452000] hdb: status error: error=0x00 { }
[ 3645.452000] ide: failed opcode was: unknown
[ 3645.452000] hdb: drive not ready for command

y se repiten hasta el cansancio.

Lo mas cerca que pude acercarme al error fueron las siguientes lineas:

Oct 12 00:30:52 pcmaguila kernel: [    5.580000] hda: Maxtor 6E040L0, ATA DISK drive
Oct 12 00:30:52 pcmaguila kernel: [    6.028000] hdb: SONY DVD RW DRU-810A, ATAPI CD/DVD-ROM drive
Oct 12 00:30:52 pcmaguila kernel: [    6.032000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[B]Oct 12 00:30:52 pcmaguila kernel: [   36.048000] hdb: lost interrupt
Oct 12 00:30:52 pcmaguila kernel: [   36.048000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 12 00:30:52 pcmaguila kernel: [   36.048000] hdb: task_in_intr: error=0x00 { }
Oct 12 00:30:52 pcmaguila kernel: [   36.048000] ide: failed opcode was: 0xa1[/B]
Oct 12 00:30:52 pcmaguila kernel: [   36.056000] hda: max request size: 128KiB
Oct 12 00:30:52 pcmaguila kernel: [   36.056000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63
Oct 12 00:30:52 pcmaguila kernel: [   36.060000] hda: cache flushes supported
Oct 12 00:30:52 pcmaguila kernel: [   36.060000]  hda: hda1 hda2 < hda5 > hda3 hda4
Oct 12 00:30:52 pcmaguila kernel: [   36.300000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 12 00:30:52 pcmaguila kernel: [   36.300000] hdb: status error: error=0x00 { }
Oct 12 00:30:52 pcmaguila kernel: [   36.300000] ide: failed opcode was: unknown
Oct 12 00:30:52 pcmaguila kernel: [   36.300000] hdb: ATAPI CD-ROM drive, 0kB Cache, UDMA(33)
Oct 12 00:30:52 pcmaguila kernel: [   36.300000] Uniform CD-ROM driver Revision: 3.20
Oct 12 00:30:52 pcmaguila kernel: [   36.500000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 12 00:30:52 pcmaguila kernel: [   36.500000] hdb: status error: error=0x00 { }
Oct 12 00:30:52 pcmaguila kernel: [   36.500000] ide: failed opcode was: unknown
Oct 12 00:30:52 pcmaguila kernel: [   36.716000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 12 00:30:52 pcmaguila kernel: [   36.716000] hdb: status error: error=0x00 { }
Oct 12 00:30:52 pcmaguila kernel: [   36.716000] ide: failed opcode was: unknown

y asi...

Como veran tengo un disco IDE Maestro y la grabadora IDE de esclava.

Sobre este error no he encontrado nada y no se que camino seguir. Que me sugieren.

Gracias.

---

### Post by faktorqm on 2007-10-16
Hola, yo tengo la misma grabadora de DVD, es un caño, pero tiene toooodos los problemas. 

seguro nunca le cambiaste el firmware, asi que aca te dejo los links:

instrucciones: [http://sony.storagesupport.com/dvdrw/downloads/810AFW10F/Firmware1_0fUpdate.htm](http://sony.storagesupport.com/dvdrw/downloads/810AFW10F/Firmware1_0fUpdate.htm)

firmware: [http://sony.storagesupport.com/legalagreement.zulu?dlid=dvdrw/downloads/810AFW10F/810A_1.0f.zip](http://sony.storagesupport.com/legalagreement.zulu?dlid=dvdrw/downloads/810AFW10F/810A_1.0f.zip)

esto lo saque de la pagina oficial de sony:

[http://sony.storagesupport.com/dvdrw/dru810adwn.htm](http://sony.storagesupport.com/dvdrw/dru810adwn.htm)

espero que te haya servido. fijate que ahi solucionan los problemas. espero que te haya servido. salu2!!

---

### Post by margori on 2007-10-16
Gracias por el dato del firmware. Lo instale desde WXP sin problemas, pero no soluciono mi problema con ubuntu.

Estuve buscando soporte por parte de Sony, pero no me dieron bola. Nada.

Asi que sigo mas o menos en la situación anterior.

Paso un listado completo de /var/log/messages, a ver si esta oculto algun dato que no he dicho. He omitido las lineas que se repetian con puntos suspensivos. Por otro lado, esto puede ser un bug?

Oct 16 16:20:55 pcmaguila syslogd 1.4.1#20ubuntu4: restart.
Oct 16 16:20:55 pcmaguila kernel: Inspecting /boot/System.map-2.6.20-16-generic
Oct 16 16:20:55 pcmaguila kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Oct 16 16:20:55 pcmaguila kernel: Symbols match kernel version 2.6.20.
Oct 16 16:20:55 pcmaguila kernel: No module symbols loaded - kernel modules not enabled. 
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] sanitize start
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] sanitize end
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() type is E820_RAM
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003dde0000 end: 000000003dee0000 type: 1
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() type is E820_RAM
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 000000003dee0000 size: 0000000000003000 end: 000000003dee3000 type: 4
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 000000003dee3000 size: 000000000000d000 end: 000000003def0000 type: 3
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 000000003def0000 size: 0000000000010000 end: 000000003df00000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 000000003e000000 size: 0000000002000000 end: 0000000040000000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003dee0000 (usable)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 000000003dee0000 - 000000003dee3000 (ACPI NVS)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 000000003dee3000 - 000000003def0000 (ACPI data)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 000000003def0000 - 000000003df00000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 000000003e000000 - 0000000040000000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] 94MB HIGHMEM available.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] 896MB LOWMEM available.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] found SMP MP-table at 000f3a00
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Zone PFN ranges:
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]   DMA             0 ->     4096
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]   Normal       4096 ->   229376
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]   HighMem    229376 ->   253664
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 16 16:20:55 pcmaguila kernel: [    0.000000]     0:        0 ->   253664
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] DMI 2.2 present.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Processor #0 15:11 APIC version 16
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Processor #1 15:11 APIC version 16
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Oct 16 16:20:55 pcmaguila kernel: [    0.000000] Detected 2109.788 MHz processor.
Oct 16 16:20:55 pcmaguila kernel: [   15.395772] Built 1 zonelists.  Total pages: 251683
Oct 16 16:20:55 pcmaguila kernel: [   15.395775] Kernel command line: root=UUID=651c2132-f0e3-473b-9cfa-b9b4aa449f7d ro quiet splash locale=es_ES
Oct 16 16:20:55 pcmaguila kernel: [   15.395905] Enabling fast FPU save and restore... done.
Oct 16 16:20:55 pcmaguila kernel: [   15.395907] Enabling unmasked SIMD FPU exception support... done.
Oct 16 16:20:55 pcmaguila kernel: [   15.395914] Initializing CPU#0
Oct 16 16:20:55 pcmaguila kernel: [   15.395964] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 16 16:20:55 pcmaguila kernel: [   15.398992] Console: colour VGA+ 80x25
Oct 16 16:20:55 pcmaguila kernel: [   15.399338] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 16 16:20:55 pcmaguila kernel: [   15.399695] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 16 16:20:55 pcmaguila kernel: [   15.417157] Memory: 994812k/1014656k available (1993k kernel code, 19252k reserved, 900k data, 328k init, 97152k highmem)
Oct 16 16:20:55 pcmaguila kernel: [   15.417166] virtual kernel memory layout:
Oct 16 16:20:55 pcmaguila kernel: [   15.417167]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417168]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417169]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417170]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417171]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417173]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417174]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
Oct 16 16:20:55 pcmaguila kernel: [   15.417176] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 16 16:20:55 pcmaguila kernel: [   15.495900] Calibrating delay using timer specific routine.. 4223.87 BogoMIPS (lpj=8447742)
Oct 16 16:20:55 pcmaguila kernel: [   15.495936] Security Framework v1.0.0 initialized
Oct 16 16:20:55 pcmaguila kernel: [   15.495943] SELinux:  Disabled at boot.
Oct 16 16:20:55 pcmaguila kernel: [   15.495956] Mount-cache hash table entries: 512
Oct 16 16:20:55 pcmaguila kernel: [   15.496081] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 16 16:20:55 pcmaguila kernel: [   15.496083] CPU: L2 Cache: 512K (64 bytes/line)
Oct 16 16:20:55 pcmaguila kernel: [   15.496085] CPU 0(2) -> Core 0
Oct 16 16:20:55 pcmaguila kernel: [   15.496096] Compat vDSO mapped to ffffe000.
Oct 16 16:20:55 pcmaguila kernel: [   15.496100] Remapping vsyscall page to ffffe000
Oct 16 16:20:55 pcmaguila kernel: [   15.496109] Checking 'hlt' instruction... OK.
Oct 16 16:20:55 pcmaguila kernel: [   15.512012] SMP alternatives: switching to UP code
Oct 16 16:20:55 pcmaguila kernel: [   15.512357] Early unpacking initramfs... done
Oct 16 16:20:55 pcmaguila kernel: [   15.777009] ACPI: Core revision 20060707
Oct 16 16:20:55 pcmaguila kernel: [   15.779919] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Oct 16 16:20:55 pcmaguila kernel: [   15.783958] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Oct 16 16:20:55 pcmaguila kernel: [   15.783978] SMP alternatives: switching to SMP code
Oct 16 16:20:55 pcmaguila kernel: [   15.784083] Booting processor 1/1 eip 3000
Oct 16 16:20:55 pcmaguila kernel: [   15.794481] Initializing CPU#1
Oct 16 16:20:55 pcmaguila kernel: [   15.871834] Calibrating delay using timer specific routine.. 4219.73 BogoMIPS (lpj=8439474)
Oct 16 16:20:55 pcmaguila kernel: [   15.871846] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 16 16:20:55 pcmaguila kernel: [   15.871848] CPU: L2 Cache: 512K (64 bytes/line)
Oct 16 16:20:55 pcmaguila kernel: [   15.871850] CPU 1(2) -> Core 1
Oct 16 16:20:55 pcmaguila kernel: [   15.871832] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Oct 16 16:20:55 pcmaguila kernel: [   15.871844] Total of 2 processors activated (8443.60 BogoMIPS).
Oct 16 16:20:55 pcmaguila kernel: [   15.872079] ENABLING IO-APIC IRQs
Oct 16 16:20:55 pcmaguila kernel: [   15.872315] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Oct 16 16:20:55 pcmaguila kernel: [   16.019537] checking TSC synchronization across 2 CPUs: 
Oct 16 16:20:55 pcmaguila kernel: [    0.000001] CPU#0 had -101 usecs TSC skew, fixed it up.
Oct 16 16:20:55 pcmaguila kernel: [    0.000003] CPU#1 had 101 usecs TSC skew, fixed it up.
Oct 16 16:20:55 pcmaguila kernel: [    0.003997] Brought up 2 CPUs
Oct 16 16:20:55 pcmaguila kernel: [    0.037944] migration_cost=261
Oct 16 16:20:55 pcmaguila kernel: [    0.038161] Booting paravirtualized kernel on bare hardware
Oct 16 16:20:55 pcmaguila kernel: [    0.038232] Time: 16:19:53  Date: 09/16/107
Oct 16 16:20:55 pcmaguila kernel: [    0.038260] NET: Registered protocol family 16
Oct 16 16:20:55 pcmaguila kernel: [    0.038331] EISA bus registered
Oct 16 16:20:55 pcmaguila kernel: [    0.038334] ACPI: bus type pci registered
Oct 16 16:20:55 pcmaguila kernel: [    0.043971] PCI: PCI BIOS revision 3.00 entry at 0xfa7b0, last bus=4
Oct 16 16:20:55 pcmaguila kernel: [    0.043973] PCI: Using configuration type 1
Oct 16 16:20:55 pcmaguila kernel: [    0.043975] Setting up standard PCI resources
Oct 16 16:20:55 pcmaguila kernel: [    0.052843] ACPI: Interpreter enabled
Oct 16 16:20:55 pcmaguila kernel: [    0.052846] ACPI: Using IOAPIC for interrupt routing
Oct 16 16:20:55 pcmaguila kernel: [    0.053333] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 16 16:20:55 pcmaguila kernel: [    0.055874] PCI: Transparent bridge - 0000:00:04.0
Oct 16 16:20:55 pcmaguila kernel: [    0.106238] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.106531] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.106821] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.107115] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.107406] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.107698] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.107990] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.108280] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.108570] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.108860] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.109151] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.109445] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.109738] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.110032] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.110323] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.110617] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.110908] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.111202] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Oct 16 16:20:55 pcmaguila kernel: [    0.111492] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.111861] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.112225] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.112587] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.112948] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.113309] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.113670] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.114031] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.114392] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.114757] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.115119] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.115483] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.115845] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.116209] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.116570] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.116930] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.117290] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.117650] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.118010] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.118371] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Oct 16 16:20:55 pcmaguila kernel: [    0.118593] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 16 16:20:55 pcmaguila kernel: [    0.118600] pnp: PnP ACPI init
Oct 16 16:20:55 pcmaguila kernel: [    0.125509] pnp: PnP ACPI: found 13 devices
Oct 16 16:20:55 pcmaguila kernel: [    0.125512] PnPBIOS: Disabled by ACPI PNP
Oct 16 16:20:55 pcmaguila kernel: [    0.125557] PCI: Using ACPI for IRQ routing
Oct 16 16:20:55 pcmaguila kernel: [    0.125561] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 16 16:20:55 pcmaguila kernel: [    0.125577] PCI: Cannot allocate resource region 0 of device 0000:00:01.3
Oct 16 16:20:55 pcmaguila kernel: [    0.183667] NET: Registered protocol family 8
Oct 16 16:20:55 pcmaguila kernel: [    0.183669] NET: Registered protocol family 20
Oct 16 16:20:55 pcmaguila kernel: [    0.184087] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184090] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184092] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184095] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184097] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184099] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184102] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184104] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
Oct 16 16:20:55 pcmaguila kernel: [    0.184341] PCI: Bridge: 0000:00:04.0
Oct 16 16:20:55 pcmaguila kernel: [    0.184343]   IO window: c000-cfff
Oct 16 16:20:55 pcmaguila kernel: [    0.184346]   MEM window: fde00000-fdefffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184349]   PREFETCH window: fd700000-fd7fffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184352] PCI: Bridge: 0000:00:09.0
Oct 16 16:20:55 pcmaguila kernel: [    0.184354]   IO window: b000-bfff
Oct 16 16:20:55 pcmaguila kernel: [    0.184356]   MEM window: fdd00000-fddfffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184358]   PREFETCH window: fdc00000-fdcfffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184361] PCI: Bridge: 0000:00:0b.0
Oct 16 16:20:55 pcmaguila kernel: [    0.184362]   IO window: a000-afff
Oct 16 16:20:55 pcmaguila kernel: [    0.184365]   MEM window: fdb00000-fdbfffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184367]   PREFETCH window: fda00000-fdafffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184369] PCI: Bridge: 0000:00:0c.0
Oct 16 16:20:55 pcmaguila kernel: [    0.184371]   IO window: 9000-9fff
Oct 16 16:20:55 pcmaguila kernel: [    0.184374]   MEM window: fd900000-fd9fffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184376]   PREFETCH window: fd800000-fd8fffff
Oct 16 16:20:55 pcmaguila kernel: [    0.184434] NET: Registered protocol family 2
Oct 16 16:20:55 pcmaguila kernel: [    0.227901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 16 16:20:55 pcmaguila kernel: [    0.228048] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 16 16:20:55 pcmaguila kernel: [    0.228875] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 16 16:20:55 pcmaguila kernel: [    0.229325] TCP: Hash tables configured (established 131072 bind 65536)
Oct 16 16:20:55 pcmaguila kernel: [    0.229328] TCP reno registered
Oct 16 16:20:55 pcmaguila kernel: [    0.243945] checking if image is initramfs... it is
Oct 16 16:20:55 pcmaguila kernel: [    0.766383] Freeing initrd memory: 6785k freed
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] audit: initializing netlink socket (disabled)
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] audit(1192551594.472:1): initialized
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] highmem bounce pool size: 64 pages
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] VFS: Disk quotas dquot_6.5.1
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] io scheduler noop registered
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] io scheduler anticipatory registered
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] io scheduler deadline registered
Oct 16 16:20:55 pcmaguila kernel: [    1.288000] io scheduler cfq registered (default)
Oct 16 16:20:55 pcmaguila kernel: [    1.304000] assign_interrupt_mode Found MSI capability
Oct 16 16:20:55 pcmaguila last message repeated 2 times
Oct 16 16:20:55 pcmaguila kernel: [    1.304000] isapnp: Scanning for PnP cards...
Oct 16 16:20:55 pcmaguila kernel: [    1.656000] isapnp: No Plug & Play device found
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] Real Time Clock Driver v1.12ac
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] mice: PS/2 mouse device common for all mice
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] input: Macintosh mouse button emulation as /class/input/input0
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] EISA: Probing bus 0 at eisa.0
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] Cannot allocate resource for EISA slot 1
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] Cannot allocate resource for EISA slot 2
Oct 16 16:20:55 pcmaguila kernel: [    1.676000] EISA: Detected 0 cards.
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] TCP cubic registered
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] NET: Registered protocol family 1
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] Starting balanced_irq
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] Using IPI No-Shortcut mode
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] ACPI: (supports S0 S1 S3 S4 S5)
Oct 16 16:20:55 pcmaguila kernel: [    1.708000]   Magic number: 11:195:338
Oct 16 16:20:55 pcmaguila kernel: [    1.708000]   hash matches device ttyzd
Oct 16 16:20:55 pcmaguila kernel: [    1.708000]   hash matches device tty59
Oct 16 16:20:55 pcmaguila kernel: [    1.708000] Freeing unused kernel memory: 328k freed
Oct 16 16:20:55 pcmaguila kernel: [    1.712000] Time: acpi_pm clocksource has been installed.
Oct 16 16:20:55 pcmaguila kernel: [    2.920000] Capability LSM initialized
Oct 16 16:20:55 pcmaguila kernel: [    2.952000] ACPI: Fan [FAN] (on)
Oct 16 16:20:55 pcmaguila kernel: [    2.956000] ACPI: Thermal Zone [THRM] (16 C)
Oct 16 16:20:55 pcmaguila kernel: [    3.372000] usbcore: registered new interface driver usbfs
Oct 16 16:20:55 pcmaguila kernel: [    3.372000] usbcore: registered new interface driver hub
Oct 16 16:20:55 pcmaguila kernel: [    3.372000] usbcore: registered new device driver usb
Oct 16 16:20:55 pcmaguila kernel: [    3.376000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Oct 16 16:20:55 pcmaguila kernel: [    3.376000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Oct 16 16:20:55 pcmaguila kernel: [    3.376000] ohci_hcd 0000:00:02.0: OHCI Host Controller
Oct 16 16:20:55 pcmaguila kernel: [    3.376000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Oct 16 16:20:55 pcmaguila kernel: [    3.376000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
Oct 16 16:20:55 pcmaguila kernel: [    3.396000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Oct 16 16:20:55 pcmaguila kernel: [    3.424000] sundance.c:v1.2 11-Sep-2006  Written by Donald Becker
Oct 16 16:20:55 pcmaguila kernel: [    3.424000]   [http://www.scyld.com/network/sundance.html](http://www.scyld.com/network/sundance.html)
Oct 16 16:20:55 pcmaguila kernel: [    3.448000] usb usb1: configuration #1 chosen from 1 choice
Oct 16 16:20:55 pcmaguila kernel: [    3.448000] hub 1-0:1.0: USB hub found
Oct 16 16:20:55 pcmaguila kernel: [    3.448000] hub 1-0:1.0: 8 ports detected
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ehci_hcd 0000:00:02.1: EHCI Host Controller
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ehci_hcd 0000:00:02.1: debug port 1
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfe02e000
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] usb usb2: configuration #1 chosen from 1 choice
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] hub 2-0:1.0: USB hub found
Oct 16 16:20:55 pcmaguila kernel: [    3.552000] hub 2-0:1.0: 8 ports detected
Oct 16 16:20:55 pcmaguila kernel: [    3.656000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
Oct 16 16:20:55 pcmaguila kernel: [    3.656000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
Oct 16 16:20:55 pcmaguila kernel: [    3.656000] forcedeth: using HIGHDMA
Oct 16 16:20:55 pcmaguila kernel: [    4.080000] usb 2-2: new high speed USB device using ehci_hcd and address 2
Oct 16 16:20:55 pcmaguila kernel: [    4.176000] eth0: forcedeth.c: subsystem: 01019:2602 bound to 0000:00:07.0
Oct 16 16:20:55 pcmaguila kernel: [    4.180000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
Oct 16 16:20:55 pcmaguila kernel: [    4.180000] NFORCE-MCP61: chipset revision 162
Oct 16 16:20:55 pcmaguila kernel: [    4.180000] NFORCE-MCP61: not 100%% native mode: will probe irqs later
Oct 16 16:20:55 pcmaguila kernel: [    4.180000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
Oct 16 16:20:55 pcmaguila kernel: [    4.180000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Oct 16 16:20:55 pcmaguila kernel: [    4.180000] SCSI subsystem initialized
Oct 16 16:20:55 pcmaguila kernel: [    4.224000] usb 2-2: configuration #1 chosen from 1 choice
Oct 16 16:20:55 pcmaguila kernel: [    4.464000] usb 2-4: new high speed USB device using ehci_hcd and address 3
Oct 16 16:20:55 pcmaguila kernel: [    4.468000] hda: Maxtor 6E040L0, ATA DISK drive
Oct 16 16:20:55 pcmaguila kernel: [    4.596000] usb 2-4: configuration #1 chosen from 1 choice
Oct 16 16:20:55 pcmaguila kernel: [    4.596000] usbcore: registered new interface driver libusual
Oct 16 16:20:55 pcmaguila kernel: [    4.600000] Initializing USB Mass Storage driver...
Oct 16 16:20:55 pcmaguila kernel: [    4.600000] scsi0 : SCSI emulation for USB Mass Storage devices
Oct 16 16:20:55 pcmaguila kernel: [    4.600000] scsi1 : SCSI emulation for USB Mass Storage devices
Oct 16 16:20:55 pcmaguila kernel: [    4.600000] usbcore: registered new interface driver usb-storage
Oct 16 16:20:55 pcmaguila kernel: [    4.600000] USB Mass Storage support registered.
Oct 16 16:20:55 pcmaguila kernel: [    4.916000] hdb: SONY DVD RW DRU-810A, ATAPI CD/DVD-ROM drive
Oct 16 16:20:55 pcmaguila kernel: [    4.916000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 16 16:20:55 pcmaguila kernel: [    9.600000] scsi 0:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 0 CCS
Oct 16 16:20:55 pcmaguila kernel: [    9.600000] scsi 1:0:0:0: Direct-Access     Ut163    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
Oct 16 16:20:55 pcmaguila kernel: [    9.604000] SCSI device sda: 121856 512-byte hdwr sectors (62 MB)
Oct 16 16:20:55 pcmaguila kernel: [    9.604000] sda: Write Protect is off
Oct 16 16:20:55 pcmaguila kernel: [    9.608000] SCSI device sda: 121856 512-byte hdwr sectors (62 MB)
Oct 16 16:20:55 pcmaguila kernel: [    9.608000] sda: Write Protect is off
Oct 16 16:20:55 pcmaguila kernel: [    9.608000]  sda: sda1
Oct 16 16:20:55 pcmaguila kernel: [    9.608000] sd 0:0:0:0: Attached scsi removable disk sda
Oct 16 16:20:55 pcmaguila kernel: [    9.608000] SCSI device sdb: 4030463 512-byte hdwr sectors (2064 MB)
Oct 16 16:20:55 pcmaguila kernel: [    9.608000] sdb: Write Protect is off
Oct 16 16:20:55 pcmaguila kernel: [    9.612000] SCSI device sdb: 4030463 512-byte hdwr sectors (2064 MB)
Oct 16 16:20:55 pcmaguila kernel: [    9.612000] sdb: Write Protect is off
Oct 16 16:20:55 pcmaguila kernel: [    9.612000]  sdb: sdb1
Oct 16 16:20:55 pcmaguila kernel: [    9.720000] sd 1:0:0:0: Attached scsi removable disk sdb
Oct 16 16:20:55 pcmaguila kernel: [    9.724000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 16 16:20:55 pcmaguila kernel: [    9.724000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[B]Oct 16 16:20:55 pcmaguila kernel: [   34.932000] hdb: lost interrupt
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] hdb: task_in_intr: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] ide: failed opcode was: 0xa1[/B]
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 19
Oct 16 16:20:55 pcmaguila kernel: [   34.932000] eth1: IC Plus Corporation IP100A FAST Ethernet Adapter at 0001c800, 00:08:54:19:0e:0e, IRQ 19.
Oct 16 16:20:55 pcmaguila kernel: [   34.940000] eth1: MII PHY found at address 0, status 0x7849 advertising 01e1.
Oct 16 16:20:55 pcmaguila kernel: [   35.240000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Oct 16 16:20:55 pcmaguila kernel: [   35.240000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
Oct 16 16:20:55 pcmaguila kernel: [   35.240000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001d800 irq 20
Oct 16 16:20:55 pcmaguila kernel: [   35.240000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001d808 irq 20
Oct 16 16:20:55 pcmaguila kernel: [   35.240000] scsi2 : sata_nv
Oct 16 16:20:55 pcmaguila kernel: [   35.552000] ata1: SATA link down (SStatus 0 SControl 300)
Oct 16 16:20:55 pcmaguila kernel: [   35.560000] ATA: abnormal status 0x7F on port 0x000109f7
Oct 16 16:20:55 pcmaguila kernel: [   35.560000] scsi3 : sata_nv
Oct 16 16:20:55 pcmaguila kernel: [   35.872000] ata2: SATA link down (SStatus 0 SControl 300)
Oct 16 16:20:55 pcmaguila kernel: [   35.880000] ATA: abnormal status 0x7F on port 0x00010977
Oct 16 16:20:55 pcmaguila kernel: [   35.888000] hda: max request size: 128KiB
Oct 16 16:20:55 pcmaguila kernel: [   35.888000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63
Oct 16 16:20:55 pcmaguila kernel: [   35.888000] hda: cache flushes supported
Oct 16 16:20:55 pcmaguila kernel: [   35.888000]  hda: hda1 hda2 < hda5 > hda3 hda4
Oct 16 16:20:55 pcmaguila kernel: [   36.136000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   36.136000] hdb: status error: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   36.136000] ide: failed opcode was: unknown
Oct 16 16:20:55 pcmaguila kernel: [   36.136000] hdb: ATAPI CD-ROM drive, 0kB Cache, UDMA(33)
Oct 16 16:20:55 pcmaguila kernel: [   36.136000] Uniform CD-ROM driver Revision: 3.20
Oct 16 16:20:55 pcmaguila kernel: [   36.336000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   36.336000] hdb: status error: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   36.336000] ide: failed opcode was: unknown
...
Oct 16 16:20:55 pcmaguila kernel: [   37.972000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   37.972000] hdb: status error: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   37.972000] ide: failed opcode was: unknown
Oct 16 16:20:55 pcmaguila kernel: [   38.212000] Attempting manual resume
Oct 16 16:20:55 pcmaguila kernel: [   38.244000] kjournald starting.  Commit interval 5 seconds
Oct 16 16:20:55 pcmaguila kernel: [   38.244000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 16 16:20:55 pcmaguila kernel: [   47.004000] eth0: no link during initialization.
Oct 16 16:20:55 pcmaguila kernel: [   47.148000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   47.148000] hdb: status error: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   47.148000] ide: failed opcode was: unknown
Oct 16 16:20:55 pcmaguila kernel: [   47.244000] NET: Registered protocol family 10
Oct 16 16:20:55 pcmaguila kernel: [   47.244000] lo: Disabled Privacy Extensions
Oct 16 16:20:55 pcmaguila kernel: [   47.244000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 16 16:20:55 pcmaguila kernel: [   47.664000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:55 pcmaguila kernel: [   47.664000] hdb: status error: error=0x00 { }
Oct 16 16:20:55 pcmaguila kernel: [   47.664000] ide: failed opcode was: unknown
Oct 16 16:20:55 pcmaguila kernel: [   48.332000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 16 16:20:55 pcmaguila kernel: [   48.332000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 16 16:20:55 pcmaguila kernel: [   48.380000] input: PC Speaker as /class/input/input2
Oct 16 16:20:55 pcmaguila kernel: [   48.400000] parport: PnPBIOS parport detected.
Oct 16 16:20:55 pcmaguila kernel: [   48.400000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Oct 16 16:20:55 pcmaguila kernel: [   48.436000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 16 16:20:55 pcmaguila kernel: [   48.552000] parport0: Printer, HEWLETT-PACKARD DESKJET 710C
Oct 16 16:20:55 pcmaguila kernel: [   48.580000] nvidia: module license 'NVIDIA' taints kernel.
Oct 16 16:20:55 pcmaguila kernel: [   48.840000] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
Oct 16 16:20:55 pcmaguila kernel: [   48.840000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [AIGP] -> GSI 23 (level, low) -> IRQ 16
Oct 16 16:20:55 pcmaguila kernel: [   48.848000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Oct 16 16:20:55 pcmaguila kernel: [   48.968000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Oct 16 16:20:55 pcmaguila kernel: [   48.972000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Oct 16 16:20:55 pcmaguila kernel: [   48.972000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
Oct 16 16:20:55 pcmaguila kernel: [   49.348000] fuse init (API version 7.8)
Oct 16 16:20:55 pcmaguila kernel: [   49.372000] lp0: using parport0 (interrupt-driven).
Oct 16 16:20:55 pcmaguila kernel: [   49.428000] Adding 1020116k swap on /dev/disk/by-uuid/9d1d1229-82c5-4d91-9ee0-8274052e47b3.  Priority:-1 extents:1 across:1020116k
Oct 16 16:20:55 pcmaguila kernel: [   49.628000] EXT3 FS on hda3, internal journal
Oct 16 16:20:55 pcmaguila kernel: [   50.020000] NTFS driver 2.1.28 [Flags: R/O MODULE].
Oct 16 16:20:55 pcmaguila kernel: [   50.084000] NTFS volume version 3.1.
Oct 16 16:20:55 pcmaguila kernel: [   50.132000] NTFS volume version 3.1.
Oct 16 16:20:55 pcmaguila kernel: [   53.108000] NET: Registered protocol family 17
Oct 16 16:20:55 pcmaguila kernel: [   54.312000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Oct 16 16:20:55 pcmaguila kernel: [   54.392000] ndiswrapper: driver net8185 (Realtek,05/09/2006,5.1063.0509.2006) loaded
Oct 16 16:20:55 pcmaguila kernel: [   54.396000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Oct 16 16:20:55 pcmaguila kernel: [   54.396000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
Oct 16 16:20:55 pcmaguila kernel: [   54.664000] ndiswrapper: using IRQ 21
Oct 16 16:20:55 pcmaguila kernel: [   60.904000] wlan0: ethernet device 00:0e:2e:aa:ae:d9 using NDIS driver: net8185, version: 0x50427, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
Oct 16 16:20:55 pcmaguila kernel: [   60.904000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 16 16:20:55 pcmaguila kernel: [   60.904000] usbcore: registered new interface driver ndiswrapper
Oct 16 16:20:55 pcmaguila kernel: [   61.460000] input: Power Button (FF) as /class/input/input4
Oct 16 16:20:55 pcmaguila kernel: [   61.460000] ACPI: Power Button (FF) [PWRF]
Oct 16 16:20:55 pcmaguila kernel: [   61.464000] input: Power Button (CM) as /class/input/input5
Oct 16 16:20:55 pcmaguila kernel: [   61.464000] ACPI: Power Button (CM) [PWRB]
Oct 16 16:20:55 pcmaguila kernel: [   61.496000] Using specific hotkey driver
Oct 16 16:20:55 pcmaguila kernel: [   61.548000] No dock devices found.
Oct 16 16:20:55 pcmaguila kernel: [   61.636000] pcc_acpi: loading...
Oct 16 16:20:55 pcmaguila kernel: [   61.812000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (version 2.00.00)
Oct 16 16:20:55 pcmaguila kernel: [   61.812000] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xc
Oct 16 16:20:55 pcmaguila kernel: [   61.812000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
Oct 16 16:20:55 pcmaguila kernel: [   61.812000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
Oct 16 16:20:55 pcmaguila kernel: [   61.812000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Oct 16 16:20:57 pcmaguila kernel: [   64.556000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:57 pcmaguila kernel: [   64.556000] hdb: status error: error=0x00 { }
Oct 16 16:20:57 pcmaguila kernel: [   64.556000] ide: failed opcode was: unknown
...
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] hdb: status error: error=0x00 { }
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] ide: failed opcode was: unknown
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] cdrom: This disc doesn't have any tracks I recognize!
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] hdb: status error: error=0x00 { }
Oct 16 16:20:58 pcmaguila kernel: [   64.808000] ide: failed opcode was: unknown
...
Oct 16 16:20:58 pcmaguila kernel: [   64.812000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:20:58 pcmaguila kernel: [   64.812000] hdb: status error: error=0x00 { }
Oct 16 16:20:58 pcmaguila kernel: [   64.812000] ide: failed opcode was: unknown
Oct 16 16:20:58 pcmaguila dhcdbd: Started up.
Oct 16 16:21:00 pcmaguila kernel: [   67.020000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:00 pcmaguila kernel: [   67.020000] hdb: status error: error=0x00 { }
Oct 16 16:21:00 pcmaguila kernel: [   67.020000] ide: failed opcode was: unknown
...
Oct 16 16:21:00 pcmaguila kernel: [   67.620000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:00 pcmaguila kernel: [   67.620000] hdb: status error: error=0x00 { }
Oct 16 16:21:00 pcmaguila kernel: [   67.620000] ide: failed opcode was: unknown
Oct 16 16:20:58 pcmaguila kernel: [   67.936000] ppdev: user-space parallel port driver
Oct 16 16:20:59 pcmaguila hpiod: 1.7.3 accepting connections at 2208... 
Oct 16 16:21:00 pcmaguila kernel: [   69.040000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct 16 16:21:00 pcmaguila kernel: [   69.040000] apm: disabled - APM is not SMP safe.
Oct 16 16:21:00 pcmaguila kernel: [   69.200000] Bluetooth: Core ver 2.11
Oct 16 16:21:00 pcmaguila kernel: [   69.200000] NET: Registered protocol family 31
Oct 16 16:21:00 pcmaguila kernel: [   69.200000] Bluetooth: HCI device and connection manager initialized
Oct 16 16:21:00 pcmaguila kernel: [   69.200000] Bluetooth: HCI socket layer initialized
Oct 16 16:21:00 pcmaguila kernel: [   69.212000] Bluetooth: L2CAP ver 2.8
Oct 16 16:21:00 pcmaguila kernel: [   69.212000] Bluetooth: L2CAP socket layer initialized
Oct 16 16:21:00 pcmaguila kernel: [   69.288000] Bluetooth: RFCOMM socket layer initialized
Oct 16 16:21:00 pcmaguila kernel: [   69.288000] Bluetooth: RFCOMM TTY layer initialized
Oct 16 16:21:00 pcmaguila kernel: [   69.288000] Bluetooth: RFCOMM ver 1.8
Oct 16 16:21:00 pcmaguila kernel: [   69.828000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:00 pcmaguila kernel: [   69.828000] hdb: status error: error=0x00 { }
Oct 16 16:21:00 pcmaguila kernel: [   69.828000] ide: failed opcode was: unknown
...
Oct 16 16:21:07 pcmaguila kernel: [   76.452000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:07 pcmaguila kernel: [   76.452000] hdb: status error: error=0x00 { }
Oct 16 16:21:07 pcmaguila kernel: [   76.452000] ide: failed opcode was: unknown
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): comenzando (versiÃ³n  2.18.0.1), pid 6485 usuario Â«marceloÂ»
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readonly:/etc/gconf/gconf.xml.mandatoryÂ» a una fuente de configuraciÃ³n de sÃ³lo lectura en la posiciÃ³n 0
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readwrite:/home/marcelo/.gconfÂ» a una fuente de configuraciÃ³n escribible en la posiciÃ³n 1
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readonly:/etc/gconf/gconf.xml.defaultsÂ» a una fuente de configuraciÃ³n de sÃ³lo lectura en la posiciÃ³n 2
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readonly:/var/lib/gconf/debian.defaultsÂ» a una fuente de configuraciÃ³n de sÃ³lo lectura en la posiciÃ³n 3
Oct 16 16:21:09 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readonly:/var/lib/gconf/defaultsÂ» a una fuente de configuraciÃ³n de sÃ³lo lectura en la posiciÃ³n 4
Oct 16 16:21:09 pcmaguila kernel: [   78.660000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:09 pcmaguila kernel: [   78.660000] hdb: status error: error=0x00 { }
Oct 16 16:21:09 pcmaguila kernel: [   78.660000] ide: failed opcode was: unknown
...
Oct 16 16:21:13 pcmaguila kernel: [   82.136000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:13 pcmaguila kernel: [   82.136000] hdb: status error: error=0x00 { }
Oct 16 16:21:13 pcmaguila kernel: [   82.136000] ide: failed opcode was: unknown
Oct 16 16:21:16 pcmaguila gconfd (marcelo-6485): Se resolviÃ³ la direcciÃ³n Â«xml:readwrite:/home/marcelo/.gconfÂ» a una fuente de configuraciÃ³n escribible en la posiciÃ³n 0
Oct 16 16:21:18 pcmaguila kernel: [   87.648000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:21:18 pcmaguila kernel: [   87.648000] hdb: status error: error=0x00 { }
Oct 16 16:21:18 pcmaguila kernel: [   87.648000] ide: failed opcode was: unknown
...
Oct 16 16:25:02 pcmaguila kernel: [  311.308000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:25:02 pcmaguila kernel: [  311.308000] hdb: status error: error=0x00 { }
Oct 16 16:25:02 pcmaguila kernel: [  311.308000] ide: failed opcode was: unknown
...
Oct 16 16:40:43 pcmaguila kernel: [ 1252.268000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Oct 16 16:40:43 pcmaguila kernel: [ 1252.268000] hdb: status error: error=0x00 { }
Oct 16 16:40:43 pcmaguila kernel: [ 1252.268000] ide: failed opcode was: unknown
Oct 16 16:40:43 pcmaguila exiting on signal 15

---

### Post by margori on 2007-10-17
Hola. Asunto arreglado, aunque no como me gustaria.

El problema es debido a un bug. Este el es reporte, con una solucion:

**[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98670](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98670)**

Lo que tuve que hacer es simplemente sacar **"quite splash"** en la linea que especifica el kernel con sus opciones en /boot/grub/menu.lst

Esto hace que no se muestre la pantalla que dice Ubuntu con la barra que se va llenando debajo en el booteo del sistema. Solo se ven todos llos mensajes del kernel.

Safa, la grabadora anda, aunque me gustaba mas la pantalla de splash y si tenia un problema veia los mensajes.

Bueno eso es todo. Soy novato en Linux, mas novato aun en Ubuntu, pero llego a mi para quedarse. Aguante Ubuntu!

Nos vemos.

---

### Post by margori on 2007-10-19
Hola amigos:

Segun informe en el post anterior, la grabadora funciona pero a medias:

- No tengo problemas al leer información de ella.
- Devuelve el mismo problema si booteo linux con un CD o DVD dentro de la unidad.
- No puedo grabar ni CDs ni DVDs

Estoy seguro que este bug del kernel no me deja hacer ninguna de estas cosas. Incluso he investigado y encontrado que tambien sucede con otras grabadoras como BenQ.

Segun tengo entendido este bug es arreglado en el kernel 2.6.22 que viene con Gutsy, cosa que aun no he probado. Asi que haré el upgradse y estere informando.

Nos vemos.

---

