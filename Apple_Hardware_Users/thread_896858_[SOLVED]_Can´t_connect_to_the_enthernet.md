---
title: "[SOLVED] Can´t connect to the enthernet"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by alexandro121 on 2008-08-21
well theres is a big story to tell about me my macbook pro and linux but i´ll ask my most important questions.

here they are:
i have fully erease the osx( ´cos i had some problems) but know mi wired and wireless connection doesn´t seem to be working, i have read some threads but cant find the answer because they dont explain how to configure the wired connection, can someone help me?

the problem is that i can´t start to configurate the other hardwares because the wired connection doesn´t work( well i think) 

anybody?

---

### Post by Stemp on 2008-08-21
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
or 
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
or even
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)
?

---

### Post by alexandro121 on 2008-08-21
hey thanks for the tips, but thats really not my problem , i had foud does pages that you have link me but the real question is that i can connect via wired, that my problem ´cos as you may notice, most of the comands require to download something, but i cant do it, thats why i can configure the wirelees, touchpad firnger tips and lot more.

my prblem is that i don´t know why the wired connection does seems to be working,,,


data: mac book pro intel core 2 duo...120 gb.... 2.2 ghz ram and im using ubuntu 8.04

---

### Post by Stemp on 2008-08-22
Sorry I thought it was a wire**less** problem, my bad.

Check your ethernet with :

```
lspci -v
dmesg | grep eth0
ifconfig
```

---

### Post by alexandro121 on 2008-08-22
THIS IS WHAT IT APPEARS whem i type in the terminal, still can´t connect

```

alexandro@alexandro-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 90000000-930fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 60c0 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 60a0 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 9b504c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: 9b400000-9b4fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 97400000-9b3fffff
	Prefetchable memory behind bridge: 0000000093100000-00000000970fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: 97300000-973fffff
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 97200000-972fffff
	Prefetchable memory behind bridge: 000000009b600000-000000009b6fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 6080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 6060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6040 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 9b504800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Memory behind bridge: 97100000-971fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 60e0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 60f8 [size=8]
	I/O ports at 6114 [size=4]
	I/O ports at 60f0 [size=8]
	I/O ports at 6110 [size=4]
	I/O ports at 6020 [size=16]
	I/O ports at 1000 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: medium devsel, IRQ 10
	Memory at 9b505000 (32-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Apple Computer Inc. Unknown device 00a0
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 5000 [size=128]
	Expansion ROM at 93000000 [disabled] [size=128K]
	Capabilities: <access denied>

0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
	Subsystem: Apple Computer Inc. Unknown device 0087
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at 97300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Marvell Technology Group Ltd. Unknown device 00ba
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at 97200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 3000 [size=256]
	Expansion ROM at 9b600000 [disabled] [size=128K]
	Capabilities: <access denied>

0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02) (prog-if 10 [OHCI])
	Flags: bus master, medium devsel, latency 248, IRQ 21
	Memory at 97104000 (32-bit, non-prefetchable) [size=2K]
	Memory at 97100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

alexandro@alexandro-laptop:~$ dmesg | grep eth0
[   74.470156] sky2 eth0: addr 00:1b:63:a5:83:5a
[   79.113334] sky2 eth0: enabling interface
[   79.965963] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   93.665985] eth0: no IPv6 routers present
alexandro@alexandro-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:a5:83:5a  
          inet6 addr: fe80::21b:63ff:fea5:835a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213485 (208.4 KB)  TX bytes:6147 (6.0 KB)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:63:a5:83:5a  
          inet addr:169.254.6.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111208 (108.6 KB)  TX bytes:111208 (108.6 KB)
```

---

### Post by Stemp on 2008-08-22
From ifconfig :
> inet addr:169.254.6.159 Bcast:169.254.255.255 Mask:255.255.0.0

You are connected and you have an IP adress !

Try to ping something :

```
ping google.com -c5
ping 72.14.207.99 -c5
```

---

### Post by alexandro121 on 2008-08-22
NOP nothing, i had found out that yes i have connection but can´t download the actulization and can´t browser the web,

my results from the ping
```

alexandro@alexandro-laptop:~$ ping google.com -c5
ping: unknown host google.com
alexandro@alexandro-laptop:~$ ping 72.14.207.99 -c5
connect: Network is unreachable
alexandro@alexandro-laptop:~$
```

---

### Post by cyberdork33 on 2008-08-22
> **Stemp said:**
> From ifconfig :


You are connected and you have an IP adress !
That is a self-assigned IP address. (starts with 169). This occurs when the DHCP server does not give you an IP. From the output it looks as though your hardware works fine it is just the Server giving you problems.

Try running ```
sudo dhclient
``` in a terminal and see what messages you get. And PLEASE, post your output in [noparse]```
codetags
```[/noparse]

---

### Post by alexandro121 on 2008-08-22
well yes, im connected but why i can´t use firefox, synaptic, the chat program, evolution, etc... what is it then?

---

### Post by cyberdork33 on 2008-08-22
> **alexandro121 said:**
> well yes, im connected but why i can´t use firefox, synaptic, the chat program, evolution, etc... what is it then?
Because you do not have a valid IP, as stated. Please give requested output.

---

### Post by vikas1234 on 2008-08-23
You are not connected to the server. For DHCP you need to have any IP from the server. Do one thing try to ping the ISP Provider IP

---

### Post by Adoring on 2008-08-23
Thank you

[COLOR="White"]http://www.al-mohd.com/[/COLOR]
[COLOR="White"]http://www.al-mohd.com/forum/[/COLOR]

---

### Post by alexandro121 on 2008-08-25
hey sorry for not repling but im out on a business trip sorry...  ill inform you in these days whats my progress cos i haven´t try the tips both gave me... thanks  and sorry

---

### Post by alexandro121 on 2008-08-25
here is my result

```
alexandro@alexandro-laptop:~$ sudo dhclient
[sudo] password for alexandro: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:63:a5:83:5a
Sending on   LPF/eth0/00:1b:63:a5:83:5a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
alexandro@alexandro-laptop:~$ 

```

---

### Post by cyberdork33 on 2008-08-25
whatever device that acts as your dhcp server (router?) is not giving your machine an IP for some reason. I do not believe this is the fault of your installed system. This could be due to some sort of MAC address filtering on the router.

---

### Post by alexandro121 on 2008-08-26
hey thanks for everything i had fix it, with your help, i change the router conf i delet a mac address in the bypass zone and now it works as hell yeah hahah thanks for all your hard work, and .... ok thats all ahah im really happy know thath i can use ubuntu in a 100%

---

### Post by cyberdork33 on 2008-08-26
Please mark this thread as solved (Thread Tools Menu)

---

