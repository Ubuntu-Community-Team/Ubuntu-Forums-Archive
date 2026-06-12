---
title: "Need Help Connecting to my network."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by wushufunk on 2008-01-27
i cannot connect to my wireless network though it is recognized by my wireless adaptor. when it asks for the wep code i type it in and it rejects it every time and im certain im typing it in right. im using an external usb lynksys wirelss g adaptor. halp! please this is driving me crazy, im loving linux and i dont want to switch back to vista just because of this.

---

### Post by emarkd on 2008-01-27
Just to be sure, have you tried disabling the encryption on your wireless network to see if you can connect without the WEP?  I've personally never had a problem on any network I've been on, encrypted or otherwise...

---

### Post by wushufunk on 2008-01-27
yes and that still hasnt work. i think it must be something wrong with the adaptor, meaning i have to get a new one, but is that even possible if its recognizing the network?

---

### Post by jan quark on 2008-01-27
please post the results of the following terminal commands

iwconfig
ifconfig
lspci
sudo iwlist scan

that will help to shed some light on your network status

---

### Post by wushufunk on 2008-01-27
Ok these were the results of the tests it ran, one of themn wouldnt go through.



iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:19:D1:52:0A:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22432 (21.9 KB)  TX bytes:22432 (21.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:B6:94:D8:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4052 (3.9 KB)  TX bytes:9465 (9.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-94-D8-DA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

