---
title: "No Ethernet No Wireless No Internet, No Clue Why?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by ashish122185 on 2007-11-09
Hi! I am a beginner with Ubuntu. This is my first hand experience with Ubuntu. After installing Ubuntu, I cannot connect to internet at all. I installed my ubuntu using wubi (shows that I really am a beginner). I have been searching about how to configure my wireless and ethernet from past 3 days without any success.

I have Broadcom Netlink Fast Ethernet card and,
Dell WLAN Wireless 1490 card.
I have a Dell Vostro 1400.
I think my NVidia Graphics card is also not picked up by Ubuntu (but thats not so important right now. Also, I have not searched about it yet).

Right now, I am concerned about getting internet.

Also, I would like to add that my ubuntu and windows vista are running on the same partition since I used wubi. I don't know if that creates any problem.

I have added the output of the three commands: ifconfig, lspci -v, lspci -n

---------------------------------------------------------------------------
Output after running command "ifconfig"

eth0      Link encap:Ethernet  HWaddr 00:1C:23:F7:56:5A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:792 (792.0 b)  TX bytes:792 (792.0 b)
----------------------------------------------------------------------------

Output after running command "lspci -v"

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f9c00000-f9efffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        Memory behind bridge: f9b00000-f9bfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f9a00000-f9afffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=32]
        Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 0227
        Flags: medium devsel, IRQ 10
        Memory at febfb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9aff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9aff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9aff500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9aff600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9aff700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

09:00.0 Ethernet controller: Broadcom Corporation Unknown device 1713 (rev 02)
        Subsystem: Dell Unknown device 0227
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

----------------------------------------------------------------------------------

Output after running command "lspci -n"

00:00.0 0600: 8086:2a00 (rev 0c)
00:01.0 0604: 8086:2a01 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 02)
00:1a.1 0c03: 8086:2835 (rev 02)
00:1a.7 0c03: 8086:283a (rev 02)
00:1b.0 0403: 8086:284b (rev 02)
00:1c.0 0604: 8086:283f (rev 02)
00:1c.1 0604: 8086:2841 (rev 02)
00:1c.3 0604: 8086:2845 (rev 02)
00:1c.5 0604: 8086:2849 (rev 02)
00:1d.0 0c03: 8086:2830 (rev 02)
00:1d.1 0c03: 8086:2831 (rev 02)
00:1d.2 0c03: 8086:2832 (rev 02)
00:1d.7 0c03: 8086:2836 (rev 02)
00:1e.0 0604: 8086:2448 (rev f2)
00:1f.0 0601: 8086:2815 (rev 02)
00:1f.1 0101: 8086:2850 (rev 02)
00:1f.2 0106: 8086:2829 (rev 02)
00:1f.3 0c05: 8086:283e (rev 02)
01:00.0 0300: 10de:0427 (rev a1)
03:01.0 0c00: 1180:0832 (rev 05)
03:01.1 0805: 1180:0822 (rev 22)
03:01.2 0880: 1180:0843 (rev 12)
03:01.3 0880: 1180:0592 (rev 12)
03:01.4 0880: 1180:0852 (rev 12)
09:00.0 0200: 14e4:1713 (rev 02)
0c:00.0 0280: 14e4:4312 (rev 01)

Any help is greatly appreciated. Whenever I start searching about my internet problem, after a while, I come back to the same point and with no solution.

Thanks,
Ashish

---

### Post by luisromangz on 2007-11-09
Your wired card seems to be recognized since there is an eth0 interface in the ifconfig listing, what is your router's config?

---

### Post by ashish122185 on 2007-11-12
Thank you replying. I was away for a while. Rather I almost gave up on Ubuntu. But today I reinstalled ubuntu. Also, I have installed Wicd and disabled Network Manager, thinking that Wicd would be better.

I am not sure if I understand what router configuration are you asking for.

I do have output of ipconfig command, if thats what it is:

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Ashish-Vostro

   Primary Dns Suffix  . . . . . . . :

   Node Type . . . . . . . . . . . . : Hybrid

   IP Routing Enabled. . . . . . . . : No

   WINS Proxy Enabled. . . . . . . . : No

   DNS Suffix Search List. . . . . . : hsd1.nj.comcast.net.



