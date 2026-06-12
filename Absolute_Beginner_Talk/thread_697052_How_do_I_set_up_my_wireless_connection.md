---
title: "How do I set up my wireless connection?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-02-14
Ok, I've been avoiding this one.. but I got to finally take care of it. How can I do this? Here is some information:

```
harrison@machine:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c2:c4:7d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=99.232.169.146 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

```

Any help or a point towards a good, clear tutorial would be very much appreciated. :grin:

---

### Post by jan quark on 2008-02-14
I think your card is supported by ubuntu and the drivers are pre-installed

so you need only to configure it 

see here

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

can you please post also the output of these terminal commands

just to be sure that everything is set up correctly

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

---

### Post by incen on 2008-02-14
Well... I just got Xubuntu on my laptop today and started to use wireless with it. However, I came back home and used the secured wireless at home. I'm wondering if Xubuntu will remember my key to the wireless rounter or not. If not, then how should I do to make it "yes"? Thanks! :)

---

### Post by h-town on 2008-02-14
iwconfig

```
harrison@machine:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

ifconfig

```
harrison@machine:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harrison@machine:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:C2:C4:7D  
          inet addr:99.232.169.146  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:b8ff:fec2:c47d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73611315 (70.2 MB)  TX bytes:4143939 (3.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

sudo iwlist scan

```
harrison@machine:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

harrison@machine:~$ 

```

---

### Post by PeterJS on 2008-02-14
> **h-town said:**
> Ok, I've been avoiding this one.. but I got to finally take care of it. How can I do this? Here is some information:

```
harrison@machine:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       **logical name: eth0**
       version: 14
       serial: 00:e0:b8:c2:c4:7d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=99.232.169.146 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

```

Any help or a point towards a good, clear tutorial would be very much appreciated. :grin:

Now that doesn't make any sense... If you look at the marvel card you'll see that it has a logical name, the intel card should have one too, I wonder if the driver module for it is actually loaded?
Try this
```

lsmod | grep ipw3945

```
If it finds something consider me officially confused, if it doesn't then the driver for the card isn't actually loaded (which is weird it should be), then you can load the driver with:
```

sudo modprobe ipw3945

```

Looking at my own card I get:
```

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:5d:fe:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: **broadcast=yes** driver=ipw3945 **driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.3.4** latency=0 module=ipw3945 **multicast=yes wireless=IEEE 802.11g**

```
It has all those extra options which further makes me think the driver isn't loaded

---

### Post by h-town on 2008-02-14
harrison@machine:~$ lsmod | grep ipw3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945

---

### Post by incen on 2008-02-14
I have some problem setting up my wirelss connection as well. I'm wondering how to do to make Xubuntu remember my key to the wireless access. Otherwise, it's really a pain to enter it every time.

I tried with what this page says:
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
However, it didn't work at all for me. After selection DHCP, the wireless just stopped working. Besides, after rebooting my computer (switching from Windows to Xubuntu), it showed something like: "nm-applet" tried to access some locked file. To unlock, type in key. However, the key to my root didn't work. Which key!?!?

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SMC"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:E2:DE:47:9B   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=-42 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

irda0     no wireless extensions.
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:41:52:A1:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:0A:D2:DA  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe0a:d2da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2990564 (2.8 MB)  TX bytes:205108 (200.3 KB)
          Interrupt:11 Base address:0xe000 Memory:c0210000-c0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:04:E2:DE:47:9B
                    ESSID:"SMC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-45 dBm  
                    Extra: Last beacon: 164ms ago

irda0     Interface doesn't support scanning.

```

---

