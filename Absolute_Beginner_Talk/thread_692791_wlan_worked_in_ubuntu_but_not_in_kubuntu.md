---
title: "wlan worked in ubuntu but not in kubuntu"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2008-02-10
Hello,

I just switched from ubuntu to kubuntu, not the desktops but a complete fresh install.

the thing is I cant get me wlan to work, here is the result of my konsole and what I did.

```

bash: ifonfig: command not found
faraz@laptop-kubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F3:86:16
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2432 (2.3 KB)  TX bytes:2432 (2.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5B:79:9B:49
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:19:5B:79:9B:49
          inet addr:169.254.6.20  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-79-9B-49-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


faraz@laptop-kubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:5b:79:9b:49
Sending on   LPF/wlan0/00:19:5b:79:9b:49
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

faraz@laptop-kubuntu:~$ sudo dhclient wlan0:ava
There is already a pid file /var/run/dhclient.pid with pid 5767
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
```

---

### Post by faraz_k86 on 2008-02-10
anyone??

---

### Post by jan quark on 2008-02-10
pls run the following commands and post the output
thank you


```
iwconfig
```

```
sudo iwlist scan
```

```
lspci
```

```
sudo lshw -C network
```

---

### Post by faraz_k86 on 2008-02-12
k here is the report of the above commands

```

bash: iwcofig: command not found
faraz@laptop-kubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

faraz@laptop-kubuntu:~$ sudo iwlist scan
[sudo] password for faraz:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:F1:B1:D9:8F
                    ESSID:"belkin54g"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-40 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000026a9d617

faraz@laptop-kubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
07:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
faraz@laptop-kubuntu:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:f3:86:16
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 00
       serial: 00:19:5b:79:9b:49
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
faraz@laptop-kubuntu:~$   
```

---

### Post by faraz_k86 on 2008-02-12
is there something wrong with my reports??

---

### Post by faraz_k86 on 2008-02-13
this never happened before on ubuntuforums.  its been 2 days and still I have no replies.

:(

---

### Post by Joeb454 on 2008-02-13
People will be looking at your thread. You have to remember that we can't all come up with a solution that easily. It might be a bug...in which case it'll be a while. It might be editing a config file, which means it wouldn't take long.

You also have to bear in mind that we all have other things to be doing as well as helping out on the forums :)

---

### Post by rkd on 2008-02-13
Here is an account by one guy who says there is a problem in knetworkmanager. He has a workaround.

   [http://mikosuria.freehostia.com/blog/2008/02/02/connect-your-rt61-to-the-wireless-network/](http://mikosuria.freehostia.com/blog/2008/02/02/connect-your-rt61-to-the-wireless-network/)

Here is a HOWTO for getting Ralink devices to work:

   [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

I don't know which is better for you to try.

---

### Post by faraz_k86 on 2008-02-13
thanks but the guide tells me to install the network manager......... that can be good? how do i get it back?


also my wireless is a belkin D-Link DWL-G630

---

### Post by Crooksey on 2008-02-13
```

sudo iwconfig wlan0 essid "belkin54g"
sudo dhclient wlan0
```

Does that not work?

If not try...

```

sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid "belkin54g"
sudo dhclient wlan0
```

---

### Post by faraz_k86 on 2008-02-14
thanks crooksey but none of them seem to work.

should I move on to another distro?

---

### Post by rkd on 2008-02-15
> **faraz_k86 said:**
> thanks but the guide tells me to install the network manager......... that can be good? how do i get it back?


also my wireless is a belkin D-Link DWL-G630
You won't need the network manager (it doesn't work right, anyway). The directions in that post tell how to do all the things the network manager is supposed to do for you.

Your wireless card is from a different manufacturer, but it uses the same electronics (RaLink RT2561/RT61) as the card in that post, so the same directions should work for you.

---

### Post by faraz_k86 on 2008-02-15
i followed that guide, but that screwed it up even more.

now it cannot even detect my card :(

---

### Post by rkd on 2008-02-15
Which of the two I mentioned did you follow?

---

### Post by faraz_k86 on 2008-02-15
this one : [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

---

### Post by rkd on 2008-02-15
Did you have any problems while going through the steps of that guide? Error messages? Did you get the files expected when you unziped the windows drivers? Anything that might be a hint that something wasn't right during the procedure, or did you just get all the way to the end and find it doesn't see the card?

I have to be leaving soon, so I might not respond to your next posting right away. I'll get to it as soon as I am able to.

---

