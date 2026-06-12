---
title: "Wireless connection seems to be detected but won't connect"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by harusp3x on 2007-01-04
I have an onboard Asus WiFi-AP Solo RTL8187 wireless network adapter. I installed the driver using ndiswrapper. I manually set up the ap to what my router gave as the Wireless MAC Address. After I input the ap, I checked the iwconfig and it apparently detects the signal since it finally stuck on the right channel, but I cannot figure out why it won't connect. I removed encryption from my router and used sudo iwconfig wlan0 key off to match.

Please help me!

Thank you.

---

### Post by meng on 2007-01-04
Try
sudo dhclient wlan0

---

### Post by zmuth734 on 2007-01-05
try:

```

sudo iwconfig wlan0
sudo iwconfig wlan0 essid <your essid here>
sudo iwconfig wlan0 key restricted <your key here>
sudo **ifconfig** wlan0 up
sudo dhclient wlan 0

```

---

### Post by harusp3x on 2007-01-05
Thanks, but no luck.

Here is the output:

iwconfig
```
wlan0     802.11b/g  ESSID:"InterScube"  
          Mode:Managed  Channel=2  Access Point: 00:18:39:C1:CC:9D   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:XXXX-XXXX-XX   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:05:9F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:4 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102 (102.0 b)  TX bytes:0 (0.0 b)
```

lshw
```
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:05:9f:6a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```


I had to set the AP manually to the Wireless MAC adress given by my router otherwise it would always list as Not-Associated. I also tried setting the AP to auto, but it would then list it as Invalid.

Also, my channel no longer sticks in the correct channel 11. It is now perpetually scrolling through every channel.

---

### Post by dannyboy79 on 2007-01-05
i think your problem is that your ap still has security set at something. this is in your iwconfig line:
Encryption key:XXXX-XXXX-XX   Security mode:open

what does iwlist scan return?

---

### Post by harusp3x on 2007-01-07
First off, it turns out I forgot to blacklist the native driver before running the ndiswrapper. So now I'm officially running the ndiswrapper version. But now I can't input an ESSID, it stays at *off/any*. The LED on the wireless card is off, so it isn't transmitting. I made sure to run *sudo ifconfig wlan0 up* but no luck.

Also iwlist scan returns no results for wlan0.

---

### Post by harusp3x on 2007-01-07
I tried native drivers, but I couldn't connect. Then I tried ndiswrapper drivers, but there was no detection. So I moved back to native drivers.

I am currently running the driver that came default with ubuntu 6.10. It seems to be picking up a signal, but not using it. Here are various command results.

*iwconfig*
```
wlan0     802.11b/g link..  ESSID:"InterScube"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


*ifconfig*
```
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:05:9F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10791 (10.5 KiB)  TX bytes:0 (0.0 b)
```



*iwlist scan*
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:C1:CC:9D
                    ESSID:"InterScube"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:11
                    Extra: Last beacon: 3ms ago
```


*sudo lshw*
```
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:05:9F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10791 (10.5 KiB)  TX bytes:0 (0.0 b)

```


It found the right channel and AP mac address. (I had given it manually in the past, but I have since reformatted. So it must be detecting the router.)

I have been working on this for 5 days and I am on my last leg here. Any solutions/suggestions?

Thank you very much.

---

