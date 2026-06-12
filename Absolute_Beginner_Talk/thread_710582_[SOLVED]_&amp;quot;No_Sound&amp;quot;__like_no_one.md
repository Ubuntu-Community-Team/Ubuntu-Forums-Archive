---
title: "[SOLVED] &amp;quot;No Sound&amp;quot;  like no one has heard that one before"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-02-28
Sound if obviously a problen with ubuntu. I have a ECS 945GCT-M mother board. Sound works fine with windows.

lspci -v reports Intel 82801G (ICH7 Family) High Definition Audio Controller

AlsaMixer shows SignaTel STAC9221 A2 chip. Everything turned up to 100% except IEC985 is off and I can't turn it on. Whatever it is??

In any case no sound what so ever.

Thanks

P.S. I did a search but turned up so many results I didn't know what to read first

---

### Post by Crooksey on 2008-02-28
```

$ sudo alsaconf
```

Try reconfiguring.

---

### Post by gorgon on 2008-02-28
first place to look would be [www.alsa-project.org](www.alsa-project.org) . The card seems to be supported, but others have had issues as well, but solved it:
[http://www.linuxquestions.org/questions/linux-hardware-18/sound-card-not-detected-intel-82801g-alsa-1.0.14-561009/](http://www.linuxquestions.org/questions/linux-hardware-18/sound-card-not-detected-intel-82801g-alsa-1.0.14-561009/)

does the link make sense to you?

good luck!

---

### Post by Crooksey on 2008-02-28
Sorry, got confuesd with two threads about alsa :)

---

### Post by linuxjerk on 2008-02-28
Yes that link does look very familiar to me. But my system is not saying sound card not found.

I think that maybe the wrong drivers are being loaded.

It finds the intel hda audio device and it's listed in the device manager.

Just no sound is being produced.

Some of this is going way over my head.

Can someone walk me through this??

---

### Post by linuxjerk on 2008-02-28
If this was running under windows I would have had it working hours ago.

Linux will probably take days.....

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

dennis@dennis-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 945G/GZ Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2950
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at d880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at d480 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 217
        Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 8136
        Flags: bus master, fast devsel, latency 0, IRQ 177
        I/O ports at e800 [size=256]
        Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by Dr.Gringo on 2008-02-28
You might want to check this link.

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by linuxjerk on 2008-02-28
So basicly what that link is saying is sound will never work in edgy or will be so difficult don't bother?

Sure wish linux would get it's act together

---

### Post by SunnyRabbiera on 2008-02-28
> **linuxjerk said:**
> So basicly what that link is saying is sound will never work in edgy or will be so difficult don't bother?

Sure wish linux would get it's act together

I would blame the sound card maker before I would blame linux personally...

---

### Post by linuxjerk on 2008-02-28
Why shouldn't I blame linux? Every soundcard I've ever used has worked on windows.

---

### Post by xeth_delta on 2008-02-28
> **linuxjerk said:**
> So basicly what that link is saying is sound will never work in edgy or will be so difficult don't bother?

Sure wish linux would get it's act together

First, please try to relax a little. Most of these problems can be solved with some tinkering :)
I am not sure how much development is being put into Edgy anymore taking into account that it is already two generations behind, and it is not a Long Time Support version.

In any case let's try to get it working. It is not a matter of getting the act together, but you have to understand that many hardware producers do not disclose the hardware specifications and hence it is more difficult to develop drivers for them. It might take a while or priority be allocated for newer versions of the same driver.

I had a look at the last link and I could not find anything about Edgy.

The problem you have might have something to do with the module load parameters being incorrectly configured. In the worst case I guess you might need to recompile the alsa drivers from the alsa website. It is not difficult and we can help you through the process.

One more thing, about the Windows comment, I would like to add a little idea from my own experience, it is just my opinion. In Linux, if you have a problem with some device, you can search over the internet information, or ask in forums. Given the transparent structure of the system it has been possible for me to pin-point a problem's cause and fix it.
In any case, even if it can be a bit time consuming, one can fix the problem in the end, in Windows, many things work out of the box, but when something does not... good luck! I have had serious difficulties identifying the roots of the problems and then even trying to solve them, given how closed the system is.

