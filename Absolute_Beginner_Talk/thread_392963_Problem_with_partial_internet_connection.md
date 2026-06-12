---
title: "Problem with partial internet connection"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by bobhawkes on 2007-03-25
Hi,

Apologies if this topic is covered elsewhere - I've serached but can't find the answer.  I've just installed Ubuntu and I am having trouble with connection to the internet.

Having disabled IPv6 in Firefox this is now working OK (I'm using it right now). However, email will not upload and I cannot access the repositories (Refresh in synaptic). I have set alias net-pf-10 to off and rebooted but still have the problem.

Any suggestions welcome. I'm determined not to be driven back to Windows!

I believe this info will help...

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:30:1B:AF:6A:72  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2789202 (2.6 MiB)  TX bytes:600143 (586.0 KiB)
          Interrupt:185 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

lspci:

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:06.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

Thanks,

Bob

---

### Post by bobhawkes on 2007-03-25
OK. Fixed it myself after search on Google. This seems to be a problem with DNS and D-Link routers. The solution is:

Go to System -> Admininstration -> Networking
Select the DNS tab
Delete the router IP address from the DNS table
Add your ISP DNS IP to the table.

All works fine now.

---

