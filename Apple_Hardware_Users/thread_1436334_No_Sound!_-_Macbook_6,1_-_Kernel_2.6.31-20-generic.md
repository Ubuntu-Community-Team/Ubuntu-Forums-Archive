---
title: "No Sound! - Macbook 6,1 - Kernel 2.6.31-20-generic"
date: 2010-03-22
forum: Apple Hardware Users
---

### Post by benoitcsirois on 2010-03-22
Hi!

My sound was working in the past, but since I upgraded to kernel 2.6.31-20, it's no longer working. I am using Ubuntu on a Macbook and followed instructions from the Macbook 6,1 wiki on Ubuntu.com.

I just installed the lastest alsa-driver using the following commands:
```
./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
make
sudo make install
```

I changed /etc/modprobe.d/alsa-base.conf so that the last line is:
```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp5
```

I rebooted

alsamixer:
```
No mixer elems found
```

lspci -v:
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2000 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel, IRQ 15
	I/O ports at 2180 [size=64]
	I/O ports at 2140 [size=64]
	I/O ports at 2100 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 14
	Memory at 93300000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at 93388000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at 93389200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at 93387000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at 93389100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at 93380000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 93200000-932fffff
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
	Memory at 93386000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 21e0 [size=8]
	Memory at 93389000 (32-bit, non-prefetchable) [size=256]
	Memory at 93389300 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 25
	I/O ports at 21d8 [size=8]
	I/O ports at 21ec [size=4]
	I/O ports at 21d0 [size=8]
	I/O ports at 21e8 [size=4]
	I/O ports at 21c0 [size=16]
	Memory at 93384000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 92000000-930fffff
	Prefetchable memory behind bridge: 0000000080000000-0000000091ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 93100000-931fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M] (rev b1)
	Subsystem: Apple Computer Inc. Device 00bd
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 1000 [size=128]
	[virtual] Expansion ROM at 93000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
	Subsystem: Apple Computer Inc. Device 0093
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 93100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

```

Please halp!

---

### Post by linuxopjemac on 2010-03-22
I would not compile alsa yourself. Stick with the repository.  And then install the alsa-backports. Use the search button and you will find many posts about this.

---

### Post by benoitcsirois on 2010-03-22
The problem with installing the backport is that my Wifi stops working. They warn about this, and it actually happens.

---

### Post by linuxopjemac on 2010-03-23
Maybe you have to also compile (install from package manager ?)  the other alsa packages, like alsa-lib, alsa-utils alsa-oss and stuff like that, I don't know.

---

### Post by Jasev on 2010-03-23
This is a known issue on the MacBook Pro. Likely the same issue...

See [http://ubuntuforums.org/showthread.php?t=1423422&page=4](http://ubuntuforums.org/showthread.php?t=1423422&page=4)

As far as I'm aware the only solution at this stage is to use grub to boot into -19, until the next kernel upgrade which will hopefully fix the issue....

---