Ok, back to the topic. Open a terminal and do the following:
```
sudo modprobe snd-hda-intel
```
then:
```
dmesg
```
post the last lines or any line referring to the sound card.

---

### Post by northern lights on 2008-02-28
Intel ICH7 family sound devices usually run smoothly in Gutsy - any particular reason you wanna stick to Edgy?

---

### Post by xeth_delta on 2008-02-28
> **linuxjerk said:**
> Why shouldn't I blame linux? Every soundcard I've ever used has worked on windows.

Read my previous post. In Windows the drivers are not developed by Microsoft. They throw that burden on the hardware producers or third parties.

In Linux, drivers are developed by the FOSS community, many times without the help of the hardware manufacturers. As I said, many times they do not release specifications. With this in mind, writing drivers from scratch for such a multitude of cards (with most of them working without issues) is a remarcable feat of coding.

Please calm down and let's maintain the level of the discussion civil

Xeth

---

### Post by SunnyRabbiera on 2008-02-28
> **linuxjerk said:**
> Why shouldn't I blame linux? Every soundcard I've ever used has worked on windows.

thats because most soundcard makers look at windows first...
Its not our fault bud that those who make crap like that ignore linux, you are asking us to become miracle workers...
Linux developers can only do so much, but it takes commitment from BOTH sides to get things cracking

---

### Post by linuxjerk on 2008-02-28
Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 945G/GZ Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2950
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at d880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at d480 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 217
        Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2624
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 8136
        Flags: bus master, fast devsel, latency 0, IRQ 177
        I/O ports at e800 [size=256]
        Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>

