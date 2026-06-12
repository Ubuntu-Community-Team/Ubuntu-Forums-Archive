---
title: "can't use USB with Gutsy"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2008-01-27
hey i just noticed something tonight.  With my computer (toshiba satellite a135 s4527) (kernel 2.6.22-14-generic)   I can't use any of the USB or the sans disk port.  I know that they aren't broken because what i ended up doing was rebooting and going to my windows partition and transferring the pictures onto my pc into windows and then rebooting again and using the "fuse" program that i have to transfer the pictures from windows to ubuntu.  Is there anyone else having this problem?  Is there a workaround?  Can somone tell me how to mount whatver i may be trying to connect to the USB through the command line? This time I was trying to connect my digital camera.  I didn't have any problems w/ feisty fawn.  So, please get back to me ladies and gentlemen!!!!

---

### Post by taurus on 2008-01-27
See if your external device appears on the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by emarkd on 2008-01-27
You can also see if your USB controller hardware is recognized using the lshw command.  If it's not there, though, someone smarter than me will have to help you ;)

---

### Post by bradmayne on 2008-01-27
here is the output from that command:  Thanks for taking an interest!  Didn't you mean the command lspci -v?  That would give us a better idea.  Fdiak is more for the partition not extra evices like a usb 
Output from sudo fdisk -l
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        8237    64621094    7  HPFS/NTFS
/dev/sda3            8238       11429    25639740   83  Linux
/dev/sda4           14328       14593     2136645    5  Extended
/dev/sda5           14328       14593     2136613+  82  Linux swap / Solaris
Ouitput from lspci -v

brad@brad-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16

---

### Post by taurus on 2008-01-27
Also

```
dmesg | tail
```

p.s.  I assume you did plug something into a USB port?

---

### Post by bradmayne on 2008-01-27
yes, i tried plugging in something!  That's how I found out that for some dumb reason gutsy won't recognize what is being plugged in!!  Here is the output of the dmesg | tail

 dmesg | tail
[   34.032000] Bluetooth: Core ver 2.11
[   34.032000] NET: Registered protocol family 31
[   34.032000] Bluetooth: HCI device and connection manager initialized
[   34.032000] Bluetooth: HCI socket layer initialized
[   34.056000] Bluetooth: L2CAP ver 2.8
[   34.056000] Bluetooth: L2CAP socket layer initialized
[   34.112000] Bluetooth: RFCOMM socket layer initialized
[   34.112000] Bluetooth: RFCOMM TTY layer initialized
[   34.112000] Bluetooth: RFCOMM ver 1.8
[   38.136000] ath0: no IPv6 routers present

---

