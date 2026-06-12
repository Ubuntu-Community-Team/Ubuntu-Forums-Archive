---
title: "A few fiesty questions."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Axis on 2007-05-08
If you couldn't tell my questions are about Fiesty Fawn 7.04. 

!) My add/remove application isn't working. I can click and do all of that properly but then when I go to apply, it wont work. It just loads and never does nothing after that. I can't even close the program, i have to restart the computer every time.

2) My  floppy drive isn't recognized, when I had windows installed it worked fine, however now it is not being detected.

3)Well there were more but I will remember them later.

Thanks,
Axis

---

### Post by Spinelli on 2007-05-08
> **Axis said:**
> If you couldn't tell my questions are about Fiesty Fawn 7.04. 

!) My add/remove application isn't working. I can click and do all of that properly but then when I go to apply, it wont work. It just loads and never does nothing after that. I can't even close the program, i have to restart the computer every time.


I have never used Fiesty, but I think you should trying using synaptic instead on Add/Remove Applications. Also if a graphical program freezes you can always press CTRL+ALT+BACKSPACE. This restarts your graphical user interface. It is much faster than rebooting the entire computer.

> 
2) My  floppy drive isn't recognized, when I had windows installed it worked fine, however now it is not being detected.

I am assuming the graphical mounter does not recognize you floppy drive. Trying putting a floppy disk in the drive and typing the following at the terminal:
```
sudo mount /dev/fd0

```
You unmount the floppy by typing:
```
sudo umount /dev/fd0

```
I think the two above commands might work without "sudo", but I'm not sure because I don't know what your /etc/fstab file looks like. I hope that helps.

---

### Post by Axis on 2007-05-08
Haven't tried the floppy thing yet but I appreciate your input and I will try it.

I didn't have the problem with add/remove before I wiped my HD for Fiesty. Also, I don't like synaptec (spelling) because every time I install something on it, I never knew how to access it afterwards.

---

### Post by [ajax] on 2007-05-08
Most things you install with synaptic are found in /usr/bin  .  You can run them by clicking on the file.  Also, you could just type the name into a terminal and it should start up from there.

---

### Post by Spinelli on 2007-05-09
> **Axis said:**
> Also, I don't like synaptec (spelling) because every time I install something on it, I never knew how to access it afterwards.

When I started using Ubuntu back in the 5.10 days I had the same problem, and I learned some basic commands and life was much easier. The four commands you can use to find files on your computer are which, whereis, find, and locate. Let's say you want to install a new web browser called Dillo.
PREREQUISITE: The universe software repository is enabled. If universe is not enabled and you don't know how to enable it follow the link below.
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
 
1. Open synaptic and search for dillo.

2. Right click on dillo and select "Mark for installation". Now sit back and watch the magic happen.

3. Now go to Applications >> Accessories >> Terminal and type the following commands.
Searches your PATH for a command named dillo
```
which dillo
```

Searches for executables, manual pages, and other stuff related to dillo
```
whereis dillo
```

Updates the locate database
```
sudo updatedb
```

Searches the locate database for dillo
```
locate dillo
```

Executes the command dillo
```
dillo
```

Now right click on a panel in GNOME and select "Add to panel". Then click custom application launcher. In the command field type dillo. Fill in the other fields with whatever information you want. Then click ok. There should now be a new button on the panel that launches the dillo web browser!

---

### Post by Axis on 2007-05-10
Thanks for that I will be sure to try it out. I still have yet to try everything that has been suggested but I still have one question that remains unanswered. How do I access the "new control panel"? I can't seem to find it anywhere I look.

---

### Post by Axis on 2007-05-10
Well the adding new packages was very helpful and that problem is solved. But where is the control panel?!?

---

### Post by drowner on 2007-05-10
I'm not sure what you mean by 'control panel'

---

### Post by RomeReactor on 2007-05-10
Hi. I'm not sure if this is what you're looking for, but here goes: Right-click on the menu on the top panel (the one that reads **Applications  Places  System**) and select "Edit Menus". Now highlight the "Preferences" menu on the left pane, and on the right pane check the entry **Control Center**.

---

### Post by Axis on 2007-05-10
Thanks very much. That was exactly what I meant. I apologize for not going into further explination on what I meant by control panel (come to find out now I was looking for control center)


However I finally got around to checking it and I still cannot use my floppy drive.

---

### Post by Spinelli on 2007-05-11
> 
However I finally got around to checking it and I still cannot use my floppy drive.

We will need more information about your computer to help you with your floppy drive. Please post the output of the following commands.
```
cat /etc/fstab
```
```
dmesg | grep 'fd0'
```

