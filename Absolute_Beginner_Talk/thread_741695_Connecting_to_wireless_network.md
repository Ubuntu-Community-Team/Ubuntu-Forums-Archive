---
title: "Connecting to wireless network"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Jacksonstevena on 2008-04-01
I am having a lot of trouble getting connected to the internet. I am a complete linux noob so bare with me. First off, I am running the latest beta of hardy. 
Here is my situation I have a belikin f5d7010 pci card, the hardware test recognizes my broadcom 43xx chipset. That's a great start. I am trying to connect to a WEP 64 bit system.

here is my iwconfig

lo      no wireless extenstions
eth0  no wireless extensions
irda0  no wireless extensions
wlan0 IEEE 802.11g   ESSID: "NETGEAR"
Mode:Managed     Channel:0               Access point: Not-Associated
Tx-power = 0 dmb


I don't understand, is wlan0 detecting my device or is that just the network information I provided it.
If it is detecting my hardware ( might I add the lights on the card are not blinking) why does it not work?:confused:

---

### Post by Jacksonstevena on 2008-04-01
Also I have tried running other distros and in all distros the trackpoint on my r31 thinkpad keeps flipping out randomly and selecting the shut down button, any advice on this?

---

### Post by joshrobinson on 2008-04-01
for the trackpad, try installing gsynaptics

```
sudo apt-get install gsynaptics
```
that will let you adjust the sensitivity and tap to click options


for the wireless, post your entire iwconfig and ifconfig commands

---

### Post by Helios1276 on 2008-04-01
This might help? Haven't tried it myself yet mind 
[http://ubuntuforums.org/showthread.php?t=737549](http://ubuntuforums.org/showthread.php?t=737549)

---

### Post by Jacksonstevena on 2008-04-01
ok here is the continuation of my iwconfig 
retry min limit:7      RTS thr:off       Fragment  thr=2346 B

Link Quality 0    Signal level: 0      noise level: 0
Tx excessive retries: 0 Invalid misc:0 Missed beacon: 0



Here is my ifconfig

Eth0      Link encap: Ethernet        HWaddr  00:00:e2:81:fd:61
              UP BROADCAST MULTICAST      MTU:1500     METRIC:1
              RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
             Txpackets: 0 errors:0 dropped: 0 overruns:0 carrier: 0
collisions:0 txqueuelen: 1000

lo  Link encap: Local loopback
Inet addr: 127.0.0.1   mask 255.0.0.0
Inet6 addr:  ::1/128 Scope:host
UP LOOPBACK RUNING MTU:16436 METRIC:1
RXPACKETS:1204 errors:0  dropped:0 Overruns:0 frame:0
Tx packets: 1204 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 
Rx bytes: 60392 (58.9 KB) Tx Bytes: 60392 (58.9KB) 








I hope this helps because I have no clue what im looking at, I bought linux for dummies read some of it and am still a dummy.

---

### Post by Jacksonstevena on 2008-04-01
> **Helios1276 said:**
> This might help? Haven't tried it myself yet mind 
[http://ubuntuforums.org/showthread.php?t=737549](http://ubuntuforums.org/showthread.php?t=737549)

For some reason under hardware drivers..... It lists absolutely nothing. whats up with that?

---

### Post by Jacksonstevena on 2008-04-01
joshrobinson Where in Jersey are you from I'm in Bergen county

---

### Post by Helios1276 on 2008-04-01
I'm gonna try it myself later this evening and if it works for me i'll give you a run down of what I did.

---

