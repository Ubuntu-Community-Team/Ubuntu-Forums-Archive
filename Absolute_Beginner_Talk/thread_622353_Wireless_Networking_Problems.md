---
title: "Wireless Networking Problems"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by neospartan on 2007-11-24
Just installed Ubuntu 7.10, and I am new to linux, but learning as I go. I checked around the forum and couldn't find a solution to my problem, or the cause of the problem for that matter. my laptop can detect the network, but seemingly cannot connect to other computers or access the internet. I posted  the results of various commands to speed things up.Thank you in advance.

*sudo iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Satellite Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A2:BE:8A   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality=93/100  Signal level=-45 dBm  Noise level=-46 dBm
          Rx invalid nwid:0  Rx invalid crypt:17  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

*ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:6D:F9:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:19:D2:86:BE:1E  
          inet6 addr: fe80::219:d2ff:fe86:be1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:50 dropped:52 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7309 (7.1 KB)  TX bytes:5426 (5.2 KB)
          Interrupt:18 Base address:0xc000 Memory:f0800000-f0800fff 

```
*iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:A2:BE:8A
                    ESSID:"Satellite Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-31 dBm  Noise level=-31 dBm
                    Extra: Last beacon: 16ms ago


eth0:avah Link encap:Ethernet  HWaddr 00:A0:D1:6D:F9:1E  
          inet addr:169.254.8.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth1:avah Link encap:Ethernet  HWaddr 00:19:D2:86:BE:1E  
          inet addr:169.254.6.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xc000 Memory:f0800000-f0800fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16188 (15.8 KB)  TX bytes:16188 (15.8 KB)

```
*route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```
*sudo iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       

```
*sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:86:be:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:6d:f9:1e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

```
Thank you in advance.

---

### Post by kelbizzle on 2007-11-24
It looks like the card still has a 169.254.x.x address. So we gotta get connected to your network first. on my laptop I use the nm-applet or you should be able to use
```
$ iwconfig eth1 ap (what ever your ap mac address is)
$ iwconfig eth1 essid (name of your router)
$ iwconfig eth1 key s:passphrase
$ dhclient eth1

```

Which type of card do you have?
```
$ lspci
```

---

### Post by neospartan on 2007-11-24
An Intel Pro/Wireless 3945ABG. Do I use the code in the terminal? I am a n00b, but I learn quickly.
"Do I use the code in the terminal? I am a n00b, but I learn quickly"
*N/m, brain fart

---

### Post by neospartan on 2007-11-24
Wait. What is an AP and how do I find its MAC Address? And is there some specific way to input my router's name?

---

### Post by neospartan on 2007-11-24
Maybe I should shut up and look? Access Point, and I found the MAC address.

---

### Post by neospartan on 2007-11-24
I ran it through twice, and I still got a no DHCPOFFERS

---

### Post by neospartan on 2007-11-26
Problems have been fixed, no need for this thread...

---

### Post by gsalem on 2007-11-27
Neospartan,
I've got probably the same problem (I cannot get mi 2945abg card to work properly, no DHCPOFFERS all the time). I'm interested by how you did solve your issue.

Thanks in advance

---

### Post by jadai on 2007-11-28
humm Goods thank You

---

