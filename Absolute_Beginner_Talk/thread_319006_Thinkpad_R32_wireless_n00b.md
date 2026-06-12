---
title: "Thinkpad R32 wireless n00b"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by James_Nostack on 2006-12-14
Our company decided to get rid of an IBM Thinkpad R32 they were never using, and I took it home and put Dapper (6.06) on it.  Things are working great, but I don't know how to connect to wifi.  Right now I'm still using an ethernet cable.

WARNING: I am such a n00b that this is my very first on-my-own wifi experience, and I don't know what I'm doing.

1.  We have a router all set up.  With my GF's Windows box, it automatically scans for wifi signal, and you can connect to the appropriate WLAN.  

2.  In Network Monitor, all I can see is lo and eth0.

3.  When I go to System -> Administration -> Networking, eth0 is listed as an ethernet connection; there is also a wireless connection, eth1.  Until recently, it wasn't configured/activated.

4.  When I go to configure it, I enable the device, enter our network's name, and the password, and specify DHCP.  It takes a little while to activate the card.

5.  I still don't know how to switch to wireless operation.  That thing on Windows, where it hunts for local wireless networks, doesn't happen, or I'm too clueless to make it happen.

I'm assuming that the MiniPCI card that came with this thing is functional (the Thinkpad was never modified, and the prior user had no problems with wireless).  

What do I do next?  I apologize for asking such a lamebrained question.

---

### Post by James_Nostack on 2006-12-15
For additional reference: 

james@Marvin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:40:C2:10
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe40:c210/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:917633 (896.1 KiB)  TX bytes:175208 (171.1 KiB)

eth1      Link encap:Ethernet  HWaddr 00:20:E0:8F:C4:55
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:f8000000-f8000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by Bachstelze on 2006-12-15
You most likely need to install drivers for your wireless card. Please paste the output of *lspci*.

---

### Post by James_Nostack on 2006-12-15
Sure, thanks!

james@Marvin:~$ ifconfig
james@Marvin:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:07.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

---

