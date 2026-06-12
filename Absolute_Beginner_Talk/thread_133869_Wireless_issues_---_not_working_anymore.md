---
title: "Wireless issues --- not working anymore"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bubbadawg on 2006-02-20
Hello All ---

I am having problems getting my Intel 2200 WiFi card to work. It has worked fine for the past few days, but tonight it stopped working and I can't get it working. 
Not sure what you will need (I am new to this) so here is both iwconfig and ifconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"wifi1313"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----------
eth1      Link encap:Ethernet  HWaddr 00:13:CE:EF:76:82
          inet6 addr: fe80::213:ceff:feef:7682/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 Memory:dfcfd000-dfcfdfff

```

I did attempt to install network-manager and the gtkwifi. Not sure if this would have caused my problems. I removed network-manager as I 
thought it could be the problem, but it didn't resolve the issue.

Thanks for any and all replies.

---

### Post by bubbadawg on 2006-02-21
Resolved - somehow the Wireless got disabled in the bios giving me a "Radio Frequency Kill Switch is on" message.

---

