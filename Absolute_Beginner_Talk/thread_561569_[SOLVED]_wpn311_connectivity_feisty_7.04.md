---
title: "[SOLVED] wpn311 connectivity feisty 7.04"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-09-27
Greetings, fellow forumites!

Thanks to those that helped me yesterday - all is well on that issue.

However, today I would like to solve the poor connectivity issue I am experiencing with my Netgear wpn311 wireless card - same card on Windows is perfect (almost). The first thing I noticed was that my signal strength seems curiously low - never more than 35-38% - and also experiences fairly consistent intermittent disconnects. I am using a compatible Netgear wpn824 router, about  20 feet away - again, no problems on the Windows box in the same room as the Linux box. Also, and I don't know if there is a causal relationship here, (but suspect there might be), I have experienced several BSODs on the windows box when trying to access shares on Ubuntu 7.04. Maybe that's a different issue altogether, but I thought I'd toss it in.

Anyway, instinct tells me that I should probably use ndiswrapper, but most threads I viewed were incomplete, or were just old enough to make me wonder about recent updates/compatibility. The hours of Googling I did did not pay off, so here I am. Thank you in advance for any help - it is greatly appreciated! Also, here is my  iwconfig:

 lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"sidewinder"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:0E:D0:CA   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/94  Signal level=-57 dBm  Noise level=-94 dBm
          Rx invalid nwid:26209  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My box is a Gateway e4600 with a p4 1.8ghz cpu, intel mobo, 1gb ram - really a very solid old workhorse.

---

