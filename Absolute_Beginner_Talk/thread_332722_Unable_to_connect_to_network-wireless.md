---
title: "Unable to connect to network-wireless"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Baethan on 2007-01-06
I have a BCM4318 wireless card (I'm fairly certain) and it's causing me no end of trouble. I've gone through every guide and FAQ I could find. I have made some progress with it, but I still can't get online. I installed WiFi Radar- it can see all the nearby the networks, but when I try to connect to mine (the settings look correct), it says it can't find the IP address. 
This is what iwconfig says:
lo: no wireless extensions.
eth0: ditto
 
eth1:IEEE 802.11g ESSID: off/any Nickname:Wireless@Home
Mode:Managed Frequency: 2.462 GHz Access Point:Not-Associated
Bit Rate=54 Mb/s Tx-Power:25 dBm
RTS thr=2347 B Fragment thr=2346 B
Encryption key:[key here, too lazy to type it out] Security mode:restricted
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
sit0: no wireless extensions
 
In Networking, the wireless connection is setup with the network name (Wireless@Home) and the key. 
 
Additional Info: I'm using 6.10. The computer in question has no access to the internet at all, so I'm currently using another computer running windows. 
 
I have no idea where to go from here- any help is greatly appreciated!

---

### Post by Vorian on 2007-01-06
```
sudo dhclient eht1
```

---

### Post by Baethan on 2007-01-06
> **Vorian said:**
> ```
sudo dhclient eht1
```
 
I've done that. I've done everything on this page: [http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102), and the guide that it links to towards the bottom.
 
Edit: Would anything happen if I did it again? I wouldn't think so, but you never know...

---

### Post by Baethan on 2007-01-06
Should I do a clean install of Ubuntu? I'd really rather not, but if that's the only way to get the stupid wireless card working, that's what I'll do.

---

