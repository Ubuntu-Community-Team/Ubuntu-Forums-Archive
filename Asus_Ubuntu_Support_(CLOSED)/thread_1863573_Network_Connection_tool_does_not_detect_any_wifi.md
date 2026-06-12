---
title: "Network Connection tool does not detect any wifi"
date: 2011-10-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tristan_ph on 2011-10-18
Im using Ubuntu Oneiric on Asus K43SV with AR9285 Wireless Network Adapter. 

I was able to connect through my wifi (with no key) but I did not display on Network connection on system tray. It is disabled and it says "Wireless Network device not managed".

I checked it through terminal using this command "iwconfig wlan0" and it seems ok. Here is the output:

```
wlan0 IEEE 802.11bgn  ESSID:"dd-wrt"  
Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:58:E6:D0   
Bit Rate=54 Mb/s   Tx-Power=15 dBm   
Retry  long limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=69/70  Signal level=-41 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:445   Missed beacon:0
```

It seems that its only the GUI that is not correctly display/scan my wifi network.

[IMG]http://i.imgur.com/23mDZ.png[/IMG]

I also tried connecting through wired connection and it works fine.

How do I fix this?

---

### Post by tristan_ph on 2011-10-18
I also posted this questing to askubuntu.com. Here is the link [http://askubuntu.com/questions/67313/network-connections-able-to-connect-to-wireless-but-network-connections-does-n](http://askubuntu.com/questions/67313/network-connections-able-to-connect-to-wireless-but-network-connections-does-n)

---

