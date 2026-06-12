---
title: "Internet Connection Issues"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-01
So I got a brand new laptop today and after getting the XP Pro part of it running, I put Ubuntu on the other side. At first, internet was working great with a direct network connection. It then said that it had to update the system, and about 246 MB later, internet stops working. It did mention something about having to use restricted drivers for an Intel Pro/Wireless 3945 Network Connection driver for Linux, but I figured that only affects the wireless card, not the network port itself.

Could someone help me debug the Ubuntu part? Once I can get a stable internet connection I can take it from there (experience with Ubuntu on my desktop has paid off)

---

### Post by Bubba64 on 2008-03-01
I don't know but it might help to post the computer brand and specs.

---

### Post by superprash2003 on 2008-03-01
are you using DHCP? or manually typing an ip?go to terminal and type ifconfig and post results here!!

---

### Post by spacefreak86 on 2008-03-01
I think DHCP but I'll switch back to it and post results of ifconfig.


```



eth0   Link encap:Ethernet  HWaddr 00:1D:72:13:8B:17
          inet addr:192.168.1.103  Bcast:192.168.1.255   Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe13:8b17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:154 dropped:0 overruns:0 frame:602
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9969 (9.7 KB)  TX bytes:7571 (7.3 KB)
          Interrupt:16 



eth1      Link encap:Ethernet  HWaddr 00:1C:BF:00:29:B2
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe00:29b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:1 dropped:11 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1287 (1.2 KB)  TX bytes:4198 (4.0 KB)
          Interrupt:17 Base address:0xc000 Memory:f8000000-f8000fff



lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Computer Specs:

Acer Extensa 5620

Intel Core 2 Duo T5450 1.66 GHz
1GB DDR2 (soon to be upgraded to 1.5)
120 GB HD (partioned in half, XP Pro on one, Ubuntu Gutsy on the other)
Intel GMA X3100 Graphics Card
Moden, Gigabit LAN and WLAN

---

### Post by jan quark on 2008-03-01
please post also

```
iwconfig
```

```
sudo lshw -C network
```

```
cat /etc/network/interfaces
```

---

### Post by spacefreak86 on 2008-03-01
```
iwconfig:
lo              no wireless extensions.

eth0          no wireless extensions.

irda0         no wireless extensions.

eth1          IEEE 802.11g  ESSID:"linksys"
                  Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:1A:47:87
                  Bit Rate:48 Mb/s   Tx-Power:15 dBm
                  Retry limit:15   RTS thr:off   Fragment thr:off
                  Power Management:off
                  Link Quality=68/100  Signal level=-65 dBm  Noise level=-65 dBm
                  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:2   Missed beacon:0

bdizzle@bdizzle:~$ sudo lshw -C network

*-network
              description: Ethernet interface
              product: NetLink BCM5787M Gigabit Ethernet PCI Express
              vendor: Broadcom Corporation
              physical id: 0
              bus info: pci@0000:02:00.0
              logical name: eth0
              version: 02
              serial: 00:1d:72:13:8b:17
               size: 100MB/s
               capacity: 1GB/s
               width: 64 bits
               clock: 33MHz
               capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
               configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
  

*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth1
                version: 02
                serial: 00:1c:bf:00:29:b2
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.0.11 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g


bdizzle@bdizzle:~$ cat /etc/network/interfaces


auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid linksys  auto eth1

```


Right now I've only got it connected via a wire and its not connecting to the internet via that. I'll worry about wireless later.

---

### Post by spacefreak86 on 2008-03-01
So yeah, I tried looking through the site, but its all for wireless internet. I know that wired internet connection should just work, but its not. Did I enable something I shouldn't have?

---

### Post by superprash2003 on 2008-03-01
type ping google.com and see if you are able to ping!!

---

### Post by trdcelica on 2008-03-01
im sort of in the saem boat as the user who made this thread.....

my wireless card works,,,, i can ping all day long but my web page, IM, nothing works....

---

### Post by spacefreak86 on 2008-03-02
Just did a fresh install of Ubuntu, nothing works. I can't get any of the desktop effects to work due to Intel X3100 Integrated Graphics Controller, and I can't connect to internet using a wired connection. Ubuntu works great on my desktop, but yeah, unless I can get internet working on this laptop, I might be stuck with just XP Pro (I'm going to try openSUSE next as soon as I get some CD-R's to burn the .iso file.

Could someone help me at least get the wired connection to work? I've tried both roaming mode and DHCP and neither will connect. When I tried to ping to [www.google.com](www.google.com) it keeps saying that the network could not be found.

---

### Post by superprash2003 on 2008-03-03
if you can ping but cannot access any webpage.. then it could be a DNS problem.. go to system->administration->network->DNS-- click on add.. and add the following 2 ips
208.67.222.222 and 208.67.220.220 .. these are OPENDNS ips

---

