---
title: "Backtrack 5 r3"
date: 2013-12-31
forum: Any Other OS
---

### Post by far-slayer on 2013-12-31
I used to be big into Linux a few years ago, Thought about picking it up again. Installed BT5r3 but I forgot how to install my wireless drivers -_- I'm running on Ethernet, But iwconfig says I have nothing


# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


lspci  says 
```
lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)

I see my Ethernet driver there, But for my Wireless, The network controller, It doesn't say what driver it is? Am I missing something here? The laptop is a Dell Inspiron 15 3521 model.  Any help would be appreicated, I have a horrible kink in my back and it kills me to set straight up in the computer chair.


Here is also the lspci -v If it helps at all.


root@bt:~# lspci -v
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
    Subsystem: Dell Device 0597
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
    Subsystem: Dell Device 0597
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCIe advanced features <?>

00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30)
    Subsystem: Dell Device 0597
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at c0600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: Dell Device 0597
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at c0614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20)
    Subsystem: Dell Device 0597
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c0619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: Dell Device 0597
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c0610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c04fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [90] Subsystem: Dell Device 0597
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: c0500000-c05fffff
    Prefetchable memory behind bridge: 00000000afb00000-00000000afbfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [90] Subsystem: Dell Device 0597
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20)
    Subsystem: Dell Device 0597
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c0618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: Dell Device 0597
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04) (prog-if 01)
    Subsystem: Dell Device 0597
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 3088 [size=8]
    I/O ports at 3094 [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3090 [size=4]
    I/O ports at 3060 [size=32]
    Memory at c0617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA <?>
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: Dell Device 0597
    Flags: medium devsel, IRQ 10
    Memory at c0615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 3040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Dell Device 0597
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Mask- TabSize=4
    Capabilities: [d0] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-36-00-00-00-b6
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)
    Subsystem: Dell Device 020c
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c0500000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at afb00000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/2 Enable-
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
```

---

### Post by QIII on 2013-12-31
[I]Moved to [B]Other OS/Distro Support

[/B][/I]The developers of Backtrack have forked it into Kali Linux.  You might be able to get better help on the [Kali forum]("http://forums.kali.org/forumdisplay.php?1-Kali-Linux-Forums").

---

