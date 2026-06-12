---
title: "How to use iMac as a wireless router under linux?"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by felixdzerzhinsky on 2008-04-25
I am running OS X, linux and Windows XP with a cable modem. Occasianally I need to share with my laptop. I can do the following under Mac OSX. 

[http://www.macinstruct.com/node/118](http://www.macinstruct.com/node/118)

What I would like to know is there a way I can do it with linux?

And Windows XP? (Pushing my luck here!)

Thanks

---

### Post by cyberdork33 on 2008-04-25
> **felixdzerzhinsky said:**
> I am running OS X, linux and Windows XP with a cable modem. Occasianally I need to share with my laptop. I can do the following under Mac OSX. 

[http://www.macinstruct.com/node/118](http://www.macinstruct.com/node/118)

What I would like to know is there a way I can do it with linux?

And Windows XP? (Pushing my luck here!)

Thanks

In Windows, you use Internet Connection Sharing to make your machine an Access Point.

I think you can create an AP with Ubuntu in the Network Administration tool in System > Administration, but I don't know that it will assign IPs automatically like OSX and WinXP without some other work.

---

### Post by felixdzerzhinsky on 2008-05-24
The solution may be here.

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

---

### Post by felixdzerzhinsky on 2008-05-30
This is my setup under Ubuntu:

```
pjharper@pjharper-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"'FelixDZ'"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 56:D1:62:41:17:60   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pjharper@pjharper-desktop:~$ ifonfig
bash: ifonfig: command not found
pjharper@pjharper-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:cb:9c:f1:26  
          inet addr:202.93.10.220  Bcast:202.93.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:fe9c:f126/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1843959 (1.7 MB)  TX bytes:376198 (367.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119112 (116.3 KB)  TX bytes:119112 (116.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:f2:96:fa:5a  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fe96:fa5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2592 (2.5 KB)  TX bytes:510 (510.0 B)
          Interrupt:17 Memory:4a200000-4a204000 
```


What do I need to do so that my Vista Machine can connect?

Vista: Use the Following Address:

IP Address: 192.196.0.5
Subnet Mask:255.255.255.0
Default Gateway: ???.???.???.???


Use the Following DNS Server:

Preferred: ???.???.???.???

---

### Post by felixdzerzhinsky on 2008-06-01
My /etc/network/interfaces
#
## wireless bridge configuration
#
auto lo
#
iface lo inet loopback
#

iface eth0 inet dhcp
auto eth0

auto wlan0
iface wlan0 inet static
         wireless-key c!)ck
         wireless-channel 6
         wireless-mode ad-hoc
         wireless-essid 'FelixDZ'
         address 192.168.0.2
	 gateway 192.168.0.1
         netmask 255.255.255.0

---

### Post by felixdzerzhinsky on 2008-06-01
Problem Solved

The problem was that I had to remove the reference to "gateway" in my /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
        wireless-key 1234567890
         wireless-channel 6
         wireless-mode ad-hoc
         wireless-essid 'FelixDZWDC'
         address 192.168.0.1
         netmask 255.255.255.0
```

Another command that helped in troubleshooting this was:
```

route -n
```

Thanks to Lynet on IRC.

This would probably work on any PC as well as an iMac. Still I hope the developers will make something a little easier in the future.

---