Wireless LAN adapter Wireless Network Connection:



   Connection-specific DNS Suffix  . : hsd1.nj.comcast.net.

   Description . . . . . . . . . . . : Dell Wireless 1490 Dual Band WLAN Mini-Ca

rd

   Physical Address. . . . . . . . . : 00-1C-26-89-6E-91

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::11a7:e838:3672:2f62%10(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.1.102(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Lease Obtained. . . . . . . . . . : Monday, November 12, 2007 7:55:42 PM

   Lease Expires . . . . . . . . . . : Tuesday, November 13, 2007 7:55:41 PM

   Default Gateway . . . . . . . . . : 192.168.1.1

   DHCP Server . . . . . . . . . . . : 192.168.1.1

   DHCPv6 IAID . . . . . . . . . . . : 167779366

   DNS Servers . . . . . . . . . . . : 68.87.64.146

                                       68.87.75.194

   NetBIOS over Tcpip. . . . . . . . : Enabled



Ethernet adapter Local Area Connection:



   Connection-specific DNS Suffix  . : hsd1.nj.comcast.net.

   Description . . . . . . . . . . . : Broadcom NetLink (TM) Fast Ethernet

   Physical Address. . . . . . . . . : 00-1C-23-F7-56-5A

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::215e:40b1:3379:7744%9(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.1.100(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Lease Obtained. . . . . . . . . . : Monday, November 12, 2007 7:55:36 PM

   Lease Expires . . . . . . . . . . : Tuesday, November 13, 2007 7:55:36 PM

   Default Gateway . . . . . . . . . : 192.168.1.1

   DHCP Server . . . . . . . . . . . : 192.168.1.1

   DHCPv6 IAID . . . . . . . . . . . : 201333795

   DNS Servers . . . . . . . . . . . : 68.87.64.146

                                       68.87.75.194

   NetBIOS over Tcpip. . . . . . . . : Enabled



Tunnel adapter Local Area Connection* 6:



   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface

   Physical Address. . . . . . . . . : 02-00-54-55-4E-01

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes



Tunnel adapter Local Area Connection* 9:



   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : isatap.{E0639DE9-69C4-48EA-BE9F-12DA4EB6F

06B}

   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes



Tunnel adapter Local Area Connection* 11:



   Connection-specific DNS Suffix  . : hsd1.nj.comcast.net.

   Description . . . . . . . . . . . : isatap.hsd1.nj.comcast.net.

   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.1.100%12(Preferred)

   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.1.102%12(Preferred)

   Default Gateway . . . . . . . . . :

   DNS Servers . . . . . . . . . . . : 68.87.64.146

                                       68.87.75.194

   NetBIOS over Tcpip. . . . . . . . : Disabled


Please let me know if I need to give output of any other command. I'll be more than happy to do so.

Thanks!! Cheers!

---

### Post by ashish122185 on 2007-11-14
I need little help here. :(

Thanks!:)

---

### Post by m@@dL3s on 2007-11-15
> **ashish122185 said:**
> I need little help here. :(

Thanks!:)

Hi, I didin't get much help with my question on the same subject either! There are a lot of posts in this forum and I think we just get buried!

I did get mine working after a lot of frustrating hours of work. What finally did it was the doc for my brand and version of wireless card on the [ubuntu wireless docs]("https://help.ubuntu.com/community/WifiDocs?highlight=%28%28WifiDocs%7CDriver%7Cbcm43xx%7CFeisty%29%29"). 

have you seen the above page?  Try looking around in there.

for me it was this one "WifiDocs/Device/Broadcom BCM4311 rev 01 (ndiswrapper)"

Not every step matched my computer and its results when I worked thru it but by a little trial and error at the end I got connected.

Good luck! I wish you well!!!

---

### Post by ashish122185 on 2007-11-15
@ m@@dL3s
Thanks a lot for posting.

I haven't gone through the link before. So I am going to do that now.

Thanks!:) Hope it will work.

---

