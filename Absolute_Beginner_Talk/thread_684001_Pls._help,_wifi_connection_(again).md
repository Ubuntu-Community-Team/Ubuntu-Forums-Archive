---
title: "Pls. help, wifi connection (again)"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by relsafus on 2008-01-31
I,m sorry but why is this so complicated in Linux/ubuntu world ?
The PCMCIA adapter I use is D-Link DWL-G650+ rev B1 and I can use WPA encryption in windows, no problema,,

In Ubuntu 7.10, I can see my Router, and all the wifi sones in my area..
I have used "wiemano1" HOWTO: Wireless..WPA1 etc guide, all the way, but now fun.

The problem is my new Router D-Link DIR 365 only support WPA1/WPA2.
After using some night time hour, I give up this Card. 

So I buy me a pretty new one from D-Link, USB devise, who should match my Router, with exelent speed. Again this works in a minute in Windows..., but in Linux world, the card is not even on my Network list..

Back to start DWL G650+

I edit the /etc/network/interfaces with all the options, no luck

ifcongig
eth0      Link encap:Ethernet  HWaddr 00:02:A5:C2:1F:12  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fec2:1f12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1406375 (1.3 MB)  TX bytes:162281 (158.4 KB)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
wlan0     Link encap:Ethernet  HWaddr 00:11:95:6D:FB:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1362 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 
wlan0:ava Link encap:Ethernet  HWaddr 00:11:95:6D:FB:23  
          inet addr:169.254.7.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11b+/g+  ESSID:"STA6DFB23"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=35/100  Signal level=9/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon0

auto wlan0
iface wlan0 inet dhcp
wpa-driver madwifi (try all the options here...)
wpa-ssid valhal (my router)
wpa-ap-scan 1 
wpa-proto WPA 
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 6f6c2ce694ab1ade26f2b2cb935b..................004f

Before this, I start "sudo apt-get install wpasupplicant",

Should I buy another Card (I never give up), so please give me some advice.
plug & play with WPA support in Linux/ubuntu...(PCMCIA, because I cant figure out why USB dont show up.

Regards

Relsafus

---

### Post by Pulka on 2008-01-31
usually there´s some fix, wait for the solutions presented in the forum

---

