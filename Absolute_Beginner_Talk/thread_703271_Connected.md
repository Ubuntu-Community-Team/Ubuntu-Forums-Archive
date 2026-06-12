---
title: "Connected"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-02-21
--------------------------------------------------------------------------------

Hi,

First of all im pretty new to the linux scene, so excuse me if the answer to my question is easy 

I have a the following Wifi Network Controller (Output of lspci) :

Broadcom Corporation BCM4368 882.11b/g Wireless Lan Controller (rev 03)

I have a Wifi Router at home... which uses a simple WEP Key... 12 character

When attempting to connect to the Wifi Router i need to enter the pass key.. the only method which i successfully managed to authenticate to the router is by using the WEP 64/128-bit HEX... no other method has managed to authenticate...

Now... it appears that i have obtained an IP address from the DHCP Server from the router... and am able to connect to it... however i cannot ping any machine within my local lan nor browse the internet.

If i connect the Laptop via a UTP cable to the Router... Internet Works Fine....

Note... i am currently using the restricted drivers BCM43xx.

I believe this has got to do with the pass key in some sort... since normally i never get these issues when an Access Point doesn't have any Pass Key (Not that that is recommended) 

Thanks for any feedback you can give!

Mark

PS... this is a dual boot... if i boot with WinXp i will be able to connect to the internet... so i doubt that this is a Router Mis configuration

---

### Post by jan quark on 2008-02-21
try to configure your network manually

system > administration > network
and set a static ip

perhaps this will work

please post also the results of these terminal commands
```
sudo lshw -C network
```
```
iwconfig
```
```
ifconfig
```
```
sudo iwlist scan
```
```
cat /etc/network/interfaces
```

---

### Post by markbusu on 2008-02-21
I tried setting a static IP address... however the same...

However im getting an IP from the DHCP Server... The results are as follows:

sudo lshw -C network
==============

Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

iwconfig
=====

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"default"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:40:F4:DD:81:E0   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=75/100  Signal level=-52 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:480  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mark@marknotebook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:7B:06:B6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:0F:B4:2D  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:7dff:fe0f:b42d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9062 errors:0 dropped:19774 overruns:0 frame:0
          TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4909402 (4.6 MB)  TX bytes:120867 (118.0 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17222 (16.8 KB)  TX bytes:17222 (16.8 KB)

sudo iwlist scan
==========
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:F4:DD:81:E0
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-43 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 68ms ago
          Cell 02 - Address: 00:03:2F:29:03:44
                    ESSID:"ACLHOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-81 dBm  Noise level=-70 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1488ms ago

cat /etc/network/interfaces
=================

auto lo
iface lo inet loopback


Thanks!

---

### Post by markbusu on 2008-02-21
Bump :)

---

### Post by jan quark on 2008-02-21
please run this command again be sure to type it correctly

```
sudo lshw -C network
```

---

