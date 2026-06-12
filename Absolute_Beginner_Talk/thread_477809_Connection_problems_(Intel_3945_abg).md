---
title: "Connection problems (Intel 3945 abg)"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by skhelter on 2007-06-18
Apparently, my computer already has the necessary drivers for its wireless, but I still can't get a connection on it for some reason. This is what I have so far: 

```

brian@brian-laptop:~$ lsmod | grep ipw
ipw3945               124576  1 
ieee80211              35272  1 ipw3945
brian@brian-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:a6:03:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:dcfff000-dcffffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:38:05:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:dcbfe000-dcbfffff irq:177
brian@brian-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:38:05:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12572 (12.2 KiB)  TX bytes:12572 (12.2 KiB)

brian@brian-laptop:~$ sudo iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49149   Missed beacon:0

```

If it matters, I am trying to connect to a linksys WRT54GS router, though I'd certainly like to be able to connect elsewhere as well. Can anyone help me out here? If you need any more clarification as to my problem, please feel free to ask.

---

### Post by skhelter on 2007-06-18
bump

---

### Post by skhelter on 2007-06-18
bump =/

---

### Post by zachflanders on 2007-06-20
I have the same card.  I've tried about a millions things from a million threads and nothing seems to work. 

Information:
I am running ubuntu studio.
I had to install  pptpd and pptp-linux to connect to my wired connection in my dorm, and I have to run the following every time i want to connect to the internet:

chmod 755 vpn.sh
sudo ./vpn.sh start

Here is some more information for yall:

```
zach@zach:~$ lsmod | grep ipw
ipw3945               118944  1 
ieee80211              50924  1 ipw3945
zach@zach:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d6000000-d6000fff irq:17
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:71:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.67.231 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d8000000-d8000fff ioport:4000-403f irq:21
zach@zach:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:AF:71:5C  
          inet addr:192.168.67.231  Bcast:192.168.71.255  Mask:255.255.248.0
          inet6 addr: 2001:638:407:1e:216:36ff:feaf:715c/64 Scope:Global
          inet6 addr: fe80::216:36ff:feaf:715c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4247973 (4.0 MiB)  TX bytes:581022 (567.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63120 (61.6 KiB)  TX bytes:63120 (61.6 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:212.201.73.174  P-t-P:192.168.1.31  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:2904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2985704 (2.8 MiB)  TX bytes:392933 (383.7 KiB)

zach@zach:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

gre0      no wireless extensions.

ppp0      no wireless extensions.

```

can anyone help us?

PS -- my wireless was working fine under edgy, so it must be possible to get it to work on feisty, right?

---

### Post by molly_001 on 2007-06-20
Under feisty with 3945abg (which I have) you should be able to get wireless up pretty quickly.
 
Wireless card using BCM43XX-FWCUTTER (requires wired internet connection, or a cd with the package on it)
**sudo apt-get install bcm43xx-fwcutter**
**sudo modprobe bcm43xx**
then restart computer and all is good
**iwconfig **to check

(above paragraph from ghost_ryder35)
 
Use Network manager afterwards, make sure there is a checkmark in the radio button for both eth0 and eth1 simultaneously.
 
For eth0, in Properties, enable Roaming.  Then reboot.
 
After that (for some reason) you will always need to left-click on the swirling icon and choose *again a second time* with left click, the network you desire, and she should connect right up.

---

### Post by qsr.nrwn on 2007-06-24
I just tried what you have suggested, it works... thanks

---

