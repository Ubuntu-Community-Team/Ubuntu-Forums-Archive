---
title: "wireless not working"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-08
i just finished installing all the updates via ethernet, so i thought i would ry the wireless and set it up, everything was going fine i put in my wep key and now where the network icon is i go to see if the enable network is checked it is but enable wireless is gone, now it dont work, it sees wireless access points around and it connects to mine but does not authenticate. it keeps asking for the passphrase, i am using a MIMO netgear router what passphrase is it the key?

---

### Post by kevdog on 2007-10-08
Are you using WEP???

Please post
iwlist scan
lshw -C network

Thanks

---

### Post by tronnix75 on 2007-10-09
yes 128bit wep

---

### Post by tronnix75 on 2007-10-09
heres the output:

root@jeff-laptop:/home/jeff# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:43:1E:76
                    ESSID:"StayOut!!!"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000002a35e0027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010005ff7f
          Cell 02 - Address: 00:1B:2F:08:09:A8
                    ESSID:"home wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:16:B6:B5:E8:E2
                    ESSID:"Skazka"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:11:95:02:AF:16
                    ESSID:"WAP1"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:18:39:D1:A7:E1
                    ESSID:"Cinnamon House"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

root@jeff-laptop:/home/jeff# ishw -C network
bash: ishw: command not found
root@jeff-laptop:/home/jeff# iwlist scan lshw -C network
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
root@jeff-laptop:/home/jeff#

---

### Post by kevdog on 2007-10-09
Its lshw -C network -- with an l as in lollipop, not an i as in igloo.

Which one of those networks was yours?

Since you are using WEP, I think you need to enter the ASCII password for your WEP.  If not we can connect from the command line and use either the ASCII or HEX key

---

### Post by tronnix75 on 2007-10-09
my network is the stay out one,

---

### Post by tronnix75 on 2007-10-09
root@jeff-laptop:/home/jeff# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:86:05:3a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=N/A ip=192.168.4.40 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c0220000-c023ffff iomemory:c0200000-c020ffff ioport:8000-803f irq:11
  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:41:23:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=192.168.4.41 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11a
       resources: iomemory:c0210000-c021ffff irq:11

---

### Post by kevdog on 2007-10-09
One last question and then Ill get around to making my point.

You are running the madwifi driver.  When you type ifconfig at the command line, are you getting ath0 or ath1 listed in addition to wifi0??

One side note -- we will find out later if the !!! characters in your ESSID are legal.  I thought in many cases on linux that the ESSID had to consist of numbers and letters.  I guess I will learn something if you manage to connect.

---

### Post by tronnix75 on 2007-10-09
root@jeff-laptop:/home/jeff# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:05:4E:41:23:EF  
          inet addr:192.168.4.41  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe41:23ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:11:25:86:05:3A  
          inet addr:192.168.4.40  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe86:53a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1754008 (1.6 MiB)  TX bytes:601143 (587.0 KiB)
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2868 (2.8 KiB)  TX bytes:2868 (2.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-41-23-EF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:5
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8198 (8.0 KiB)  TX bytes:3890 (3.7 KiB)
          Interrupt:11 
i guess not

---

### Post by tronnix75 on 2007-10-09
can anyone help on this?

---

### Post by tronnix75 on 2007-10-09
is there no one that can help on this issue, i really need my wireless to work

---

### Post by tronnix75 on 2007-10-09
> **kevdog said:**
> One last question and then Ill get around to making my point.

You are running the madwifi driver.  When you type ifconfig at the command line, are you getting ath0 or ath1 listed in addition to wifi0??

One side note -- we will find out later if the !!! characters in your ESSID are legal.  I thought in many cases on linux that the ESSID had to consist of numbers and letters.  I guess I will learn something if you manage to connect.

Hi are you going to make your point on this, i need your help thanks man dude or dudet:guitar:

---

### Post by tronnix75 on 2007-10-11
> **tronnix75 said:**
> root@jeff-laptop:/home/jeff# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:05:4E:41:23:EF  
          inet addr:192.168.4.41  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe41:23ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:11:25:86:05:3A  
          inet addr:192.168.4.40  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe86:53a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1754008 (1.6 MiB)  TX bytes:601143 (587.0 KiB)
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2868 (2.8 KiB)  TX bytes:2868 (2.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-41-23-EF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:5
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8198 (8.0 KiB)  TX bytes:3890 (3.7 KiB)
          Interrupt:11 
i guess not

I guess no one can help me on this what crap

---

