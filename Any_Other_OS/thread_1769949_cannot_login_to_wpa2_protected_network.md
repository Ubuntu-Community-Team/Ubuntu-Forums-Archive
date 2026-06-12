---
title: "cannot login to wpa2 protected network"
date: 2011-05-28
forum: Any Other OS
---

### Post by n3140f on 2011-05-28
I am living with my folks and cannot go and rest the router.  

I am now using Linux Mint 11 Katya.  Kernel 2.6.38-8-generic-pae.

The machine is a HP dm3 1030us.

I have been working on this for over a month and I really need to go wireless.

I have been reading the Forums and using google and other sites.

After spending a lot of time, I still don't know what the problem is!

lspci reveals:


this machine is an HP dm3 1030us with the atheros 5009 adapeter.



02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


mintwifi reveals:
 I. scanning WIFI PCI devices...
sh: cannot create /tmp/detected_wireless_devices: Permission denied
  -- Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
      ==> PCI ID = 168c:002a (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:21:cc:3f:73:9f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe3f:739f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64669404 (64.6 MB)  TX bytes:5942013 (5.9 MB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:ee:e7:16  
          inet6 addr: fe80::222:5fff:feee:e716/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5265 (5.2 KB)  TX bytes:14726 (14.7 KB)

-------------------------
* V. querying DHCP...


I still don't know what the problem is.  Hardware - Software - I don't know.

---

### Post by Perfect Storm on 2011-05-29
Moved to Other OS/Distro Talk.

---

### Post by VanR on 2011-05-29
You probably need the proper password. You can usually find it under networking in Windows (if you folks are running Windows). It's usually a number about 24 digits long.!!!!!!

---

