---
title: "Lubuntu Bad Graphics 1GHz E-Mac"
date: 2013-10-21
forum: Apple Hardware Users
---

### Post by Skyline_8650 on 2013-10-21
Greetings, I downloaded and a booted the live CD of Lubuntu 13.10, and it booted fine and even posting this from the live CD. Seems to work pretty well, however the graphics are what looks like 800X600 in 1 bit color, menus and text look fine photos are a pixled mess icons are a few colors. 

Comptuer is a stock 1ghz E-mac wtih 512MB RAM and 80GB and Superdrive. Out put of lspci -v is

lubuntu@lubuntu:~$ lspci -v
0000:00:0b.0 Host bridge: Apple Inc. UniNorth 1.5 AGP
    Flags: bus master, 66MHz, medium devsel, latency 16
    Capabilities: <access denied>
    Kernel driver in use: agpgart-uninorth

0000:00:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV200 [Radeon 7500/7500 LE] (prog-if 00 [VGA controller])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RV200 [Radeon 7500/7500 LE]
    Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 48
    Memory at 98000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 0400 [size=256]
    Memory at 90000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 90020000 [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeonfb

0001:10:0b.0 Host bridge: Apple Inc. UniNorth 1.5 PCI
    Flags: bus master, 66MHz, medium devsel, latency 16

0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo Mac I/O (rev 03)
    Flags: bus master, medium devsel, latency 16
    Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

0001:10:18.0 USB controller: Apple Inc. KeyLargo USB (prog-if 10 [OHCI])
    Flags: bus master, medium devsel, latency 16, IRQ 27
    Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

0001:10:19.0 USB controller: Apple Inc. KeyLargo USB (prog-if 10 [OHCI])
    Flags: bus master, medium devsel, latency 16, IRQ 28
    Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

0002:20:0b.0 Host bridge: Apple Inc. UniNorth 1.5 Internal PCI
    Flags: bus master, 66MHz, medium devsel, latency 16

0002:20:0e.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller
    Flags: bus master, medium devsel, latency 16, IRQ 40
    Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci

0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth GMAC (Sun GEM) (rev 01)
    Flags: bus master, 66MHz, slow devsel, latency 16, IRQ 41
    Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
    Expansion ROM at f5100000 [disabled] [size=1M]
    Kernel driver in use: gem

lubuntu@lubuntu:~$

---

