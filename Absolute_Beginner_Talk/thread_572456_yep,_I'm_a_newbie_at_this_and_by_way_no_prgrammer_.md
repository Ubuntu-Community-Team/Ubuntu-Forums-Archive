---
title: "yep, I'm a newbie at this and by way no prgrammer need help!!!!!!!!!!!"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by robhudson78 on 2007-10-10
Well , I would just like to say that I'm absolutely fascinated with Ubuntu and have completely switched out of error of accidently wiping windows during install....

My trouble is this....I don't know anything about programming, but I'm trying the best I can...this is what I got and I really need to get my WiFi working . Any help would be so much appreciated

robert@Hudson:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I'm having trouble figuring this out(configuring)

---

### Post by Het Irv on 2007-10-10
Alright. What kind of wireless card do you have and what version of Disto/version are you using?
Is there anything special about your wireless that might be useful to know?

---

### Post by nick_h on 2007-10-10
Try to scan for a router using:
```
sudo iwlist eth1 scan
```

---

