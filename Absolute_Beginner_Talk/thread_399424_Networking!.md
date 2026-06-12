---
title: "Networking!"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Blue Summer on 2007-04-02
Hi all i've just got a new belkin g) mimo notebook card and im wondering how the heck i install this on my laptop *which currently has no internet connection* the main networked computer is running xp and has a netgear dg834gt router, anyone have a clue how i can install it?

im running breezy badger atm.

---

### Post by Blue Summer on 2007-04-02
hmmm i clicked on the 2 computer screens in the top right hand corner near the battery monitor/time, its found something on eth0 which the single seems to be right  in comparison to my router, also when i type iwconfig in, it told me it can find my network, im just stuck on how to activate my card...

---

### Post by Blue Summer on 2007-04-02
anyone?:popcorn:

---

### Post by cyberdork33 on 2007-04-02
please post output of ifconfig and iwconfig

---

### Post by david_kt on 2007-04-02
First of all, why do you use breezy? You should use dapper at least in my opinion. As I am not using breezy, I only could give you what is available on dapper i.e. go to 

```
system>administration>networking
```

and see whether or not your card is detected. IF it is detected, you just need to activate it and configure it.

DK

---

### Post by cyberdork33 on 2007-04-02
aye, missed the breezy part, I'd upgrade first as that will probably yield better hardware support...

---

### Post by Blue Summer on 2007-04-02
Right, i think it has found it and ive clicked activate but it won't connect or anything and in iwconfig it says its found my network. I cant copy the iwconfig and ifconfig because its quite long lol. Im using breezy because it was the only one available on shipit for free. As my proper computer crashes every 5 seconds and the internets just not working lol. So downloading it is pretty much outta the question unless anyone wants to send me it lol :)

---

### Post by Blue Summer on 2007-04-04
right, im using feisty now. It's sort of found my card, its found it as a mimo but under a different manufactorers name -ralink and its showing me how good the signal is, it's found 3 different wireless things under system>admin>network  wlan1, wlan0 and wifi0, thats under connections. Anyone can help me now?

Also can anyone tell me how to navigate to my desktop on the terminal?

---

### Post by cyberdork33 on 2007-04-04
post the output of iwconfig and ifconfig

---

### Post by Blue Summer on 2007-04-04
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"JacobsE"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:7D:2A:D2   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:"JacobsE"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:7D:2A:D2   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-73 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ifconfig:

```

rob@rob-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:18:85:0D:17  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe85:d17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:333213460 (317.7 MiB)  TX bytes:12159671 (11.5 MiB)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-05-3C-06-9F-3F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:576 (576.0 b)
          Interrupt:9 

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:10:75:04  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:522799 (510.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:10 

wlan1     Link encap:Ethernet  HWaddr 00:05:3C:06:9F:3F  
          inet6 addr: fe80::205:3cff:fe06:9f3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:576 (576.0 b)
          Interrupt:9 


```

---

### Post by cyberdork33 on 2007-04-04
It is finding (at least) two WiFi cards (one internal?). You need to determine which is which (Your card should be marked with the hardware address and will match one of those listed). The one with the Hardware address of 00-05-3C-06-9F-3F-00-00-00-00-00-00-00-00-00-00 looks like it might be a ethernet over firewire device. This might interfere with your other interfaces and may need to be disabled.

At the moment, I am going to assume that your card in question is the wlan0 device. This will probably be easier if you disable the card not being used. (You can do that in the network config you mentioned earlier)

You might also look into installing network-manager. It will simplify connecting to various networks.

---

