---
title: "Complete N00b"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Cheat King on 2007-05-31
Hello, I am a complete n00b to Ubuntu and Linux. I am looking at KisMet, all that is the problem is that in the kismet.conf file, I do not know what the chipset is. My wireless card is an Intel WM3945ABG (I *think*) So... the problem is at this part of the conf file:

```
source=[chipset],eth1,Kismet
``` 

So, do you know what my chipset is, or how to find it out?

Don't hurt me! I'm a n00b XD

:KS

---

### Post by Sparkster185 on 2007-05-31
```

lspci -v | less

```

you can scroll through this to find what make/model you have.

---

### Post by lyceum on 2007-05-31
Welcome! :D

You can also open the box.

:popcorn:

---

### Post by Cheat King on 2007-05-31
Thanks Sparkster, I'll give it a go! And lyceum, I do not want to open it up...

Oh, and thanks lyceum!

And, erm, Sparkster... I can't find mine...

---

### Post by Cheat King on 2007-05-31
OK, sorry for the double post, but I have found my one:

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

But, which is the chipset that I need? XD

---

### Post by Cheat King on 2007-05-31
Seeing as it is nearly on the second page... BUMP!

---

### Post by Cheat King on 2007-05-31
*Bangs head*

:KS:popcorn::p;):D:o:):guitar:

---

### Post by lyceum on 2007-05-31
Well to bump you again, It looks like an Intell. Can you put the whole list up? I really do not know enough about this, but if I can see the whole picture I may be able to wrape by head around it. But, I thought Intel would work with Ubutnu so I am not sure... (I know you don't want to, but my solution is always to look inside for myself)

---

### Post by Cheat King on 2007-05-31
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
(prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, fast devsel, latency 0
        Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d4000000-d5ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: d8000000-d80fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02) (prog-if 01
 [AHCI 1.0])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d8006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at d8005000 (32-bit, non-prefetchable) [size=2K]
        Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Gateway 2000 Unknown device 0366
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d8004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

---

### Post by Cheat King on 2007-05-31
Please! I really need to know this :cry:

---

### Post by reckless2k2 on 2007-05-31
The kismet site tells you what to type for every card chipset. View their site real quick in the FAQ.

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

I believe you'll be using one in the "ipw" line.

ipw3945

---

### Post by Cheat King on 2007-05-31
Thank you man, you rule! But I get this:
```
cheatking@cheatking-laptop:~/Desktop$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to cheatking (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipw3945' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...
cheatking@cheatking-laptop:~/Desktop$ 

```

---

### Post by reckless2k2 on 2007-05-31
I'd check out a few posts other places about that driver or try the older ipw codes like 2200 or 2100.

---

### Post by Cheat King on 2007-05-31
Well, I've tried all of the Intel ones and it doesn't look like it is supported...

Well, after looking around the forum, I have got to recompile Kismet, can someone PM me on how to do this please? I am a complete n00b...

Anyways... now is time for sleepy-boos... XD

---

### Post by lyceum on 2007-06-01
[http://www.intel.com/support/wireless/wlan/pro3945abg/index.htm](http://www.intel.com/support/wireless/wlan/pro3945abg/index.htm)

This IS your card, but how to set it up? I could not find anything here in the forums or google as to how to set up/ Sorry. You might be able to do it with NDISWrapper, but I could not tell you how. Sorry. :(

-edit

 found this:

[http://ubuntuforums.org/showthread.php?t=457956&highlight=ntel+PRO%2FWireless+3945ABG](http://ubuntuforums.org/showthread.php?t=457956&highlight=ntel+PRO%2FWireless+3945ABG)

and 

[http://ubuntuforums.org/showthread.php?t=438166&highlight=ntel+PRO%2FWireless+3945ABG](http://ubuntuforums.org/showthread.php?t=438166&highlight=ntel+PRO%2FWireless+3945ABG)

Hope they help.

---

### Post by reckless2k2 on 2007-06-01
OK....I wouldn't normally recommend this but if you are looking to use penetration testing programs such as kismet, you should probably lean to a penetration testing distro like backtrack or nubuntu. I'm not sure if nubuntu is still around but i know backtrack is and they patch the kernel with all necessary drivers for most if not all wifi cards with the ability to inject and sniff. Doing something like that in Ubuntu will require some kernel work.  The good thing is that penetration distros run on USB keys or CDs.

---

