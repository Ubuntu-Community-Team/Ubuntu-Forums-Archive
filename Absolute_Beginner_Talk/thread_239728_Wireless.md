---
title: "Wireless"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-19
Hi, I have recently had a wireless router installed in my house and need to try and configure it with Ubuntu, I was wondering if anyone could tell me how to go about this:

The router is: Linksys wireless-G

I have an Acer Ferarri 4000 laptop and it has wireless built in to it. I don't know exactly what wireless card it is :(

Please help!

Calv

---

### Post by GeekSpeek'r on 2006-08-19
I sense two questions in this post:

Are you trying to configure your router?
-or-
Are you trying to configure your wireless NIC card

??

---

### Post by bensexson on 2006-08-19
Post the output from sudo ifconfig -a, sudo iwconfig, dmesg, and lspci.

---

### Post by calvinthomas on 2006-08-19
> **bensexson said:**
> Post the output from sudo ifconfig -a, sudo iwconfig, dmesg, and lspci.

**The first:**

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F4:69:1B  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef4:691b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1038646 (1014.3 KiB)  TX bytes:423814 (413.8 KiB)
          Interrupt:50 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:5D:3F:67  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**The second:**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**The third:**

d3000 for 393216 bytes
[17179726.412000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179726.412000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc3ecbcc0 for 393216 bytes
[17179747.652000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa915e000 for 245760 bytes
[17179747.656000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179747.656000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc75ec3c0 for 245760 bytes
[17179750.088000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa882b000 for 917504 bytes
[17179750.092000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179750.092000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc333c500 for 917504 bytes
[17179798.372000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa92de000 for 655360 bytes
[17179798.376000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179798.376000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3780 for 655360 bytes
[17179829.472000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa77ca000 for 2883584 bytes
[17179829.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179829.488000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc75ec180 for 2883584 bytes
[17179830.140000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08e8a000 for 49152 bytes
[17179830.144000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179830.144000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc75eccc0 for 49152 bytes
[17179993.308000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x090bf000 for 16384 bytes
[17179993.308000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179993.308000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3d40 for 16384 bytes
[17180049.848000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8cd1000 for 655360 bytes
[17180049.848000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180049.848000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd7f09580 for 655360 bytes
[17180061.124000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x091ac000 for 73728 bytes
[17180061.124000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180061.124000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc333c400 for 73728 bytes
[17180064.528000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x09159000 for 32768 bytes
[17180064.528000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180064.528000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2a00 for 32768 bytes
[17180080.064000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8ed1000 for 204800 bytes
[17180080.064000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180080.064000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3140 for 204800 bytes
[17180081.756000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7e28000 for 1064960 bytes
[17180081.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180081.760000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f24c0 for 1064960 bytes
[17180086.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x090b5000 for 16384 bytes
[17180086.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.924000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3b40 for 16384 bytes
[17180086.928000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa7c31000 for 4096000 bytes
[17180086.940000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3640 for 4096000 bytes
[17180086.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa9903000 for 131072 bytes
[17180086.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2a40 for 131072 bytes
[17180086.944000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x091a2000 for 32768 bytes
[17180086.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2900 for 32768 bytes
[17180086.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x091a2000 for 32768 bytes
[17180086.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.948000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2ac0 for 32768 bytes
[17180086.952000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8e70000 for 262144 bytes
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f29c0 for 262144 bytes
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x091a2000 for 98304 bytes
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2840 for 98304 bytes
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x091a2000 for 98304 bytes
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2740 for 98304 bytes
[17180086.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8db1000 for 360448 bytes
[17180086.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2600 for 360448 bytes
[17180086.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8de1000 for 163840 bytes
[17180086.968000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.968000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f25c0 for 163840 bytes
[17180086.968000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8de1000 for 163840 bytes
[17180086.968000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.968000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2580 for 163840 bytes
[17180086.976000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8d99000 for 458752 bytes
[17180086.980000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.980000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd31f2440 for 458752 bytes
[17180086.980000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8dd1000 for 229376 bytes
[17180086.980000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.984000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xccb7df00 for 229376 bytes
[17180086.984000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8dd1000 for 229376 bytes
[17180086.984000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180086.984000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xccb7dec0 for 229376 bytes
[17180087.000000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8d81000 for 557056 bytes
[17180087.000000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.004000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3b80 for 557056 bytes
[17180087.004000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8dc1000 for 294912 bytes
[17180087.004000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.004000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xccb7de80 for 294912 bytes
[17180087.004000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8dc1000 for 294912 bytes
[17180087.008000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.008000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xccb7dd80 for 294912 bytes
[17180087.024000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8d69000 for 655360 bytes
[17180087.028000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.028000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3cc0 for 655360 bytes
[17180087.028000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8db1000 for 360448 bytes
[17180087.032000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.032000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3c40 for 360448 bytes
[17180087.032000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8db1000 for 360448 bytes
[17180087.036000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180087.036000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3bc0 for 360448 bytes
[17180088.956000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8a1a000 for 1261568 bytes
[17180088.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180088.964000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3800 for 1261568 bytes
[17180091.712000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8b87000 for 196608 bytes
[17180091.716000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180091.716000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc3ecbf00 for 196608 bytes
[17180108.212000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8b87000 for 196608 bytes
[17180108.212000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180108.212000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3f00 for 196608 bytes
[17180112.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x0921d000 for 8192 bytes
[17180112.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180112.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e31c0 for 8192 bytes
[17180133.052000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8a0e000 for 163840 bytes
[17180133.052000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180133.052000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc57e3ac0 for 163840 bytes
[17180137.624000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8a06000 for 196608 bytes
[17180137.624000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180137.624000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc75ecac0 for 196608 bytes
[17180148.952000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8f0b000 for 163840 bytes
[17180148.952000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180148.952000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc2d2cc40 for 163840 bytes
[17180152.364000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8a06000 for 196608 bytes
[17180152.364000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180152.364000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc2d2cc00 for 196608 bytes
[17180162.408000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8f0b000 for 163840 bytes
[17180162.408000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17180162.408000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc2d2cbc0 for 163840 bytes
[17180165.920000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa8a

(This one carries on giving the same problem over and over again, I can't physically post it all!)

**The fourth:**

0000:00:00.0 Host bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

---

### Post by calvinthomas on 2006-08-19
BTW as an update if I use network settings in ubuntu and enable wireless, when I press ok, if I go back into it, it is inactive again! I am running on a wire at the moment!

The router itself is set up (it works on all other computers and on my windows partition)

Calv

---

### Post by bensexson on 2006-08-19
OK good for the wireless you have it working.  Do you know how the router is configured?  Do you know the ssid? Do you know what if any encryption is being used?  Look at the output from sudo iwlist eth1 scan.  Post the output if you have questions.  The fglrx errors from dmesg are from the fglrx drivers for your ATI video card.

---

### Post by calvinthomas on 2006-08-19
eth1 I think is my cabled connection, eth0 seems to be my wireless connection (or lack of it).

The router was only installed today so no encryption of any sort has been put on it as of yet.

Putting the code you mentioned in to a terminal on eth1 it gives me:

eth1      Interface doesn't support scanning : No such device

and on eth0 it gives me:

eth0      Interface doesn't support scanning.

Sorry I can't be more helpful with diagnosing my problem and stuff, i'm not very technical (particularly on wireless networks!)

Calv

---

### Post by bensexson on 2006-08-19
eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s
RTS thrff Fragment thrff
Encryption keyff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

This is your wireless.  What did you do to get this working to the point it is? Post the output from lsmod | grep bcm43xx and lsmod | grep ndiswrapper.

---

### Post by calvinthomas on 2006-08-19
**The First:**

bcm43xx               138892  0 
ieee80211softmac       32384  1 bcm43xx
ieee80211              40072  2 bcm43xx,ieee80211softmac

The second doesn't give any output at all, just goes to the next line!

I didn't do anything to get it to where it is, I haven't played with the wireless at all except for going in to networking and trying to activate the wireless.

Calv

---

### Post by bensexson on 2006-08-19
Look here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
This should guide you to get your wireless working.  You probably need touse fwcutter to get the firmware or use ndiswrapper instead.

---

### Post by calvinthomas on 2006-08-19
Thanks for the link, following the guide 'improved' things but didn't fix things, now I have an active wireless connection in networking (at least it says active) but I cannot get online, instead of saying the page cannot be displayed it just sits on looking up site and goes nowhere, also when I scan ports it says: No Scan Results rather than what it previously said, also my wireless light (My laptop has a light when the wireless connection is being activated) comes on and stays on for a few seconds every so often, in windows when its working the light flickers rather than staying on constant or off constant.

Don't know if any of the above helps, any help appreciated though!

Calv

---

### Post by calvinthomas on 2006-08-21
bump. No-one know what I can do?

Calv

---

### Post by compwiz18 on 2006-09-01
if you've got a bcm4318 try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

(the post will tell you how to check if you do)

---

