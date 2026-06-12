---
title: "[SOLVED] LiveCD desktop splash screen crash"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by SDL on 2007-06-15
Hi. I'm new to Linux and have been trying to run the 32-bit Unbuntu 7.04 LiveCD on my pc.

I have no apparent problems until the splash screen loads, followed by the desktop and the introduction sound plays. Within a very short period of time, the mouse becomes completely unresponsive and the only thing I can do is turn off the computer by holding the front power switch down for 3s.

I've booted numerous times and normally I can only get as far as the yellow screen with Ubuntu written in the centre although once the start menu did appear and I managed to click on that just before the PC crased.

The CD works fine and I performed the CheckSum and memtest on it successfully.

My PC is 3 years old, and has successfully run XP during that time. The specs are:
Processor:       AMD Athlon 64, 2000 MHz (10 x 200) 3000+
Motherboard:  Foxconn 755A01/K8S755A Series
RAM:               1536 MB  (PC3200 DDR SDRAM)
Graphics card: NVIDIA GeForce FX 5700  (128 MB)
HDD:               WDC WD1200JB-00GVC0 (111 GB)

Thanks for reading this.

Stephen.

---

### Post by candtalan on 2007-06-15
there are reports of freezing with 7.04 in this forum, it did for me too. On one machine only, the others are all ok. If it is the same thing, then with more or different configuration or applications, it might reduce or dissappear even, I do not think it is known yet. In my case I was able to run long enough to install (from kubuntu) the xubuntu-desktop also. I did not run it much after that so far but it did not freeze over more than 24 hours, then I turned it off.

