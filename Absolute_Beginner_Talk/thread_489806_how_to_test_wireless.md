---
title: "how to test wireless?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-07-01
I'm running 7.04 and am trying to connect to my wireless provider. Network Manager only gives me the option of connecting to my wired network or manually configuring--there's no option for wireless, even though there used to be. I just reinstalled NM because I was worried that my fooling around with another management tool (wicd) had somehow disabled the wireless. I also checked that wlan0 roaming is enabled. I want to see if the problem is on my end or on my AP's end. Is there a term command that can tell me whether my wireless card is operating correctly?

iwconfig produces the following output:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Is the proof that I'm OK on my end buried in here?

thanks

---

### Post by diatribe on 2007-07-01
your wireless card is detected, so you will just have to enter the essid name and then any passwords you may have

---

