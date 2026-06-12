---
title: "Ndiswrapper Worked? Or did it?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Kymac on 2007-05-15
I have this [Wireless Card](http://www.newegg.com/Product/Product.asp?Item=N82E16833135111)

After looking around, I found ndiswrapper, installed it, and followed it's directions.  When I run ndiswrapper -l in the terminal, it claims the driver is installed, and the device is found, or whatever.

However, I am still having problem connecting to my wireless router (even after taking off its encryption).  Is there a way to see if my card is even working?

Any Help would be appreciated.

---

### Post by n8bounds on 2007-05-15
run ```
 iwconfig 
```
you should see something like:
```


eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"n8x0rzLAN"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:5E:C1:E5
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