ineteresting to see:
[http://ubuntuforums.org/showthread.php?t=412125&highlight=freeze+crazy](http://ubuntuforums.org/showthread.php?t=412125&highlight=freeze+crazy)

---

### Post by SDL on 2007-06-17
Thanks for your reply. I'm still reading through the link you sent me, so I'll let you know how I get on.

One interesting detail about what I'm experiencing is it seems to differ from most other accounts as the freezes are not transient and the PC is completely unresponsive, even using ALT-SysRq-O.

I should also mention that I have now abandoned the LiveCD and installed the alternated CD 32-bit Ubuntu 7.04 onto a partitioned drive. So, I'm now capable of using Recovery mode at least!

---

### Post by SDL on 2007-06-17
I think I have a different problem to the ones described here:
> [http://ubuntuforums.org/showthread.p...t=freeze+crazy](http://ubuntuforums.org/showthread.p...t=freeze+crazy)

They describe freezes, whereas I have difficulty with crashes - most of them can move their mice - for me the mouse won't move, the keyboard won't work, none of the keys such as Ctrl-Alt-F1 or Ctrl-SysRq-O will work. In fact the only way I can turn off the PC is to press the reset or power buttons on the case.

Another significant difference is that these users all seem to have installed special nvidia drivers. I'm very much a Linux beginner but I don't think I can have installed any special drivers seeing as I haven't been able to make it past the login screen!

Somebody did mention debugging in the thread:
[https://help.ubuntu.com/community/DebuggingSystemCrash]("https://help.ubuntu.com/community/DebuggingSystemCrash")
Perhaps I could use this to explore my problem in more detail.

MemoryTest gives me a clean bill of health. If you could tell me how to copy the file:
> /var/log/kern.log
onto a memory stick so that I could copy and paste the results into this forum that might help me?

Thanks for the help and sorry to write such a big post.

Stephen.

---

### Post by Rui Pais on 2007-06-17
hi.
the way to copy stuff to memory stick is simple. 
The tricky thing is get your stick mounted...

If your desktop can hold stable enough so you can insert the stick on the usb port and get auto maunted, do that  and close imediatly session as soon as it appears on desktop.

Now, press Ctrl+Alt+F1 and on console login (as normal user)
type:
```
ls /media/* 
```
to check where the stick is mounted (the name)
the just do: 
```
cd /media/<name_of_stick>
```
and type:
```
cp /var/log/kern.log .
cp ~/.xsession-errors .
```

If you session is not stable enough to hold till stick is mounted, post here and we tell you how can you do it manually.


btw, what driver do you use to your nvidia (and if isn't nv how do you install it)?

---

### Post by SDL on 2007-06-18
Hi.

Sorry for the slow response - I've been at work where I don't have access to a PC.

Unfortunately, I think my PC is too unstable to mount the USB stick automatically, only once have I even been able to enter my username and password before the crash occurs.

I haven't altered the nvidia driver from the default install, so presumably I'm using the nv driver?

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-18
hi.
So your box frozen even when you didn't login? just keeping gdm (the login manager) running?

Sounds like some hardware incompatibility...

Another suspect is the nvidia driver. Some users find the open source nv more stable then closed source nvidia. Others complain exactly of the opposite...

To mount you stick you need to know how kernel detect it. 
Go to a console (Ctrl+Alt+F1)
Insert the usb stick, wait till light stop flashing and type:
```
dmesg
```
shoud give a lot of output and in the last lines something like:
```
[ 2512.844356] sdc: assuming drive cache: write through
[ 2512.844364]  sdc: **sdc1**
[ 2512.845692] sd 4:0:0:0: Attached scsi removable disk sdc

```
so in this example its detected as sdc1. Now do:
```
mkdir stick
```
then:
```
mount /dev/sdc1 stick
```
and replace sdc1 if your dmesg shows something different (should be sdcX or sgX).
Should be mounted.
type:
```
sudo mount
```
to check it (or **ls stick**)
Now type:```

cp /var/log/kern.log stick/
cp ~/.xsession-errors stick/
```
And you have those logs on the stick.

(better print this ...)

---

### Post by SDL on 2007-06-18
Yes, the PC crashes even when in gdm - rarely I can login successfully but I'd never have time to do anything beyond that.

I tried to use the USB stick as you suggest. Unfortunately, when I type:
```
mdir stick
```
I get an error message:
> The program 'mdir' is currently not installed. You can install it by typing sudo apt-get install mtools

When I enter:
```
sudo apt-get install mtools
```
I get the error message:
> -bash: mdir command not found

I'd try to install the closed source nvidia drivers but without the use of a USB stick that won't be possible as I haven't successfully configured my wireless card either! :|

Have searched the forums for my startup problems and the 'mdir' problem with no success. Sorry to keep asking you for help, as a new user it's frustrating to be able to do so little to help myself.

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-18
> **SDL said:**
> Yes, the PC crashes even when in gdm - rarely I can login successfully but I'd never have time to do anything beyond that.

I tried to use the USB stick as you suggest. Unfortunately, when I type:
```
mdir stick
```
I get an error message

[COLOR="DimGray"]damn it, you got me 2nd time with typos.
My deepest sorries, Stephen. 
I read my post 2 or 3 times to make sure it was alright (i know you haven't much Linux practice) and did notice. 

It's:
```
**mkdir stick**
```
[/COLOR]

edit: oops. bad boy. Your typo, this time, not mine... :lol:

---

### Post by Rui Pais on 2007-06-18
btw there is an excellent tool that you can always use.
Its called auto-completion.

Type 2 or 3 letters of the command and then press the key TAB. 
That will automatically finish instruction with the correct command.

---

### Post by SDL on 2007-06-18
Ooops... works a whole lot better without the typos!

Here is the file kern.log:
> Jun 18 19:16:49 PC1 kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jun 18 19:16:49 PC1 kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Jun 18 19:16:49 PC1 kernel: Symbols match kernel version 2.6.20.
Jun 18 19:16:49 PC1 kernel: No module symbols loaded - kernel modules not enabled. 
Jun 18 19:16:49 PC1 kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jun 18 19:16:49 PC1 kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 18 19:16:49 PC1 kernel: [    0.000000] sanitize start
Jun 18 19:16:49 PC1 kernel: [    0.000000] sanitize end
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fef0000 end: 000000005fff0000 type: 1
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 000000005fff0000 size: 0000000000003000 end: 000000005fff3000 type: 4
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 000000005fff3000 size: 000000000000d000 end: 0000000060000000 type: 3
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Jun 18 19:16:49 PC1 kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 18 19:16:49 PC1 kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jun 18 19:16:49 PC1 kernel: [    0.000000] 639MB HIGHMEM available.
Jun 18 19:16:49 PC1 kernel: [    0.000000] 896MB LOWMEM available.
Jun 18 19:16:49 PC1 kernel: [    0.000000] found SMP MP-table at 000f56c0
Jun 18 19:16:49 PC1 kernel: [    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
Jun 18 19:16:49 PC1 kernel: [    0.000000] Zone PFN ranges:
Jun 18 19:16:49 PC1 kernel: [    0.000000]   DMA             0 ->     4096
Jun 18 19:16:49 PC1 kernel: [    0.000000]   Normal       4096 ->   229376
Jun 18 19:16:49 PC1 kernel: [    0.000000]   HighMem    229376 ->   393200
Jun 18 19:16:49 PC1 kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 18 19:16:49 PC1 kernel: [    0.000000]     0:        0 ->   393200
Jun 18 19:16:49 PC1 kernel: [    0.000000] On node 0 totalpages: 393200
Jun 18 19:16:49 PC1 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 18 19:16:49 PC1 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 18 19:16:49 PC1 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jun 18 19:16:49 PC1 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Jun 18 19:16:49 PC1 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Jun 18 19:16:49 PC1 kernel: [    0.000000]   HighMem zone: 1279 pages used for memmap
Jun 18 19:16:49 PC1 kernel: [    0.000000]   HighMem zone: 162545 pages, LIFO batch:31
Jun 18 19:16:49 PC1 kernel: [    0.000000] DMI 2.2 present.
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f7100
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff3000
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff3040
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff6e40
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 18 19:16:49 PC1 kernel: [    0.000000] Processor #0 15:12 APIC version 16
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 18 19:16:49 PC1 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 18 19:16:49 PC1 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 18 19:16:49 PC1 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 18 19:16:49 PC1 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 18 19:16:49 PC1 kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
Jun 18 19:16:49 PC1 kernel: [    0.000000] Detected 1999.482 MHz processor.
Jun 18 19:16:49 PC1 kernel: [   18.424594] Built 1 zonelists.  Total pages: 390129
Jun 18 19:16:49 PC1 kernel: [   18.424598] Kernel command line: root=UUID=80883c48-ec10-49ad-a97a-f7efa1f2d4f6 ro quiet splash
Jun 18 19:16:49 PC1 kernel: [   18.424730] mapped APIC to ffffd000 (fee00000)
Jun 18 19:16:49 PC1 kernel: [   18.424732] mapped IOAPIC to ffffc000 (fec00000)
Jun 18 19:16:49 PC1 kernel: [   18.424736] Enabling fast FPU save and restore... done.
Jun 18 19:16:49 PC1 kernel: [   18.424738] Enabling unmasked SIMD FPU exception support... done.
Jun 18 19:16:49 PC1 kernel: [   18.424748] Initializing CPU#0
Jun 18 19:16:49 PC1 kernel: [   18.424802] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 18 19:16:49 PC1 kernel: [   18.426164] Console: colour VGA+ 80x25
Jun 18 19:16:49 PC1 kernel: [   18.426849] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 18 19:16:49 PC1 kernel: [   18.427348] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 18 19:16:49 PC1 kernel: [   18.471949] Memory: 1547972k/1572800k available (1992k kernel code, 23576k reserved, 893k data, 328k init, 655296k highmem)
Jun 18 19:16:49 PC1 kernel: [   18.471959] virtual kernel memory layout:
Jun 18 19:16:49 PC1 kernel: [   18.471960]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jun 18 19:16:49 PC1 kernel: [   18.471961]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 18 19:16:49 PC1 kernel: [   18.471962]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jun 18 19:16:49 PC1 kernel: [   18.471964]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 18 19:16:49 PC1 kernel: [   18.471965]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Jun 18 19:16:49 PC1 kernel: [   18.471966]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Jun 18 19:16:49 PC1 kernel: [   18.471967]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Jun 18 19:16:49 PC1 kernel: [   18.471970] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 18 19:16:49 PC1 kernel: [   18.548778] Calibrating delay using timer specific routine.. 4000.83 BogoMIPS (lpj=8001662)
Jun 18 19:16:49 PC1 kernel: [   18.548821] Security Framework v1.0.0 initialized
Jun 18 19:16:49 PC1 kernel: [   18.548832] SELinux:  Disabled at boot.
Jun 18 19:16:49 PC1 kernel: [   18.548848] Mount-cache hash table entries: 512
Jun 18 19:16:49 PC1 kernel: [   18.549009] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
Jun 18 19:16:49 PC1 kernel: [   18.549018] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 18 19:16:49 PC1 kernel: [   18.549021] CPU: L2 Cache: 512K (64 bytes/line)
Jun 18 19:16:49 PC1 kernel: [   18.549024] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
Jun 18 19:16:49 PC1 kernel: [   18.549036] Compat vDSO mapped to ffffe000.
Jun 18 19:16:49 PC1 kernel: [   18.549041] Remapping vsyscall page to ffffe000
Jun 18 19:16:49 PC1 kernel: [   18.549052] Checking 'hlt' instruction... OK.
Jun 18 19:16:49 PC1 kernel: [   18.564937] SMP alternatives: switching to UP code
Jun 18 19:16:49 PC1 kernel: [   18.565206] Freeing SMP alternatives: 11k freed
Jun 18 19:16:49 PC1 kernel: [   18.565429] Early unpacking initramfs... done
Jun 18 19:16:49 PC1 kernel: [   18.847036] ACPI: Core revision 20060707
Jun 18 19:16:49 PC1 kernel: [   18.853295] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun 18 19:16:49 PC1 kernel: [   18.855121] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
Jun 18 19:16:49 PC1 kernel: [   18.855137] Total of 1 processors activated (4000.83 BogoMIPS).
Jun 18 19:16:49 PC1 kernel: [   18.855228] ENABLING IO-APIC IRQs
Jun 18 19:16:49 PC1 kernel: [   18.855388] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 18 19:16:49 PC1 kernel: [   19.000713] Brought up 1 CPUs
Jun 18 19:16:49 PC1 kernel: [   19.000905] Booting paravirtualized kernel on bare hardware
Jun 18 19:16:49 PC1 kernel: [   19.000972] Time: 19:16:17  Date: 05/18/107
Jun 18 19:16:49 PC1 kernel: [   19.000999] NET: Registered protocol family 16
Jun 18 19:16:49 PC1 kernel: [   19.001079] EISA bus registered
Jun 18 19:16:49 PC1 kernel: [   19.001083] ACPI: bus type pci registered
Jun 18 19:16:49 PC1 kernel: [   19.036791] PCI: PCI BIOS revision 2.10 entry at 0xfba50, last bus=1
Jun 18 19:16:49 PC1 kernel: [   19.036793] PCI: Using configuration type 1
Jun 18 19:16:49 PC1 kernel: [   19.036795] Setting up standard PCI resources
Jun 18 19:16:49 PC1 kernel: [   19.049152] ACPI: Interpreter enabled
Jun 18 19:16:49 PC1 kernel: [   19.049154] ACPI: Using IOAPIC for interrupt routing
Jun 18 19:16:49 PC1 kernel: [   19.049631] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 18 19:16:49 PC1 kernel: [   19.049635] PCI: Probing PCI hardware (bus 00)
Jun 18 19:16:49 PC1 kernel: [   19.049692] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jun 18 19:16:49 PC1 kernel: [   19.050238] Boot video device is 0000:01:00.0
Jun 18 19:16:49 PC1 kernel: [   19.050264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 18 19:16:49 PC1 kernel: [   19.081146] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.081340] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.081537] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.081730] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.081925] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.082118] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.082314] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.082510] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 18 19:16:49 PC1 kernel: [   19.084821] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 18 19:16:49 PC1 kernel: [   19.084835] pnp: PnP ACPI init
Jun 18 19:16:49 PC1 kernel: [   19.087692] pnp: PnP ACPI: found 13 devices
Jun 18 19:16:49 PC1 kernel: [   19.087695] PnPBIOS: Disabled by ACPI PNP
Jun 18 19:16:49 PC1 kernel: [   19.087744] PCI: Using ACPI for IRQ routing
Jun 18 19:16:49 PC1 kernel: [   19.087747] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 18 19:16:49 PC1 kernel: [   19.092646] NET: Registered protocol family 8
Jun 18 19:16:49 PC1 kernel: [   19.092648] NET: Registered protocol family 20
Jun 18 19:16:49 PC1 kernel: [   19.093107] PCI: Bridge: 0000:00:01.0
Jun 18 19:16:49 PC1 kernel: [   19.093109]   IO window: disabled.
Jun 18 19:16:49 PC1 kernel: [   19.093113]   MEM window: e8000000-e9ffffff
Jun 18 19:16:49 PC1 kernel: [   19.093117]   PREFETCH window: d0000000-dfffffff
Jun 18 19:16:49 PC1 kernel: [   19.093151] NET: Registered protocol family 2
Jun 18 19:16:49 PC1 kernel: [   19.132747] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 18 19:16:49 PC1 kernel: [   19.133003] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 18 19:16:49 PC1 kernel: [   19.134386] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 18 19:16:49 PC1 kernel: [   19.135069] TCP: Hash tables configured (established 131072 bind 65536)
Jun 18 19:16:49 PC1 kernel: [   19.135072] TCP reno registered
Jun 18 19:16:49 PC1 kernel: [   19.144778] checking if image is initramfs... it is
Jun 18 19:16:49 PC1 kernel: [   19.700791] Freeing initrd memory: 6785k freed
Jun 18 19:16:49 PC1 kernel: [   19.701212] audit: initializing netlink socket (disabled)
Jun 18 19:16:49 PC1 kernel: [   19.701227] audit(1182194178.360:1): initialized
Jun 18 19:16:49 PC1 kernel: [   19.701286] highmem bounce pool size: 64 pages
Jun 18 19:16:49 PC1 kernel: [   19.701346] VFS: Disk quotas dquot_6.5.1
Jun 18 19:16:49 PC1 kernel: [   19.701364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 18 19:16:49 PC1 kernel: [   19.701419] io scheduler noop registered
Jun 18 19:16:49 PC1 kernel: [   19.701421] io scheduler anticipatory registered
Jun 18 19:16:49 PC1 kernel: [   19.701423] io scheduler deadline registered
Jun 18 19:16:49 PC1 kernel: [   19.701431] io scheduler cfq registered (default)
Jun 18 19:16:49 PC1 kernel: [   19.788673] isapnp: Scanning for PnP cards...
Jun 18 19:16:49 PC1 kernel: [   20.141933] isapnp: No Plug & Play device found
Jun 18 19:16:49 PC1 kernel: [   20.160134] Real Time Clock Driver v1.12ac
Jun 18 19:16:49 PC1 kernel: [   20.160178] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 18 19:16:49 PC1 kernel: [   20.160283] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 19:16:49 PC1 kernel: [   20.160433] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 18 19:16:49 PC1 kernel: [   20.160831] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 19:16:49 PC1 kernel: [   20.161006] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun 18 19:16:49 PC1 kernel: [   20.161161] mice: PS/2 mouse device common for all mice
Jun 18 19:16:49 PC1 kernel: [   20.161604] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 18 19:16:49 PC1 kernel: [   20.161808] input: Macintosh mouse button emulation as /class/input/input0
Jun 18 19:16:49 PC1 kernel: [   20.161834] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 18 19:16:49 PC1 kernel: [   20.161837] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 18 19:16:49 PC1 kernel: [   20.162043] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 18 19:16:49 PC1 kernel: [   20.162206] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 18 19:16:49 PC1 kernel: [   20.162210] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 18 19:16:49 PC1 kernel: [   20.162299] EISA: Probing bus 0 at eisa.0
Jun 18 19:16:49 PC1 kernel: [   20.162308] Cannot allocate resource for EISA slot 1
Jun 18 19:16:49 PC1 kernel: [   20.162316] Cannot allocate resource for EISA slot 4
Jun 18 19:16:49 PC1 kernel: [   20.162330] EISA: Detected 0 cards.
Jun 18 19:16:49 PC1 kernel: [   20.192497] TCP cubic registered
Jun 18 19:16:49 PC1 kernel: [   20.192509] NET: Registered protocol family 1
Jun 18 19:16:49 PC1 kernel: [   20.192528] Using IPI No-Shortcut mode
Jun 18 19:16:49 PC1 kernel: [   20.192596] ACPI: (supports S0 S3 S4 S5)
Jun 18 19:16:49 PC1 kernel: [   20.192635]   Magic number: 11:88:294
Jun 18 19:16:49 PC1 kernel: [   20.192640]   hash matches device hpet
Jun 18 19:16:49 PC1 kernel: [   20.192665]   hash matches device ttyz8
Jun 18 19:16:49 PC1 kernel: [   20.192679]   hash matches device ttywb
Jun 18 19:16:49 PC1 kernel: [   20.192793]   hash matches device tty27
Jun 18 19:16:49 PC1 kernel: [   20.193235] Freeing unused kernel memory: 328k freed
Jun 18 19:16:49 PC1 kernel: [   20.196404] Time: tsc clocksource has been installed.
Jun 18 19:16:49 PC1 kernel: [   20.205374] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 18 19:16:49 PC1 kernel: [   21.418290] Capability LSM initialized
Jun 18 19:16:49 PC1 kernel: [   21.452941] ACPI: Fan [FAN] (on)
Jun 18 19:16:49 PC1 kernel: [   21.457623] ACPI: Thermal Zone [THRM] (30 C)
Jun 18 19:16:49 PC1 kernel: [   21.968618] usbcore: registered new interface driver usbfs
Jun 18 19:16:49 PC1 kernel: [   21.968639] usbcore: registered new interface driver hub
Jun 18 19:16:49 PC1 kernel: [   21.968658] usbcore: registered new device driver usb
Jun 18 19:16:49 PC1 kernel: [   21.969225] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 18 19:16:49 PC1 kernel: [   21.969256] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
Jun 18 19:16:49 PC1 kernel: [   21.969269] ohci_hcd 0000:00:03.0: OHCI Host Controller
Jun 18 19:16:49 PC1 kernel: [   21.969402] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jun 18 19:16:49 PC1 kernel: [   21.969418] ohci_hcd 0000:00:03.0: irq 16, io mem 0xea083000
Jun 18 19:16:49 PC1 kernel: [   22.030695] ieee1394: Initialized config rom entry `ip1394'
Jun 18 19:16:49 PC1 kernel: [   22.042837] SCSI subsystem initialized
Jun 18 19:16:49 PC1 kernel: [   22.058037] usb usb1: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   22.058062] hub 1-0:1.0: USB hub found
Jun 18 19:16:49 PC1 kernel: [   22.058075] hub 1-0:1.0: 3 ports detected
Jun 18 19:16:49 PC1 kernel: [   22.068058] libata version 2.20 loaded.
Jun 18 19:16:49 PC1 kernel: [   22.164039] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
Jun 18 19:16:49 PC1 kernel: [   22.164057] ohci_hcd 0000:00:03.1: OHCI Host Controller
Jun 18 19:16:49 PC1 kernel: [   22.164076] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jun 18 19:16:49 PC1 kernel: [   22.164093] ohci_hcd 0000:00:03.1: irq 17, io mem 0xea085000
Jun 18 19:16:49 PC1 kernel: [   22.198687] FDC 0 is a post-1991 82077
Jun 18 19:16:49 PC1 kernel: [   22.226879] usb usb2: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   22.226904] hub 2-0:1.0: USB hub found
Jun 18 19:16:49 PC1 kernel: [   22.226916] hub 2-0:1.0: 3 ports detected
Jun 18 19:16:49 PC1 kernel: [   22.331928] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
Jun 18 19:16:49 PC1 kernel: [   22.331946] ohci_hcd 0000:00:03.2: OHCI Host Controller
Jun 18 19:16:49 PC1 kernel: [   22.331965] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Jun 18 19:16:49 PC1 kernel: [   22.331983] ohci_hcd 0000:00:03.2: irq 18, io mem 0xea088000
Jun 18 19:16:49 PC1 kernel: [   22.393893] usb usb3: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   22.393916] hub 3-0:1.0: USB hub found
Jun 18 19:16:49 PC1 kernel: [   22.393927] hub 3-0:1.0: 2 ports detected
Jun 18 19:16:49 PC1 kernel: [   22.471787] usb 1-2: new low speed USB device using ohci_hcd and address 2
Jun 18 19:16:49 PC1 kernel: [   22.500631] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
Jun 18 19:16:49 PC1 kernel: [   22.500645] ehci_hcd 0000:00:03.3: EHCI Host Controller
Jun 18 19:16:49 PC1 kernel: [   22.500668] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
Jun 18 19:16:49 PC1 kernel: [   22.500699] PCI: cache line size of 64 is not supported by device 0000:00:03.3
Jun 18 19:16:49 PC1 kernel: [   22.500709] ehci_hcd 0000:00:03.3: irq 19, io mem 0xea082000
Jun 18 19:16:49 PC1 kernel: [   22.500717] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 18 19:16:49 PC1 kernel: [   22.500784] usb usb4: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   22.500806] hub 4-0:1.0: USB hub found
Jun 18 19:16:49 PC1 kernel: [   22.500813] hub 4-0:1.0: 8 ports detected
Jun 18 19:16:49 PC1 kernel: [   22.611569] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 18 19:16:49 PC1 kernel: [   22.611594] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 20
Jun 18 19:16:49 PC1 kernel: [   22.611723] eth0: RTL8169s/8110s at 0xf88c2000, 00:01:6c:2d:1a:9f, IRQ 20
Jun 18 19:16:49 PC1 kernel: [   22.614839] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 19 (level, low) -> IRQ 21
Jun 18 19:16:49 PC1 kernel: [   22.671348] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[ea086000-ea0867ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 18 19:16:49 PC1 kernel: [   22.676653] pata_sis 0000:00:02.5: version 0.5.1
Jun 18 19:16:49 PC1 kernel: [   22.691210] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
Jun 18 19:16:49 PC1 kernel: [   22.691253] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
Jun 18 19:16:49 PC1 kernel: [   22.691269] scsi0 : pata_sis
Jun 18 19:16:49 PC1 kernel: [   23.027923] ata1.00: ATAPI, max UDMA/33
Jun 18 19:16:49 PC1 kernel: [   23.029210] ata1.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 18 19:16:49 PC1 kernel: [   23.029213] ata1.01: ATA-6: WDC WD1200JB-00GVC0, 08.02D08, max UDMA/100
Jun 18 19:16:49 PC1 kernel: [   23.029216] ata1.01: 234441648 sectors, multi 16: LBA48 
Jun 18 19:16:49 PC1 kernel: [   23.195867] ata1.00: configured for UDMA/33
Jun 18 19:16:49 PC1 kernel: [   23.209075] ata1.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jun 18 19:16:49 PC1 kernel: [   23.209078] ata1.01: configured for UDMA/100
Jun 18 19:16:49 PC1 kernel: [   23.209086] scsi1 : pata_sis
Jun 18 19:16:49 PC1 kernel: [   23.368554] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-2510A  2.15 PQ: 0 ANSI: 5
Jun 18 19:16:49 PC1 kernel: [   23.368813] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
Jun 18 19:16:49 PC1 kernel: [   23.371047] sata_sis 0000:00:05.0: version 0.7
Jun 18 19:16:49 PC1 kernel: [   23.371073] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
Jun 18 19:16:49 PC1 kernel: [   23.371085] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
Jun 18 19:16:49 PC1 kernel: [   23.371126] ata3: SATA max UDMA/133 cmd 0x0001b800 ctl 0x0001bc02 bmdma 0x0001c800 irq 22
Jun 18 19:16:49 PC1 kernel: [   23.371151] ata4: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001c402 bmdma 0x0001c808 irq 22
Jun 18 19:16:49 PC1 kernel: [   23.371164] scsi2 : sata_sis
Jun 18 19:16:49 PC1 kernel: [   23.683481] ata3: SATA link down (SStatus 0 SControl 300)
Jun 18 19:16:49 PC1 kernel: [   23.693990] ATA: abnormal status 0x7F on port 0x0001b807
Jun 18 19:16:49 PC1 kernel: [   23.694014] scsi3 : sata_sis
Jun 18 19:16:49 PC1 kernel: [   23.835433] usb 1-2: new low speed USB device using ohci_hcd and address 3
Jun 18 19:16:49 PC1 kernel: [   23.963496] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20000623bb]
Jun 18 19:16:49 PC1 kernel: [   24.007398] ata4: SATA link down (SStatus 0 SControl 300)
Jun 18 19:16:49 PC1 kernel: [   24.017881] ATA: abnormal status 0x7F on port 0x0001c007
Jun 18 19:16:49 PC1 kernel: [   24.020203] sata_sil 0000:00:0e.0: version 2.2
Jun 18 19:16:49 PC1 kernel: [   24.020219] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 22
Jun 18 19:16:49 PC1 kernel: [   24.020282] ata5: SATA max UDMA/100 cmd 0xf88c6080 ctl 0xf88c608a bmdma 0xf88c6000 irq 22
Jun 18 19:16:49 PC1 kernel: [   24.020305] ata6: SATA max UDMA/100 cmd 0xf88c60c0 ctl 0xf88c60ca bmdma 0xf88c6008 irq 22
Jun 18 19:16:49 PC1 kernel: [   24.020313] scsi4 : sata_sil
Jun 18 19:16:49 PC1 kernel: [   24.038445] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jun 18 19:16:49 PC1 kernel: [   24.038451] Uniform CD-ROM driver Revision: 3.20
Jun 18 19:16:49 PC1 kernel: [   24.038606] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jun 18 19:16:49 PC1 kernel: [   24.038888] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 18 19:16:49 PC1 kernel: [   24.038898] sda: Write Protect is off
Jun 18 19:16:49 PC1 kernel: [   24.038900] sda: Mode Sense: 00 3a 00 00
Jun 18 19:16:49 PC1 kernel: [   24.038912] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 18 19:16:49 PC1 kernel: [   24.038946] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jun 18 19:16:49 PC1 kernel: [   24.038953] sda: Write Protect is off
Jun 18 19:16:49 PC1 kernel: [   24.038954] sda: Mode Sense: 00 3a 00 00
Jun 18 19:16:49 PC1 kernel: [   24.038965] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 18 19:16:49 PC1 kernel: [   24.038968]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Jun 18 19:16:49 PC1 kernel: [   24.043055] sd 0:0:1:0: Attached scsi generic sg1 type 0
Jun 18 19:16:49 PC1 kernel: [   24.054182] usb 1-2: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   24.058826]  sda1 sda2 sda3 < sda5 >
Jun 18 19:16:49 PC1 kernel: [   24.080432] sd 0:0:1:0: Attached scsi disk sda
Jun 18 19:16:49 PC1 kernel: [   24.287887] Attempting manual resume
Jun 18 19:16:49 PC1 kernel: [   24.287892] swsusp: Resume From Partition 8:5
Jun 18 19:16:49 PC1 kernel: [   24.287894] PM: Checking swsusp image.
Jun 18 19:16:49 PC1 kernel: [   24.288077] PM: Resume from disk failed.
Jun 18 19:16:49 PC1 kernel: [   24.320974] kjournald starting.  Commit interval 5 seconds
Jun 18 19:16:49 PC1 kernel: [   24.320986] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 19:16:49 PC1 kernel: [   24.335317] ata5: SATA link down (SStatus 0 SControl 310)
Jun 18 19:16:49 PC1 kernel: [   24.335335] scsi5 : sata_sil
Jun 18 19:16:49 PC1 kernel: [   24.371306] usb 1-3: new full speed USB device using ohci_hcd and address 4
Jun 18 19:16:49 PC1 kernel: [   24.647256] ata6: SATA link down (SStatus 0 SControl 310)
Jun 18 19:16:49 PC1 kernel: [   25.539105] usb 1-3: device descriptor read/64, error -62
Jun 18 19:16:49 PC1 kernel: [   30.810207] usb 1-3: device descriptor read/64, error -62
Jun 18 19:16:49 PC1 kernel: [   31.090171] usb 1-3: new full speed USB device using ohci_hcd and address 5
Jun 18 19:16:49 PC1 kernel: [   32.257901] usb 1-3: device descriptor read/64, error -62
Jun 18 19:16:49 PC1 kernel: [   34.253041] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 18 19:16:49 PC1 kernel: [   34.360750] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 18 19:16:49 PC1 kernel: [   34.419580] Linux agpgart interface v0.102 (c) Dave Jones
Jun 18 19:16:49 PC1 kernel: [   34.420782] agpgart: Detected AGP bridge 0
Jun 18 19:16:49 PC1 kernel: [   34.424804] agpgart: AGP aperture is 128M @ 0xe0000000
Jun 18 19:16:49 PC1 kernel: [   34.722371] ieee80211_crypt: registered algorithm 'NULL'
Jun 18 19:16:49 PC1 kernel: [   34.730868] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jun 18 19:16:49 PC1 kernel: [   34.730872] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jun 18 19:16:49 PC1 kernel: [   34.772274] bcm43xx driver
Jun 18 19:16:49 PC1 kernel: [   34.772365] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 17 (level, low) -> IRQ 22
Jun 18 19:16:49 PC1 kernel: [   34.813918] logips2pp: Detected unknown logitech mouse model 89
Jun 18 19:16:49 PC1 kernel: [   34.904102] parport: PnPBIOS parport detected.
Jun 18 19:16:49 PC1 kernel: [   34.904145] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 18 19:16:49 PC1 kernel: [   34.997724] parport0: Printer, Canon BJC-250
Jun 18 19:16:49 PC1 kernel: [   35.028664] input: PC Speaker as /class/input/input2
Jun 18 19:16:49 PC1 kernel: [   35.222066] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 20
Jun 18 19:16:49 PC1 kernel: [   35.285660] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
Jun 18 19:16:49 PC1 kernel: [   35.545069] intel8x0_measure_ac97_clock: measured 58901 usecs
Jun 18 19:16:49 PC1 kernel: [   35.545073] intel8x0: clocking to 48000
Jun 18 19:16:49 PC1 kernel: [   37.528780] usb 1-3: device descriptor read/64, error -62
Jun 18 19:16:49 PC1 kernel: [   37.808705] usb 1-3: new full speed USB device using ohci_hcd and address 6
Jun 18 19:16:49 PC1 kernel: [   42.832827] usb 1-3: device descriptor read/8, error -110
Jun 18 19:16:49 PC1 kernel: [   42.957776] usb 1-3: device descriptor read/8, error -62
Jun 18 19:16:49 PC1 kernel: [   43.239920] usb 1-3: new full speed USB device using ohci_hcd and address 7
Jun 18 19:16:49 PC1 kernel: [   48.264193] usb 1-3: device descriptor read/8, error -110
Jun 18 19:16:49 PC1 kernel: [   48.389142] usb 1-3: device descriptor read/8, error -62
Jun 18 19:16:49 PC1 kernel: [   48.799100] usb 3-1: new low speed USB device using ohci_hcd and address 2
Jun 18 19:16:49 PC1 kernel: [   49.005982] usb 3-1: configuration #1 chosen from 1 choice
Jun 18 19:16:49 PC1 kernel: [   49.017061] usbcore: registered new interface driver hiddev
Jun 18 19:16:49 PC1 kernel: [   49.081932] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /class/input/input4
Jun 18 19:16:49 PC1 kernel: [   49.081965] input: USB HID v1.00 Joystick [Dual PSX-USB Adaptor  Dual PSX-USB Adaptor ] on usb-0000:00:03.0-2
Jun 18 19:16:49 PC1 kernel: [   49.093919] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /class/input/input5
Jun 18 19:16:49 PC1 kernel: [   49.093943] input: USB HID v1.00 Joystick [Dual PSX-USB Adaptor  Dual PSX-USB Adaptor ] on usb-0000:00:03.2-1
Jun 18 19:16:49 PC1 kernel: [   49.093953] usbcore: registered new interface driver usbhid
Jun 18 19:16:49 PC1 kernel: [   49.093956] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 18 19:16:49 PC1 kernel: [   49.169693] usbcore: registered new interface driver xpad
Jun 18 19:16:49 PC1 kernel: [   49.169697] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jun 18 19:16:49 PC1 kernel: [   49.360553] lp0: using parport0 (interrupt-driven).
Jun 18 19:16:49 PC1 kernel: [   49.411850] Adding 1156640k swap on /dev/disk/by-uuid/9d237c4a-bb25-4c5f-b4cf-4bb66e6c2dda.  Priority:-1 extents:1 across:1156640k
Jun 18 19:16:49 PC1 kernel: [   49.520700] EXT3 FS on sda2, internal journal
Jun 18 19:16:49 PC1 kernel: [   50.117090] ibm_acpi: ec object not found
Jun 18 19:16:49 PC1 kernel: [   50.199246] input: Power Button (FF) as /class/input/input6
Jun 18 19:16:49 PC1 kernel: [   50.203415] ACPI: Power Button (FF) [PWRF]
Jun 18 19:16:49 PC1 kernel: [   50.230676] input: Power Button (CM) as /class/input/input7
Jun 18 19:16:49 PC1 kernel: [   50.234783] ACPI: Power Button (CM) [PWRB]
Jun 18 19:16:49 PC1 kernel: [   50.261897] input: Sleep Button (CM) as /class/input/input8
Jun 18 19:16:49 PC1 kernel: [   50.266031] ACPI: Sleep Button (CM) [FUTS]
Jun 18 19:16:49 PC1 kernel: [   50.324703] No dock devices found.
Jun 18 19:16:49 PC1 kernel: [   50.344382] Using specific hotkey driver
Jun 18 19:16:49 PC1 kernel: [   50.414898] pcc_acpi: loading...
Jun 18 19:16:49 PC1 kernel: [   50.606580] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
Jun 18 19:16:49 PC1 kernel: [   50.606626] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Jun 18 19:16:49 PC1 kernel: [   50.606640] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Jun 18 19:16:49 PC1 kernel: [   50.606642] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
Jun 18 19:16:49 PC1 kernel: [   50.606645] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
Jun 18 19:16:49 PC1 kernel: [   50.606647] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
Jun 18 19:16:52 PC1 kernel: [   53.764931] r8169: eth1: link down
Jun 18 19:16:52 PC1 kernel: [   53.882623] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


Unfortunately, I cannot provide the other file. When I enter:
```
cp ~/.xsession-errors stick//
```
I get the error message:
> cp: cannot stat '/root/xsession-errors': No such file or directory
I'm going to try it again though as I'm now paranoid about my spelling!

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-18
Do you done this from Recovery mode? I suppose so, since you are root.
Better to turn gdm off and start on normal mode (will take you to a console)
do:
```
sudo mv /etc/rc5.d/S*gdm /etc/
```
then reboot (normally, no Recovery) and when you hit a console (you may need to press CTRL+ALt+F1) login as normal user.

You can then add then ~/.xsession-errors.

In a quick look theres nothing look bad on kern.log. 
You may need to add one that contains the logs of a frozen.
Try post this 2:
/var/log/messages 
and
/var/log/Xorg.0.log

I have to go to bed now. It's late here. I'll give an eye on your logs by the morning, or some other user.
Don't horry with asking many questions. 
Is good that you search around and try, of course, but let me telling, yours is not a simple or easy issue. 
Check my tip on auto-login 2 posts above. It avoids most of typing errors on console.

good luck (don't give up)

---

### Post by SDL on 2007-06-19
Yes, the previous data was from recovery mode.

I had a problem with turning off gdm using:
```
sudo mv /etc/rc5.d/S*gdm /etc/
```

I got the error message:
> mv: cannot stat '/etc/rc5.d/S*gdm' No such file or directory.

I used 'Tab' to attempt to make sure my spelling was right but the furthest I could get with it was:
> sudo mv /etc/rc5.d/README

When I pressed tab again, the following prefixes were suggested:
> .bash_history
.profile
.bash_logout
stick/
.bashrc
.sudo_as_admin_successful

I probably won't be able to post again until around this time tomorrow. Thanks for all the help.

Stephen.

---

### Post by Rui Pais on 2007-06-19
Hi,
thats strange. 
Anyway, now that i come to think of it i'm not sure the default boot level is 5 or 2... try to search for SXXgdm either on rc2.d and rc5.d and move them (temporarily) to /etc/.

Another way is installing an very useful app, sysv-rc-conf that make turn those things on/off very easy. 
You can download the deb from the net to your stick and install it with dpkg -i.
Btw, do your router support wired connection? If so (and most do) it's just a case of connect a cable and you should have internet, since your net card is loaded by the kernel and router is already config.

But the important thing now is check your **/var/log/messages** and **/var/log/Xorg.0.log**.

---

### Post by penvzila on 2007-06-19
> **SDL said:**
> Thanks for your reply. I'm still reading through the link you sent me, so I'll let you know how I get on.

One interesting detail about what I'm experiencing is it seems to differ from most other accounts as the freezes are not transient and the PC is completely unresponsive, even using ALT-SysRq-O.

I should also mention that I have now abandoned the LiveCD and installed the alternated CD 32-bit Ubuntu 7.04 onto a partitioned drive. So, I'm now capable of using Recovery mode at least!

That's pretty much where I'm at.  I can use recovery mode to install some NVIDIA drivers, and then start gdm.  But the next time, I have to do it all over again.  Trying to boot the kernel normally gives me the "failed to allocate resource mem" error.

---

### Post by SDL on 2007-06-20
Hi. More problems! I successfully used:
```
sudo mv /etc/rc2.d/S*gdm /etc/
```

Problem is now when Ubuntu loads, it gets stuck on the loading screen when the bar reaches about 80% of the way across. I undid the move and the new problem resolved.

I then redid the move and pressed Ctrl-Alt-F1 during the loading screen. The PC became completely unresponsive (presumably at about 80% loaded again), the last line of text was:
> Running local boot scripts (/etc/rc.local)
After this point I had to use the power button on the case to turn off the PC.

I tried to open both of the files you requested from Recovery mode:
/var/log/messages
and
/var/log/Xorg.0.log
but I got similar messages for both:
bash: /var/log/messages: Permission denied

I typed in /var/log/ and pressed Tab and the options I was given were:
bittorent/
fsck/
news/
cups/
gdm/
samba/
dist-upgrade/
installer/
unattended-upgrade/

Penvzila, which Nvidia drivers do you install? Maybe I could try doing what you do and seeing if we have exactly the same problem?

Thanks.

Stephen.

---

### Post by SDL on 2007-06-20
Sorry, I'm about to double post but I realise I failed to answer some of Rui Pais' questions.

Unfortunately, I lack a long enough cable to have access to our router but I'm happy to persevere with the USB stick.

Would 'sysv-rc-conf' still be useful to me now that moving gdm didn't work?

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-20
Hi Stephen.
Well installing it would hurt. It's package it's [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fs%2Fsysv-rc-conf%2Fsysv-rc-conf_0.99-5_all.deb&md5sum=0707dbafdab52140fdffd12d22b89d4f&arch=all&type=main").
It can be installed with:```
sudo dpkg -i sysv-rc-conf*.deb
```

But the most important now is give a look at your logs. 
You couldn't read them with 'Permission denied' message. That means you nead administrative powers. 
When that happens you redo the command with sudo:
```
sudo cp /var/log/messages stick/
sudo cp /var/log/Xorg.0.log stick/
sudo cp /home/*your_user_name_here*/.xsession-errors stick/
```
replace *your_user_name_here* with your user name (that make things easier).

Some of them are a bit longer. You can add those here as attach instead of post  the all message.

After that we can try to install NVidia drivers and see if that work.

Good Luck.

---

### Post by SDL on 2007-06-20
Hi Rui. Sounds like a good plan.

I've zipped and attached the 'messages' and 'xorg.0.log' files. For.xsession-errors I get an error message saying 'no such file or directory.'

I tried to install sysv-rc-conf*.deb but got the following error message:
> dpkg: dependency problmes prevent configuration of sys-rc-conf: sys-rc-conf depends on libcurses-ui-perl; however: Package libcurses-ui-perl is not installed

Presumably I need to download and install 'libcurses-ui-perl'?

I hope those logs help. Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-20
hi,
i checked those logs. but they don't seems containing any message relative to a gnome session (broken or not).
You may have to check for older logs...

But lets try another approach. Xorg log have an error. Seems that it tried to load something related with glx.
Have you changed your /etc/X11/xorg.conf?

I think a best option is trying to install nvidia drivers and check if that make things more stable...

Here is an howto install:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

You can get off-line official ubuntu packages here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

Essentially you need to install this package:
[http://packages.ubuntu.com/feisty/x11/nvidia-glx](http://packages.ubuntu.com/feisty/x11/nvidia-glx)
in the page it's listed the dependencies, download because it may be needed:
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-common](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-common)
The others should be present already (i think) 

Install those packages with sudo dpkg -i
and then run (just for precaution:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
and reconfigure your xserver:
```
dpkg-reconfigure -phigh xserver-xorg
```
reboot normally  ( no Recovery mode)
and check what happens.

---

### Post by SDL on 2007-06-21
Hi Rui.

Starting with the good news, I managed to install sysv-rc-conf. For the sake of anybody following me, the extra packages I had to download were:
libcurses-ui-perl_0.95-5_all.deb
libcurses-perl_1.13-1_i386.deb
libterm-readkey-perl_2.30-3ubuntu1_i386.deb
I haven't used sys-rc-conf yet - is there anything I should do with it?

I also installed the Nvidia drivers as you suggested but the reboot caused the same problems as before. :(

I haven't changed my /etc/X11/xorg.conf except, presumably, when I installed the Nvidia drivers today. How would I go about finding my older logs? Is it possible that the crash occurs so suddenly that nothing is written to the logs?

Just to check with you, when I ran this command:
```
dpkg-reconfigure -phigh xserver-xorg
```
Should I have been required to configure anything myself? Whatever it did didn't ask me for any further input.

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-21
Hi Stephen.

So you got NVidia installed. Good! 

You should put now the moved S*gdm to original positions, to try with your new drivers.
But since you install sysv-rc-conf, things are a lot easier (couldn't all be bad :) )

Run:
```
sudo sysv-rc-conf
```
it will show a screen full of [ ] [ ] [ ], some with an X inside like, [X]. The services with X are the turned on.
Navigate with arrows of keyboard, till the line 'gdm' and ensure that columns 2, 3 4 and 5 have Xs (and only that ones!) 
Xs can be turned on/off with Space Bar. After that pres 'Q' key and it's done :)

The dpkg-reconfigure command with -phigh detects all automatically. So seems ok. You can check by type:
```
cat /etc/X11/xorg.conf | grep nvidia
```
that should output (maybe with other lines) this:
>  Driver         "nvidia"
If thats the case all seems correct.

And finally, the moment of truth:
```
sudo /etc/init.d/gdm start
```
Note that you should do this last command *not* in Recovery mode but with kernel boot normally, or will fail. 
The other commands could be done in either modes. 
If you can get to console in normal mode without crashes then opt by that :)

I wish all goes well.
Best of lucks.

---

### Post by SDL on 2007-06-21
Hi Rui.

No luck, it still crashes...

I moved gdm back to where it lives, then ran sysv-rc-conf and found that gdm only had X's in columns 2, 3, and 4 so I added column 5 (now gdm is the only app in which column 5 has an X - shall I post some photos of my sysv-rc-conf?)

I ran the command:
```
cat /etc/X11/xorg.conf | grep nvidia
```
but nothing happened, I'm going to try it again incase I got something wrong but I wasn't getting very far pressing Tab and I did double check it. :???:

Moving onto the boot itself. So when Ubuntu started, the loading screen appeared and I pressed Ctrl-Alt-F1, however, when the boot process finished, the login splash screen appeared and I had to press Ctrl-Alt-F1 again. At this point the standard crash occurred. The last line of text was:
> [28.468000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
From looking around on these forums, I think that bcm43 is something to do with my wireless card. I could disable it if that would help?

Good night.

Stephen.

---

### Post by Rui Pais on 2007-06-23
Hi, sorry the late answer (busy days...)
I'm in a run now, just a quick tips.

Apparently dpkg-reconfigure failed. So you still not tested Nvidia driver. 
It failed, but it was still on the original "nv".
From a console run:
```
sudo nano /etc/X11/xorg.conf
```
(not the X in X11 is a upper case)

using arroe keys search for the line
> Driver         "nv"
and replade by:
> Driver         "nvidia"

Press Ctrl+X
ans then Y to accept save changes.
run again:
```
sudo /etc/init.d/gdm restart
```
btw did your
```
dmesg | grep nvidia
```
outputs something (or an empty line?)

About sysv-rc-conf... yes it should have level 5 with a lot of Xs, like 2-4.
I'm not sure if default ubuntu level is 2 or 5. I'll check that later and post.
Can you post a pic of it?  

I' leave now for a few hours I catch later if you got time to try.

Best of luck.

---

### Post by SDL on 2007-06-23
Hi. Good news, I think.

I accidentally entered ```
sudo /etc/init.d/gdm start
``` whilst still in recovery mode and that worked really well. I had the desktop up and even managed a quick game of Sudoku, no crashes at all. Unfortunately, that doesn't solve the problem for when I'm not in recovery mode...

One point to note was that as the desktop came up the error message > Internal error Failed to initialize HAL! appeared, but I just pressed OK and continued with the session.

I ran dpkg-reconfigure again and checked /etc/X11/xorg.conf as you suggested, it seems OK to me, the driver was labelled as "nvidia."

Previously I ran the command```
cat /etc/X11/xorg.conf | grep nvidia
``` which was unsuccessful although I could have entered nvidia-xconfig, nvidia-settings, nvidia-bug report.sh, or nvidia-glx-config instead of plain 'nvidia.'

This time I ran ```
dmesg | grep nvidia
``` which gave me the message > [32.589517] nvidia: module license 'NVIDIA' taints kernel.

I've attached a picture of sysv-conf.

Don't worry about how long it takes you to reply, you've been amazing to help me this much. Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-23
Hi Stephen, good news indeed.
If you can load gdm and run session without crashes in recovery, that seems point to some initial service issue, probably activating (or trying) some obscure hardware.

About the nvidia. 
The dmesg (healthy) output, means that kernel finded and loaded the driver, so all is ok there (the taint warning is just to inform that he loaded a restricted license object that don't have code available. It's no longer an full open source Linux.)

The nvidia at xorg.conf is an indication for X server to run on nvidia. So when you run gdm start it will use that driver (the other driver, nv,  is build directly at kernel). 
Everything seems correct.

About services, i checked, and default Ubuntu one is 2. So i don't think the 5 will had any difference, but i never saw them deactivated... maybe it was a good idea use sysv-rc-conf to turn on 5 on any option that have the 2...4 with Xs (only those).

The HAL message could be a clue, yes. maybe reinstall it:
```
sudo aptitude reinstall hal hal-device-manager
``` 
i don't have great hopes for reinstalls... i have seen several time HAL warnings when all runs well... so, i don't no more about it.

Lets try to boot normally but passing some safe flags to kernel to see if it helps.

Boot your machine choose the normal entry (not the recovery) from boot menu and press '**E**' key.
you will see 3 or 4 lines on your screen. Use Arrow Keys of keyboard and select the one start with the word 'kernel'. Press '**E**' again (is E for Edit ;)). 
Go to end of line and type (carefully) this words separated by spaces:
```
 noapic nolapic
```
Then press Enter and then '**B**' (for boot).

if it still crashes repeat again but this time use this:
```
 acpi=off 
```

That will make your kernel load less things some of them know for being a problem for some hardware.
Good Luck.

---

### Post by SDL on 2007-06-23
Hi Rui. It works!

Using ```
acpi=off
``` worked perfectly. No error messages, crashes or anything else. The other line of code didn't solve the problem.

Where do I go from here? Presumably I shouldn't need to enter acpi=off every time I use Ubuntu?

Thanks.

Stephen.

---

### Post by Rui Pais on 2007-06-23
> **SDL said:**
> Hi Rui. It works!

Using ```
acpi=off
``` worked perfectly. No error messages, crashes or anything else. The other line of code didn't solve the problem.

Where do I go from here? Presumably I shouldn't need to enter acpi=off every time I use Ubuntu?

Thanks.

Stephen.

He he. We catch the thing :)
Excellent. 

Acpi is the power control stuff. You can live happy without it :)
 
Now let see the best way to do it.

Try first run sysv-rc-conf and turn off all Xs in the first 2 lines, the acpi-support and acpid. 
And reboot without add nothing to kernel line.
Check if crashes. 
This is easier, but i suspect you will get crashes...
If so, you will need to edit grub options. 
I'll tell you how to do it if need, ok?

Congratulations for your working system.  :D

---

### Post by SDL on 2007-06-23
Hi Rui.

Unfortunately, the sysv-conf method has been unsuccessful. Please could you let me know about the grub method?

And the congratulations are all yours, I'd have given up long ago without your help.

Stephen.

---

### Post by Rui Pais on 2007-06-23
No problem, glad i could help :)

And you been a persistent user, most people would get scared with one third of so many line commands :p.

So, editing will be more easy with a gui... best reboot with the acpi=off on the kernel line.

Do:
```
gksudo gedit /boot/grub/menu.lst
```

search for the line that you have been editing manually and add the same acpi=off.

After that search for the line:
# defoptions
it should say something like:
> # defoptions=quiet splash
add to the acpi=off at the end to the other options (DO NOT REMOVE the # from the beginning!)
> # defoptions=quiet splash acpi=off
That will automatically add that option in any future updates or new kernels :)

And thats all.

Btw, the livecds can be boot with same option, if you face any problems of the kind in the future.
In one of my boxes, sometimes i have to give that option to some versions and others work normally without it... i think it changes with acpi versions of each Ubuntu or LiveCD i use with it...

Glad i could help you.
If you get into problems with the above instructions post about it.

Have fun :D

---

### Post by SDL on 2007-06-23
I've run into a slight hitch. Still works perfectly when I manually enter acpi=off but editing menu.lst hasn't worked. :(

Next time I booted up the PC after changing the file, I typed the first two letters of my username and it crashed. I've posted a screenshot of my menu.lst, have I done something wrong?

Thanks.

Stephen.

---

### Post by Liakath on 2007-06-23
> **SDL said:**
> I've run into a slight hitch. Still works perfectly when I manually enter acpi=off but editing menu.lst hasn't worked. :(

Next time I booted up the PC after changing the file, I typed the first two letters of my username and it crashed. I've posted a screenshot of my menu.lst, have I done something wrong?

Thanks.

Stephen.

Ignore my post Sorry I think I got a little confused

---

### Post by Rui Pais on 2007-06-23
hi again Stephen,
That part on your pic is correct.

Did you changed, too, the line:
```
kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=xxxxxxxxxxxxxxx ro quiet splash
```
to 
```
kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=xxxxxxxxxxxxxxx ro quiet splash acpi=off
```

it not means the must be exactly like that but the equivalent. The one thats starts with word kernel and has the quiet and splash options?

---

### Post by SDL on 2007-06-23
Hi Rui.

I have now! I'm currently writing this from my fully-functioning installation of Ubuntu 7.04 which didn't require any tampering with as it loaded up flawlessly - well except that I had to select it as I've decided to keep XP as my default for now!

Thank you so much for sorting out all my problems. See you around.

Stephen.

---

### Post by Rui Pais on 2007-06-23
Glad is Ok :)

See you Stephen.

---