dennis@dennis-desktop:~$ sudo modprobe snd-hda-intel
Password:
dennis@dennis-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.17-10-generic/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        
srcversion:     C2D094BCAA551D6738DF488
dennis@dennis-desktop:~$ sudo modrobe snd-hda-intel
Password:
sudo: modrobe: command not found
dennis@dennis-desktop:~$ sudo modprobe snd-hda-intel
dennis@dennis-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007f7b0000 (usable)
[17179569.184000]  BIOS-e820: 000000007f7b0000 - 000000007f7be000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007f7be000 - 000000007f7f0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 1143MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 522160
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 292784 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 synnex                                ) @ 0x000fa180
[17179569.184000] ACPI: RSDT (v001 AAMMII OEMRSDTA 0x11000707 MSFT 0x00000097) @ 0x7f7b0000
[17179569.184000] ACPI: FADT (v002 AAMMII OEMFACP  0x11000707 MSFT 0x00000097) @ 0x7f7b0200
[17179569.184000] ACPI: MADT (v001 AAMMII OEMAPIC  0x11000707 MSFT 0x00000097) @ 0x7f7b0390
[17179569.184000] ACPI: MCFG (v001 AAMMII OEMMCFG  0x11000707 MSFT 0x00000097) @ 0x7f7b0400
[17179569.184000] ACPI: OEMB (v001 AAMMII AMI_OEM  0x11000707 MSFT 0x00000097) @ 0x7f7be040
[17179569.184000] ACPI: HPET (v001 AAMMII OEMHPET  0x11000707 MSFT 0x00000097) @ 0x7f7b5420
[17179569.184000] ACPI: DSDT (v001  945GM   945GM2 0x00000002 INTL 0x20051117) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:3 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:3 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 2060908k/2088640k available (1910k kernel code, 26516k reserved, 1070k data, 308k init, 1171136k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2992.664 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 5990.49 BogoMIPS (lpj=11980988)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000441d 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.728000] Freeing initrd memory: 5563k freed
[17179569.728000] ACPI: Core revision 20060707
[17179569.728000] ACPI: Looking for DSDT ... not found!
[17179569.740000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[17179569.740000] SMP alternatives: switching to SMP code
[17179569.740000] Booting processor 1/1 eip 3000
[17179569.752000] Initializing CPU#1
[17179569.832000] Calibrating delay using timer specific routine.. 5985.21 BogoMIPS (lpj=11970437)
[17179569.832000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.832000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.832000] monitor/mwait feature present.
[17179569.832000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.832000] CPU: L2 cache: 1024K
[17179569.832000] CPU: Hyper-Threading is disabled
[17179569.832000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000441d 00000000 00000000
[17179569.832000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[17179569.832000] Total of 2 processors activated (11975.71 BogoMIPS).
[17179569.832000] ENABLING IO-APIC IRQs
[17179569.832000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.984000] checking TSC synchronization across 2 CPUs: passed.
[17179569.988000] Brought up 2 CPUs
[17179570.124000] migration_cost=8000
[17179570.124000] NET: Registered protocol family 16
[17179570.124000] EISA bus registered
[17179570.124000] ACPI: bus type pci registered
[17179570.124000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179570.124000] PCI: Not using MMCONFIG.
[17179570.124000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[17179570.124000] PCI: Using configuration type 1
[17179570.124000] Setting up standard PCI resources
[17179570.140000] ACPI: Interpreter enabled
[17179570.140000] ACPI: Using IOAPIC for interrupt routing
[17179570.140000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.140000] PCI: Probing PCI hardware (bus 00)
[17179570.144000] Boot video device is 0000:00:02.0
[17179570.148000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.148000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.148000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.160000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.172000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179570.172000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[17179570.172000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.172000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.172000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[17179570.172000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.176000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.176000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.176000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.176000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.176000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.176000] pnp: PnP ACPI init
[17179570.184000] pnp: PnP ACPI: found 19 devices
[17179570.184000] PnPBIOS: Disabled by ACPI PNP
[17179570.184000] PCI: Using ACPI for IRQ routing
[17179570.184000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.192000] pnp: 00:0f: ioport range 0xa00-0xa0f has been reserved
[17179570.192000] pnp: 00:0f: ioport range 0xa10-0xa1f has been reserved
[17179570.192000] pnp: 00:0f: ioport range 0xa20-0xa2f has been reserved
[17179570.192000] pnp: 00:0f: ioport range 0xa30-0xa3f has been reserved
[17179570.192000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.192000] PCI: Bridge: 0000:00:1c.0
[17179570.192000]   IO window: disabled.
[17179570.192000]   MEM window: disabled.
[17179570.192000]   PREFETCH window: disabled.
[17179570.192000] PCI: Bridge: 0000:00:1c.3
[17179570.192000]   IO window: e000-efff
[17179570.192000]   MEM window: feb00000-febfffff
[17179570.192000]   PREFETCH window: disabled.
[17179570.192000] PCI: Bridge: 0000:00:1e.0
[17179570.192000]   IO window: disabled.
[17179570.192000]   MEM window: disabled.
[17179570.192000]   PREFETCH window: disabled.
[17179570.192000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.192000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.192000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.192000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.192000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.192000] NET: Registered protocol family 2
[17179570.240000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.240000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179570.240000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.240000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.240000] TCP reno registered
[17179570.240000] audit: initializing netlink socket (disabled)
[17179570.240000] audit(1204294073.240:1): initialized
[17179570.240000] highmem bounce pool size: 64 pages
[17179570.240000] VFS: Disk quotas dquot_6.5.1
[17179570.240000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.240000] Initializing Cryptographic API
[17179570.240000] io scheduler noop registered
[17179570.240000] io scheduler anticipatory registered
[17179570.240000] io scheduler deadline registered
[17179570.240000] io scheduler cfq registered (default)
[17179570.240000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.240000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.240000] assign_interrupt_mode Found MSI capability
[17179570.240000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.240000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.240000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.240000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.240000] assign_interrupt_mode Found MSI capability
[17179570.240000] Allocate Port Service[0000:00:1c.3:pcie00]
[17179570.240000] Allocate Port Service[0000:00:1c.3:pcie02]
[17179570.240000] isapnp: Scanning for PnP cards...
[17179570.596000] isapnp: No Plug & Play device found
[17179570.620000] Real Time Clock Driver v1.12ac
[17179570.624000] hpet_resources: 0xfed00000 is busy
[17179570.624000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.624000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.624000] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.624000] mice: PS/2 mouse device common for all mice
[17179570.624000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.624000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.624000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.624000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179570.624000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.624000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.624000] EISA: Probing bus 0 at eisa.0
[17179570.624000] EISA: Detected 0 cards.
[17179570.624000] TCP bic registered
[17179570.624000] NET: Registered protocol family 1
[17179570.624000] NET: Registered protocol family 8
[17179570.624000] NET: Registered protocol family 20
[17179570.624000] Starting balanced_irq
[17179570.624000] Using IPI No-Shortcut mode
[17179570.624000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.624000] Freeing unused kernel memory: 308k freed
[17179570.644000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.708000] Capability LSM initialized
[17179571.748000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.748000] ACPI: Getting cpuindex for acpiid 0x3
[17179571.748000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.748000] ACPI: Getting cpuindex for acpiid 0x4
[17179571.748000] ACPI: Thermal Zone [THRM] (40 C)
[17179572.160000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179572.160000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 209
[17179572.160000] ICH7: chipset revision 1
[17179572.160000] ICH7: not 100% native mode: will probe irqs later
[17179572.160000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.160000] Probing IDE interface ide0...
[17179572.900000] hda: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[17179573.688000] hdb: ATAPI 52X CDROM, ATAPI CD/DVD-ROM drive
[17179573.748000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.772000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179573.772000] Uniform CD-ROM driver Revision: 3.20
[17179573.776000] hdb: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[17179573.872000] SCSI subsystem initialized
[17179573.872000] libata version 1.20 loaded.
[17179573.876000] ata_piix 0000:00:1f.2: version 1.05
[17179573.876000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 177
[17179573.876000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179573.876000] ata1: SATA max UDMA/133 cmd 0xD080 ctl 0xD002 bmdma 0xC800 irq 177
[17179573.876000] ata2: SATA max UDMA/133 cmd 0xCC00 ctl 0xC882 bmdma 0xC808 irq 177
[17179574.048000] ata1: dev 0 cfg 49:2f00 82:306b 83:7c01 84:4123 85:3069 86:3c01 87:4023 88:203f
[17179574.048000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179574.060000] ata1: dev 0 configured for UDMA/100
[17179574.060000] scsi0 : ata_piix
[17179574.228000] ata2: disabling port
[17179574.228000] scsi1 : ata_piix
[17179574.228000]   Vendor: ATA       Model: ST380815AS        Rev: 3.CH
[17179574.228000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.236000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179574.236000] sda: Write Protect is off
[17179574.236000] sda: Mode Sense: 00 3a 00 00
[17179574.236000] SCSI device sda: drive cache: write back
[17179574.236000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179574.236000] sda: Write Protect is off
[17179574.236000] sda: Mode Sense: 00 3a 00 00
[17179574.236000] SCSI device sda: drive cache: write back
[17179574.236000]  sda: sda1 sda2 < sda5 >
[17179574.280000] sd 0:0:0:0: Attached scsi disk sda
[17179574.428000] Probing IDE interface ide1...
[17179574.464000] usbcore: registered new driver usbfs
[17179574.464000] usbcore: registered new driver hub
[17179574.488000] USB Universal Host Controller Interface driver v3.0
[17179574.488000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[17179574.488000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.488000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.488000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.488000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x0000d880
[17179574.488000] usb usb1: configuration #1 chosen from 1 choice
[17179574.488000] hub 1-0:1.0: USB hub found
[17179574.488000] hub 1-0:1.0: 2 ports detected
[17179574.596000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
[17179574.596000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.596000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.596000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.596000] uhci_hcd 0000:00:1d.1: irq 177, io base 0x0000d800
[17179574.596000] usb usb2: configuration #1 chosen from 1 choice
[17179574.596000] hub 2-0:1.0: USB hub found
[17179574.596000] hub 2-0:1.0: 2 ports detected
[17179574.704000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179574.704000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.704000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.704000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179574.704000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000d480
[17179574.704000] usb usb3: configuration #1 chosen from 1 choice
[17179574.704000] hub 3-0:1.0: USB hub found
[17179574.704000] hub 3-0:1.0: 2 ports detected
[17179574.812000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179574.812000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.812000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179574.812000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179574.812000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000d400
[17179574.812000] usb usb4: configuration #1 chosen from 1 choice
[17179574.812000] hub 4-0:1.0: USB hub found
[17179574.812000] hub 4-0:1.0: 2 ports detected
[17179574.920000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
[17179574.920000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.920000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.920000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179574.920000] ehci_hcd 0000:00:1d.7: debug port 1
[17179574.920000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179574.920000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xfea37c00
[17179574.924000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.924000] usb usb5: configuration #1 chosen from 1 choice
[17179574.924000] hub 5-0:1.0: USB hub found
[17179574.924000] hub 5-0:1.0: 8 ports detected
[17179575.060000] Attempting manual resume
[17179575.096000] kjournald starting.  Commit interval 5 seconds
[17179575.096000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.308000] input: PC Speaker as /class/input/input1
[17179582.372000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179582.376000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179582.764000] hw_random: RNG not detected
[17179582.784000] Linux agpgart interface v0.101 (c) Dave Jones
[17179582.788000] agpgart: Detected an Intel 945G Chipset.
[17179582.788000] agpgart: Detected 7932K stolen memory.
[17179582.804000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179582.864000] Floppy drive(s): fd0 is 1.44M
[17179582.884000] parport: PnPBIOS parport detected.
[17179582.884000] parport0: PC-style at 0x378 (0x778), irq 7<6>FDC 0 is a post-1991 82077
[17179582.888000] , dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179582.976000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179582.976000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179582.976000] eth0: Identified chip type is 'RTL8101E'.
[17179582.976000] eth0: r10001.02, the Linux device driver for Realtek Ethernet Controllers at 0xe800, 00:1e:90:6d:58:f9, IRQ 177
[17179582.976000] eth0: Auto-negotiation Enabled.
[17179584.500000] eth0: 100Mbps Full-duplex operation.
[17179584.500000] Realtek RTL8139/810x Family Fast Ethernet Network Adapter
[17179584.500000] Driver version:1.02
[17179584.500000] Released date:2006/02/23
[17179584.500000] Link Status:Linked
[17179584.500000] Link Speed:100Mbps
[17179584.500000] Duplex mode:Full-Duplex
[17179584.500000] I/O Base:0xE800(I/O port)
[17179584.500000] IRQ:177
[17179584.712000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179584.712000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179584.808000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.188000] input: PS/2 Generic Mouse as /class/input/input2
[17179585.208000] ts: Compaq touchscreen protocol output
[17179585.476000] lp0: using parport0 (interrupt-driven).
[17179585.508000] Adding 3196892k swap on /dev/disk/by-uuid/166705ac-eff3-459d-9d22-eeb252e77b63.  Priority:-1 extents:1 across:3196892k
[17179585.560000] EXT3 FS on sda1, internal journal
[17179585.892000] NET: Registered protocol family 17
[17179591.216000] ACPI: Power Button (FF) [PWRF]
[17179591.216000] ACPI: Power Button (CM) [PWRB]
[17179591.356000] ibm_acpi: ec object not found
[17179591.400000] pcc_acpi: loading...
[17179593.536000] NET: Registered protocol family 10
[17179593.536000] lo: Disabled Privacy Extensions
[17179593.536000] IPv6 over IPv4 tunneling driver
[17179594.268000] [drm] Initialized drm 1.0.1 20051102
[17179594.272000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.272000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179594.708000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179594.708000] apm: disabled - APM is not SMP safe.
[17179597.912000] Bluetooth: Core ver 2.8
[17179597.912000] NET: Registered protocol family 31
[17179597.912000] Bluetooth: HCI device and connection manager initialized
[17179597.912000] Bluetooth: HCI socket layer initialized
[17179598.128000] Bluetooth: L2CAP ver 2.8
[17179598.128000] Bluetooth: L2CAP socket layer initialized
[17179598.228000] Bluetooth: RFCOMM socket layer initialized
[17179598.228000] Bluetooth: RFCOMM TTY layer initialized
[17179598.228000] Bluetooth: RFCOMM ver 1.7
[17179604.484000] eth0: no IPv6 routers present
dennis@dennis-desktop:~$

---

### Post by xeth_delta on 2008-02-28
I don't see the lines I was looking for. I am trying to identify what codec the sound card uses. Try:
```
dmesg | grep -i hda
```
or
```
dmesg | grep -i codec
```
For example, in my computer it looks like:
```
[   16.232000] hda_codec: STAC922x, Apple subsys_id=106b2200
[   47.432000] hda_codec: STAC922x, Apple subsys_id=106b2200

```
where STAC922x is the codec used in the card. With this information in hand, one can read in the alsa documentation what parameters should be used.

[EDIT] Please do use the CODE tags and place the output between them. In the posting page you will see a "#" button.

---

### Post by linuxjerk on 2008-02-28
dennis@dennis-desktop:~$ dmesg | grep -i hda
[17179572.160000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.900000] hda: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[17179573.772000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
dennis@dennis-desktop:~$ 


I don't think that's what your looking for

---

### Post by xeth_delta on 2008-02-28
> **linuxjerk said:**
> dennis@dennis-desktop:~$ dmesg | grep -i hda
[17179572.160000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.900000] hda: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[17179573.772000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
dennis@dennis-desktop:~$ 


I don't think that's what your looking for

Indeed it is not. Let's try restarting the alsa sub-system:
```
sudo /etc/init.d/alsa-utils restart
```
Try dmesg again and see if any relevant lines are present.

By the way. Are all the sound modules loaded?
```
lsmod | grep snd
```

---

### Post by linuxjerk on 2008-02-28
dennis@dennis-desktop:~$ dmesg | grep -i codec
dennis@dennis-desktop:~$ sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                                            [ ok ] 
 * Setting up ALSA...                                                                               [ ok ] 
dennis@dennis-desktop:~$ dmesg | grep -i hda
[17179572.160000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.900000] hda: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[17179573.772000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
dennis@dennis-desktop:~$ lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
dennis@dennis-desktop:~$

---

### Post by xeth_delta on 2008-02-28
Still not what I was looking for. I will need to go sleep, but I will post again after I wake up.
The fastest solution would probably be to get the latest drivers source and compile it. Download the version 1.0.16 from: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Follow the instructions posted in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), section "ALSA driver Compilation", subsection "Using alsa-source".

I will be online later to assist you. Meanwhile, good luck, write for any question you may have.
By the way, I am curious, why have sticked to 6.10 Edgy Eft?

---

### Post by linuxjerk on 2008-02-28
Actually I do have Gutsy on order. Should be here in a couple days.
Should I not worry about this and wait for gutsy?

Do you think things will work any better with that? From what I've read there are
problems with intel there also.

---

### Post by linuxjerk on 2008-02-29
Well go ahead and sleep. I'm about ready for that myself.

I really appreciate your help and I'll check the forum in the morning.

---

### Post by northern lights on 2008-02-29
> **linuxjerk said:**
> Actually I do have Gutsy on order. Should be here in a couple days.
Should I not worry about this and wait for gutsy?

Do you think things will work any better with that? From what I've read there are
problems with intel there also.

As mentioned earlier the alsa drivers shipped with Gutsy support all ICH families up to 7.

The problems you're referring to occur with HighDefAudio / ICH8 sound devices (on a buddy's laptop ICH8 runs stable in Hardy alpha5, but that just as a side note).

Since you're saying you have ordered it, are you planning a clean install off the CD anyway? If so, indeed don't worry about it and wait a few days. You are aware though, that you could update your system to Gutsy anytime you want?!

---

### Post by marine63 on 2008-02-29
:l

---

### Post by linuxjerk on 2008-02-29
Yes I plan to do a clean install with gutsy. When I noticed the sound problem with edgy I did not do anything further with this install.

But like you say there will probably be problems with sound with gutsy.

---

### Post by northern lights on 2008-02-29
> **linuxjerk said:**
> But like you say there will probably be problems with sound with gutsy.

Not with you're soundcard, though. And man, you gotta give credit to people that code a driver, less than two month after hardware release without thorough knowledge of the hardware itsself...

---

### Post by linuxjerk on 2008-02-29
Yes I do.

Seems like somewhat of a liability coding for something you don't fully understand.

I thought my board was last years model. I didn't realize it was that up to date.

So gutsy should work out of the box?

---

### Post by xeth_delta on 2008-02-29
> **linuxjerk said:**
> Yes I do.

Seems like somewhat of a liability coding for something you don't fully understand.

I thought my board was last years model. I didn't realize it was that up to date.

So gutsy should work out of the box?

Hi again. I just noticed you were mentioning your laptop has an ICH7 chipset. I looked with "lshw -C sound" on mine, and what do you know? It does have an ICH7 chipset. It works out of the box. I preferred to install the latest drivers on top as I wanted some extra features that became available for my MacBook on the latest alsa release.

In any case, I think it will work directly. Let us know how it goes when you do the clean installation. :)

---

### Post by xeth_delta on 2008-02-29
Just more on how the information for the sound card would look like:
```
lshw -C sound
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

---

### Post by linuxjerk on 2008-02-29
Ok thanks for the info.

This isn't a laptop though. It's a desktop. I guess intel chipsets are popular.

It's kind of strange that edgy didn't give me any error messages. No "sound card not found" or anything.

The 82801G (ICH7 Family) chipset is listed in the device manager like everything is working properly.

The only clue is no sound.

---

### Post by northern lights on 2008-03-01
You can check yourself under
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

---

### Post by xeth_delta on 2008-03-01
> **linuxjerk said:**
> Ok thanks for the info.

This isn't a laptop though. It's a desktop. I guess intel chipsets are popular.

It's kind of strange that edgy didn't give me any error messages. No "sound card not found" or anything.

The 82801G (ICH7 Family) chipset is listed in the device manager like everything is working properly.

The only clue is no sound.

I would say give Gutsy a try and let us know if there are any problems.

---

### Post by linuxjerk on 2008-03-01
ok, hopefully it will come in the next few days.

---

### Post by xeth_delta on 2008-03-01
> **linuxjerk said:**
> ok, hopefully it will come in the next few days.

Of course, until the CD arrives, if you have time to spare and want to try compiling the drivers yourself, you can try that, even if it is merely to learn how to. :)

---

### Post by Riffer on 2008-03-01
others said it better then me

---

### Post by xeth_delta on 2008-03-01
> **Riffer said:**
> others said it better then me

Sorry, I don't understand what you mean. Can you please be more explicit?

---

### Post by linuxjerk on 2008-03-01
Hello xeth_delta

No I think I'll pass on the compiling for now. Probably should learn more though.

Gutsy has arrived today. Success, the sound cometh :guitar:

But...  more questions !!!

I am trying to share folders so I can do network transfers.

I get the error that I need to install (NFS) and (SMB) when I press the button that says install it does nothing. Pops back up again with the same error and repeats.
I'm on the internet when this happens and that doesn't help.
I think Samba is already installed???

Also how do you find out the network name of this computer? Like in windows for network transfers.
I know I had this working in edgy but I have forgotten it now.

---

### Post by xeth_delta on 2008-03-02
> **linuxjerk said:**
> Hello xeth_delta

No I think I'll pass on the compiling for now. Probably should learn more though.

Gutsy has arrived today. Success, the sound cometh :guitar:

But...  more questions !!!

I am trying to share folders so I can do network transfers.

I get the error that I need to install (NFS) and (SMB) when I press the button that says install it does nothing. Pops back up again with the same error and repeats.
I'm on the internet when this happens and that doesn't help.
I think Samba is already installed???

Also how do you find out the network name of this computer? Like in windows for network transfers.
I know I had this working in edgy but I have forgotten it now.

Great to read you have sound! :D
I am sorry, but I do not have much experience with SMB and would be unable to offer any useful information.
I suggest that you perform a search or start a new thread on the issue. Don't forget to mark this thread solved if the sound issues are gone.
Good luck!

---

### Post by northern lights on 2008-03-02
> **linuxjerk said:**
> I get the error that I need to install (NFS) and (SMB)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server")

---

