---
title: "Madwifi problem."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-09-17
Ive been following the instructions on [http://madwifi.org/wiki/UserDocs/AccessPointInterface](http://madwifi.org/wiki/UserDocs/AccessPointInterface) to create an AP, but I've been unable to get my wi-fi devices to recognize it.

I've just noticed that when I try to get my device to connect the "Rx invalid nwid:" portion of the iwconfig output increases a little.
```

nwm@nwm-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:15:E9:B4:D5:88   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:82  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Kitsun on 2007-09-17
Bump, got pushed back to 3rd page :'(

---

### Post by reckless2k2 on 2007-09-17
i don't understand your question. are you having problems connecting?

---

### Post by Kitsun on 2007-09-17
I am attempting to run my DWLG650 (Atheros) Wi-Fi card as a Access Point and have my Nintendo DS connect to it.

The only interaction I have gotten between the laptop and the DS is the incrementation of the "Rx invalid nwid" stat on the output of "iwconfig"

---

