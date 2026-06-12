---
title: "Wifi problem with driver already installed"
date: 2013-09-29
forum: Apple Hardware Users
---

### Post by stefan9 on 2013-09-29
Hello I'm a very new beginner in UNIX systems and I want to learn. I have a big problem with my mcbook pro 4,1 wifi does not work I don't what to do anymore is does not search for wif I can not connect to wifi. 

```
boo@boo-MacBook:~$ sudo iwconfig
[sudo] password for boo: 
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"sarmale"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:2358-0857-01
          Power Management:off


boo@boo-MacBook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61)



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:41:3c:fb:e0  
          inet addr:192.168.0.66  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:41ff:fe3c:fbe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1839583 (1.8 MB)  TX bytes:338695 (338.6 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52132 (52.1 KB)  TX bytes:52132 (52.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:23:12:04:47:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I tried to connect to a wireless with sudo iwconfig wlan0 essid name key **** and then dhclient but it does not work I don't what to do.

If you need more information let me know please.

---

### Post by jmjmail on 2013-09-30
have you installed the driver ? 
http : // askubuntu.com /questions /313626/no-wireless-in-kernel-3-9-0
you have to remove spaces i cant post links

---

### Post by stefan9 on 2013-10-01
Yes I tried, when I install the kernel driver the wifi is not working at all is not detecting anymore. Right now wifi is working but only in my house Idk why, and every time I have to conect with sudo iwconfig wlan0 essid. How to make it work like searching for wifi? thank you

---

