---
title: "Connecting to Wifi signals from the terminal"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-31
Hey i've got a quick question regarding connecting to wifi signals through the terminal.  when i do iwlist scan i get a bunch of signals, two of which have the SAME NAME, as in ESSID.  Using  ~$ sudo iwconfig wlan0 essid "linksys" THEN ~$ sudo dhclient wlan0
how would i distinguish between the twoi signals?!?! is there another parameter i can add in order to specify which signal i wish to connect to.I've quoted the two signals below with all their info, if anyone's got any answers that'd be great!  

Thanks, Alain

> 
Cell 02 - Address: 00:18:F8:5E:8E:F7
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


> 
Cell 08 - Address: 00:06:25:76:52:ED
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Thanks for taking the time to help me out! hope you've got an answer!

---

### Post by milosz.galazka on 2007-07-31
Hello,

Try to add ap parameter to iwconfig, like
sudo iwconfig wlan0 essid "linksys"  ap 00:06:25:76:52:ED
or
sudo iwconfig wlan0 essid "linksys"  ap 00:18:F8:5E:8E:F7

---

