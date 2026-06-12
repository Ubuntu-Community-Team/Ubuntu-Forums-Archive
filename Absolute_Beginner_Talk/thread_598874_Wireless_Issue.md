---
title: "Wireless Issue"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by kboss715 on 2007-10-31
I am using Linux for the first time, my third day or so. My Belkin wireless card works, but unlike on Windows XP I get kicked off at random. Sometimes I have to remove the card and replace it and it works. Other times I have to restart the computer. Also, when I put in the card it fails to connect under network manager, but when I click the logo and select my network the second time it works about half the time. What should I do to remedy this? Thanks in advance.

---

### Post by arkara on 2007-10-31
without having any special knowledge on the matter it seems that the drivers have a bug.
so you might w8 for the next release or for some kind of a bugfix.
i think you can settle down with a wired network for the moment. sorry for the experience of yours.

---

### Post by kboss715 on 2007-10-31
I would love to use a wired network instead, but in my apartment we have solely wireless. Thanks for the reply anyways.

---

### Post by RomeReactor on 2007-10-31
Hi. What chipset does your Belkin card use? does it work with a native driver or are you using ndiswrapper? please enter the following commands in the terminal (Applications->Accessories->Terminal) and post the output:
```
sudo lshw -C network
```
and
```
lspci -v
```

And welcome to the forums!

---

### Post by jppaynesr on 2007-10-31
I suggest that you replace network manager with WICD. I could not get reliable wireless until I installd wicd. 
See this thread
[http://ubuntuforums.org/showthread.php?p=3656835](http://ubuntuforums.org/showthread.php?p=3656835)

---

### Post by kboss715 on 2007-10-31
Hey, the Belkin is a Wireless G USB Network Adapter. I think I am using the drivers that came right with Ubuntu, I didn't install anything called ndiswrapper. From the codes I got:

kev@ubuntu:~$ sudo lshw -C network
[sudo] password for kev:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:dd:af:18
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:c2:18:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 802.11g

kev@ubuntu:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at b0000000 (32-bit, prefetchable) [size=64M]
        Memory at b4000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: e0000000-efffffff
        Prefetchable memory behind bridge: a0000000-afffffff

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f0001000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f0002000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at e000 [size=16]
        Memory at f0000000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8070 [size=16]

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: d0000000-dfffffff
        Prefetchable memory behind bridge: 90000000-9fffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at f0000400 (32-bit, non-prefetchable) [size=256]

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at f0000500 (32-bit, non-prefetchable) [size=256]

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at a0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at e0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at a8000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 90000000-93fff000 (prefetchable)
        Memory window 1: d4000000-d7fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


Thanks for the response.

---

### Post by RomeReactor on 2007-10-31
Please post the output of:
```
lsusb
```
Are you running Ubuntu 7.10 (Gutsy)?

---

### Post by kboss715 on 2007-11-01
Yes I use Gutsy.

kev@ubuntu:~$ lsusb
Bus 003 Device 002: ID 050d:705a Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I tried installing WICD. It could show me the two networks that are normally available to me. The problem was that it showed each connection at -1% signal strength. I have re-installed network manager for now though.

---

### Post by RomeReactor on 2007-11-02
You could try using the [RT73 drivers from RaLink]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29"); or [this tutorial]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux"), which relies on installing NdisWrapper to use your windows XP drivers in Ubuntu. I don't have a Belkin (or a usb wi-fi device for that matter), so those links are probably the best I can do in that regard. You should wait for someone who's managed to get it working properly to provide more assistance.

If you *do* decide to go ahead with either tutorial and need help, please post back and we'll see what we can do.

---

