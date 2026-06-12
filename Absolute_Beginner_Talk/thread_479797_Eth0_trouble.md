---
title: "Eth0 trouble"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-06-20
I used the how to forum to get my internet up running on my broadcom card. I can't get it to become recognized as Eth0, so thus when I reboot, I have to restart the process to get my internet up and running... When I run iwconfig it shows:

lo        no wireless extensions.

eth0      no wireless extensions.

sudo      IEEE 802.11g  ESSID:"WEST7572"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:5C:0B:E3   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by schwascore on 2007-06-20
wireless cards are by named wlan0 by default in Ubuntu, unless the guide you followed had you do something odd.

could you post a link as to which guide you followed?

Also, which broadcomm card do you have and what kind of computer are you working on?

---

