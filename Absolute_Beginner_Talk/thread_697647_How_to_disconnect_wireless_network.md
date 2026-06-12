---
title: "How to disconnect wireless network"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-15
When i type iwconfig i get this

ppp0      no wireless extensions.

root@coubury-desktop:/home/coubury# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0  RT61 Wireless  [COLOR="black"]ESSID:"WANADOO-DB30"  Nickname:"WANADOO-DB30"[/COLOR]
          Mode:Monitor  Frequency:2.442 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

This is wrong tho i dont have Wanadoo internet how do i delate this? its causing alot of problems!

---

### Post by Dr Small on 2008-02-15
What is your interface... ath0 or eth0?
Generally, to turn off network, you run:
```
sudo ifdown eth0
```

Dr Small

---

### Post by coubury on 2008-02-15
When i type iwconfig i get this

ppp0      no wireless extensions.

root@coubury-desktop:/home/coubury# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0  RT61 Wireless  [COLOR="black"]ESSID:"WANADOO-DB30"  Nickname:"WANADOO-DB30"[/COLOR]
          Mode:Monitor  Frequency:2.442 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

This is wrong tho i dont have Wanadoo internet how do i delate this? its causing alot of problems!

---

### Post by oldb0y on 2008-02-15
You could always deactivate your wireless-card...

---

### Post by macogw on 2008-02-15
Posting twice will not get you twice as much help.  It will just split up efforts to help and mean that info you post in one thread will not be visible to those helping you in another.

---