---

### Post by Axis on 2007-05-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fdad8080-5f79-4666-83f0-547fef651c2f /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



Thats from the first one, the other one accepted the command, but literally did nothing

---

### Post by Spinelli on 2007-05-13
> **Axis said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fdad8080-5f79-4666-83f0-547fef651c2f /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



Thats from the first one, the other one accepted the command, but literally did nothing
NOTE: The end of the following command should be 'fd zero' NOT 'fd capital O'
```
dmesg | grep 'fd0'
```

You also might want to post a full dmesg to this thread.
```
dmesg > ~/dmesg.txt
```
You should now have a file called dmesg.txt in your home directory.

---

### Post by setyawan111 on 2007-05-16
[B]Problem FDD cannot mount.
This problem after I use MB Jetway chipset VIA. 
what must I do for solbe the problem?

user@user-desktop:~$ vim /etc/fstab[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd3
UUID=46ade255-56e0-4bb0-a526-101d93868a50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=eef2febf-ddad-45b6-9901-ca051d25776a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


user@user-desktop:~$ dmesg | grep 'fd0'
[   56.053152] mapped APIC to ffffd000 (fee00000)
[    3.159434] Floppy drive(s): fd0 is 1.44M
[  272.681577] VFS: Can't find ext3 filesystem on dev fd0.
[  272.682131] VFS: Can't find a valid FAT filesystem on dev fd0.
user@user-desktop:~$ 


user@user-desktop:~$  dmesg > ~/dmesg.txt
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003bde0000 end: 000000003bee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003bee0000 size: 0000000000003000 end: 000000003bee3000 type: 4
[    0.000000] copy_e820_map() start: 000000003bee3000 size: 000000000000d000 end: 000000003bef0000 type: 3
[    0.000000] copy_e820_map() start: 000000003bef0000 size: 0000000000010000 end: 000000003bf00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bee0000 (usable)
[    0.000000]  BIOS-e820: 000000003bee0000 - 000000003bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bee3000 - 000000003bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bf00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5000
[    0.000000] Entering add_active_range(0, 0, 245472) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245472
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245472
[    0.000000] On node 0 totalpages: 245472
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15971 pages, LIFO batch:3
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 P4M80P                                ) @ 0x000f9190
[    0.000000] ACPI: RSDT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee3040
[    0.000000] ACPI: FADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee30c0
[    0.000000] ACPI: MADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee7fc0
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20060113) @ 0x3bee8090
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060113) @ 0x3bee8520
[    0.000000] ACPI: DSDT (v001 P4M80P AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:c2d00000)
[    0.000000] Detected 3200.215 MHz processor.
[   56.052997] Built 1 zonelists.  Total pages: 243555
[   56.053002] Kernel command line: root=UUID=46ade255-56e0-4bb0-a526-101d93868a50 ro quiet splash 
[   56.053152] mapped APIC to ffffd000 (fee00000)
[   56.053155] mapped IOAPIC to ffffc000 (fec00000)
[   56.053158] Enabling fast FPU save and restore... done.
[   56.053160] Enabling unmasked SIMD FPU exception support... done.
[   56.053173] Initializing CPU#0
[   56.053269] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   56.054534] Console: colour VGA+ 80x25
[   56.055271] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   56.055855] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   56.076707] Memory: 962048k/981888k available (1992k kernel code, 19208k reserved, 893k data, 328k init, 64384k highmem)
[   56.076717] virtual kernel memory layout:
[   56.076718]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   56.076719]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   56.076720]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   56.076721]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   56.076722]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   56.076723]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   56.076724]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   56.076727] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   56.152970] Calibrating delay using timer specific routine.. 6407.29 BogoMIPS (lpj=12814588)
[   56.153009] Security Framework v1.0.0 initialized
[   56.153014] SELinux:  Disabled at boot.
[   56.153029] Mount-cache hash table entries: 512
[   56.153151] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   56.153159] monitor/mwait feature present.
[   56.153161] using mwait in idle threads.
[   56.153167] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   56.153170] CPU: L2 cache: 2048K
[   56.153172] CPU: Physical Processor ID: 0
[   56.153174] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000649d 00000000 00000000
[   56.153184] Compat vDSO mapped to ffffe000.
[   56.153187] Remapping vsyscall page to ffffe000
[   56.153201] Checking 'hlt' instruction... OK.
[   56.169002] SMP alternatives: switching to UP code
[   56.169310] Early unpacking initramfs... done
[   56.433527] ACPI: Core revision 20060707
[   56.437717] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   56.489690] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   56.489713] SMP alternatives: switching to SMP code
[   56.489833] Booting processor 1/1 eip 3000
[   56.500314] Initializing CPU#1
[   56.579655] Calibrating delay using timer specific routine.. 6400.52 BogoMIPS (lpj=12801040)
[   56.579664] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   56.579671] monitor/mwait feature present.
[   56.579678] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   56.579680] CPU: L2 cache: 2048K
[   56.579683] CPU: Physical Processor ID: 0
[   56.579685] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000649d 00000000 00000000
[   56.580193] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   56.580235] Total of 2 processors activated (12807.81 BogoMIPS).
[   56.580982] ENABLING IO-APIC IRQs
[   56.581292] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   56.727214] checking TSC synchronization across 2 CPUs: passed.
[    0.003990] Brought up 2 CPUs
[    0.218579] migration_cost=132
[    0.218865] Booting paravirtualized kernel on bare hardware
[    0.218960] Time: 13:43:40  Date: 04/16/107
[    0.218990] NET: Registered protocol family 16
[    0.219080] EISA bus registered
[    0.219086] ACPI: bus type pci registered
[    0.227287] PCI: PCI BIOS revision 2.10 entry at 0xfb730, last bus=1
[    0.227290] PCI: Using configuration type 1
[    0.227292] Setting up standard PCI resources
[    0.237780] ACPI: Interpreter enabled
[    0.237783] ACPI: Using IOAPIC for interrupt routing
[    0.238458] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.238463] PCI: Probing PCI hardware (bus 00)
[    0.239734] Boot video device is 0000:01:00.0
[    0.239795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.290289] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.290641] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.290995] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.291344] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.291662] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.291971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.292283] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.292595] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.293105] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.293587] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.293950] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.294381] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.296579] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.296589] pnp: PnP ACPI init
[    0.300899] pnp: PnP ACPI: found 13 devices
[    0.300903] PnPBIOS: Disabled by ACPI PNP
[    0.300957] PCI: Using ACPI for IRQ routing
[    0.300960] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.311493] NET: Registered protocol family 8
[    0.311496] NET: Registered protocol family 20
[    0.311872] pnp: 00:02: ioport range 0x400-0x47f could not be reserved
[    0.311875] pnp: 00:02: ioport range 0x500-0x50f has been reserved
[    0.312230] PCI: Bridge: 0000:00:01.0
[    0.312234]   IO window: b000-bfff
[    0.312240]   MEM window: fb000000-fcffffff
[    0.312244]   PREFETCH window: f4000000-f7ffffff
[    0.312263] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.312291] NET: Registered protocol family 2
[    0.354944] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.355154] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.355767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.356200] TCP: Hash tables configured (established 131072 bind 65536)
[    0.356203] TCP reno registered
[    0.366982] checking if image is initramfs... it is
[    0.901156] Freeing initrd memory: 7007k freed
[    0.901877] audit: initializing netlink socket (disabled)
[    0.901901] audit(1179323020.612:1): initialized
[    0.902012] highmem bounce pool size: 64 pages
[    0.902110] VFS: Disk quotas dquot_6.5.1
[    0.902139] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.902204] io scheduler noop registered
[    0.902207] io scheduler anticipatory registered
[    0.902210] io scheduler deadline registered
[    0.902221] io scheduler cfq registered (default)
[    0.902306] PCI: Bypassing VIA 8237 APIC De-Assert Message
[    0.902541] isapnp: Scanning for PnP cards...
[    1.253173] isapnp: No Plug & Play device found
[    1.279511] Real Time Clock Driver v1.12ac
[    1.279573] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.279695] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.280346] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.280574] mice: PS/2 mouse device common for all mice
[    1.281213] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.281377] input: Macintosh mouse button emulation as /class/input/input0
[    1.281416] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.281421] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.281694] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.281932] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.281938] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.282043] EISA: Probing bus 0 at eisa.0
[    1.282086] EISA: Detected 0 cards.
[    1.312094] TCP cubic registered
[    1.312105] NET: Registered protocol family 1
[    1.312132] Starting balanced_irq
[    1.312141] Using IPI No-Shortcut mode
[    1.312227] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.312307] ACPI: (supports S0 S1 S4 S5)
[    1.312360]   Magic number: 7:258:736
[    1.312872] Freeing unused kernel memory: 328k freed
[    1.315944] Time: tsc clocksource has been installed.
[    2.511633] Capability LSM initialized
[    2.545810] ACPI: Fan [FAN] (on)
[    2.550111] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.550163] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.550171] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.551381] ACPI: Thermal Zone [THRM] (40 C)
[    2.970107] usbcore: registered new interface driver usbfs
[    2.970144] usbcore: registered new interface driver hub
[    3.021699] usbcore: registered new device driver usb
[    3.090460] SCSI subsystem initialized
[    3.112705] libata version 2.20 loaded.
[    3.141272] sata_via 0000:00:0f.0: version 2.1
[    3.141836] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    3.141846] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[    3.141870] sata_via 0000:00:0f.0: routed to hard irq line 11
[    3.145421] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[    3.146253] ata1: SATA max UDMA/133 cmd 0x0001fc00 ctl 0x0001f802 bmdma 0x0001ec00 irq 16
[    3.146291] ata2: SATA max UDMA/133 cmd 0x0001f400 ctl 0x0001f002 bmdma 0x0001ec08 irq 16
[    3.146316] scsi0 : sata_via
[    3.147262] USB Universal Host Controller Interface driver v3.0
[    3.159434] Floppy drive(s): fd0 is 1.44M
[    3.181809] FDC 0 is a post-1991 82077
[    3.353426] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.363520] ATA: abnormal status 0x7F on port 0x0001fc07
[    3.363538] scsi1 : sata_via
[    3.568743] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.578834] ATA: abnormal status 0x7F on port 0x0001f407
[    3.579810] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    3.579836] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[    3.579852] VP_IDE: chipset revision 6
[    3.579855] VP_IDE: not 100% native mode: will probe irqs later
[    3.579871] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    3.579881]     ide0: BM-DMA at 0xe400-0xe407, BIOS settings: hda:pio, hdb:pio
[    3.579898]     ide1: BM-DMA at 0xe408-0xe40f, BIOS settings: hdc:DMA, hdd:DMA
[    3.579909] Probing IDE interface ide0...
[    4.146931] Probing IDE interface ide1...
[    4.677351] hdc: ATAPI CD-ROM MAX 56X, ATAPI CD/DVD-ROM drive
[    4.956470] hdd: Maxtor 2F020J0, ATA DISK drive
[    5.012527] ide1 at 0x170-0x177,0x376 on irq 15
[    6.587309] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    6.587324] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    6.587342] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    6.587519] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    6.587576] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfdfff000
[    6.587585] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.587697] usb usb1: configuration #1 chosen from 1 choice
[    6.587742] hub 1-0:1.0: USB hub found
[    6.587751] hub 1-0:1.0: 8 ports detected
[    6.598078] hdc: ATAPI 56X CD-ROM drive, 128kB Cache
[    6.598089] Uniform CD-ROM driver Revision: 3.20
[    6.606216] hdd: max request size: 128KiB
[    6.606354] hdd: 40718160 sectors (20847 MB) w/2048KiB Cache, CHS=40395/16/63, UDMA(133)
[    6.606486] hdd: cache flushes supported
[    6.606532]  hdd: hdd1 hdd2 hdd3 hdd4 < hdd5 hdd6ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    6.695683] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[    6.695798] eth0: VIA Rhine II at 0x1cc00, 00:30:18:a2:78:e4, IRQ 18.
[    6.696524] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 0021.
[    6.696678] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    6.696692] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    6.696729] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    6.696757] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e000
[    6.696902] usb usb2: configuration #1 chosen from 1 choice
[    6.696939] hub 2-0:1.0: USB hub found
[    6.696950] hub 2-0:1.0: 2 ports detected
[    6.715734]  hdd7 >
[    6.802667] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    6.802684] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    6.802720] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    6.802747] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000dc00
[    6.802891] usb usb3: configuration #1 chosen from 1 choice
[    6.802931] hub 3-0:1.0: USB hub found
[    6.802942] hub 3-0:1.0: 2 ports detected
[    6.906307] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    6.906321] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    6.906355] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    6.906380] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d800
[    6.906520] usb usb4: configuration #1 chosen from 1 choice
[    6.906558] hub 4-0:1.0: USB hub found
[    6.906568] hub 4-0:1.0: 2 ports detected
[    7.010040] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    7.010062] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    7.010098] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    7.010126] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d400
[    7.010265] usb usb5: configuration #1 chosen from 1 choice
[    7.010308] hub 5-0:1.0: USB hub found
[    7.010320] hub 5-0:1.0: 2 ports detected
[    7.500342] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    7.689111] usb 3-2: configuration #1 chosen from 1 choice
[    7.881645] Attempting manual resume
[    7.881649] swsusp: Resume From Partition 22:69
[    7.881651] PM: Checking swsusp image.
[    7.919422] PM: Resume from disk failed.
[    7.963897] kjournald starting.  Commit interval 5 seconds
[    7.963902] EXT3-fs: mounted filesystem with ordered data mode.
[    8.206169] usbcore: registered new interface driver libusual
[    9.177265] Initializing USB Mass Storage driver...
[    9.177348] scsi2 : SCSI emulation for USB Mass Storage devices
[    9.177406] usb-storage: device found at 2
[    9.177409] usb-storage: waiting for device to settle before scanning
[    9.177412] usbcore: registered new interface driver usb-storage
[    9.177416] USB Mass Storage support registered.
[   14.163343] usb-storage: device scan complete
[   14.268418] scsi 2:0:0:0: Direct-Access     MITSUMI  USB FDD          1050 PQ: 0 ANSI: 0 CCS
[   21.565571] eth0: link up, 10Mbps, half-duplex, lpa 0x0021
[   22.968517] Linux agpgart interface v0.102 (c) Dave Jones
[   22.974179] agpgart: Detected VIA VT3314 chipset
[   22.982659] agpgart: AGP aperture is 128M @ 0xe8000000
[   23.038248] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.042661] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.473180] NET: Registered protocol family 17
[   23.540584] parport: PnPBIOS parport detected.
[   23.540635] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   23.814873] input: PC Speaker as /class/input/input2
[   23.867133] NET: Registered protocol family 10
[   23.867249] lo: Disabled Privacy Extensions
[   24.182778] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   24.305939] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   24.305949] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 19
[   24.306102] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   24.476400] SCSI device sda: 2880 512-byte hdwr sectors (1 MB)
[   24.603996] sda: Write Protect is off
[   24.603999] sda: Mode Sense: 00 52 94 00
[   24.604002] sda: assuming drive cache: write through
[   25.114399] SCSI device sda: 2880 512-byte hdwr sectors (1 MB)
[   25.241997] sda: Write Protect is off
[   25.242000] sda: Mode Sense: 00 52 94 00
[   25.242002] sda: assuming drive cache: write through
[   25.242006]  sda: unknown partition table
[   26.645661] sd 2:0:0:0: Attached scsi removable disk sda
[   26.681155] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   26.865406] fuse init (API version 7.8)
[   26.887341] lp0: using parport0 (interrupt-driven).
[   26.913450] Adding 425680k swap on /dev/disk/by-uuid/eef2febf-ddad-45b6-9901-ca051d25776a.  Priority:-1 extents:1 across:425680k
[   27.055963] EXT3 FS on hdd3, internal journal
[   32.386162] No dock devices found.
[   32.414885] Using specific hotkey driver
[   32.492771] ibm_acpi: ec object not found
[   32.551767] input: Power Button (FF) as /class/input/input4
[   32.551810] ACPI: Power Button (FF) [PWRF]
[   32.551864] input: Power Button (CM) as /class/input/input5
[   32.551889] ACPI: Power Button (CM) [PWRB]
[   32.697217] pcc_acpi: loading...
[   34.323708] eth0: no IPv6 routers present
[   42.343031] ppdev: user-space parallel port driver
[   43.325560] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   43.325567] apm: disabled - APM is not SMP safe.
[   43.690547] Bluetooth: Core ver 2.11
[   43.690727] NET: Registered protocol family 31
[   43.690732] Bluetooth: HCI device and connection manager initialized
[   43.690736] Bluetooth: HCI socket layer initialized
[   43.788942] Bluetooth: L2CAP ver 2.8
[   43.788949] Bluetooth: L2CAP socket layer initialized
[   43.806461] Bluetooth: RFCOMM socket layer initialized
[   43.806598] Bluetooth: RFCOMM TTY layer initialized
[   43.806603] Bluetooth: RFCOMM ver 1.8
[   56.103023] eth0: no IPv6 routers present
[  272.680954] cramfs: wrong magic
[  272.681577] VFS: Can't find ext3 filesystem on dev fd0.
[  272.682126] FAT: bogus number of reserved sectors
[  272.682131] VFS: Can't find a valid FAT filesystem on dev fd0.

---

### Post by Spinelli on 2007-05-16
> **setyawan111 said:**
> [B]Problem FDD cannot mount.
This problem after I use MB Jetway chipset VIA. 
what must I do for solbe the problem?

[  272.681577] VFS: Can't find ext3 filesystem on dev fd0.
[  272.682126] FAT: bogus number of reserved sectors
[  272.682131] VFS: Can't find a valid FAT filesystem on dev fd0.

Try formating the floppy. Try using different floppy disks.

NOTE: When you format a floppy disk you will lose all of the data on it.

---

