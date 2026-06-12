---
title: "wifi woes"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by aitutaki on 2008-01-15
Having finally managed to get a copy of Ubuntu Studio happily booting off an external hard drive, I'm now having problems with wifi. I installed a Belkin G+ USB adaptor using ndiswrapper, and it worked perfectly well. Until I restarted - now, the wireless connection doesn't come up under network at all, and when it eventually does (using depmod and modprobe) it still won't open up any web pages. When I scan in the terminal it picks up the connection fine .

Any help would be really, really appreciated - how ever much I love what I've seen of ubuntu, the amount of problems I've had are starting to make a return to windows seem like a better idea.

---

### Post by angryfirelord on 2008-01-15
First, let's see if it can get a DHCP address. After you've modprobed, run:
```
sudo iwconfig *name_of_Device* essid *name_of_router*
```
```
sudo dhclient *name_of_device*
```

---

### Post by aitutaki on 2008-01-15
No  DCHPOFFERS received

Er oh...

Thanks for your help - any idea what to do from here?

---

### Post by aitutaki on 2008-01-15
somebody?!?!

---

### Post by Whiffle on 2008-01-15
Could you post the output of iwconfig ?

---

### Post by aitutaki on 2008-01-15
iwconfig:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BeBox"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00: 90: D0: F6: 31: 31   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Cheers for the help.

---

