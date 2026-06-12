---
title: "Macbook 2,1 8.04 single-boot : Continuous errors from madwifi in syslog and kernlog"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by tylermoody on 2008-05-11
I'm seeing this error showing up in my logs 3 times every second: 

[timestamp][system name]kernel: [11747.073299] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.

What could be causing this? I installed madwifi the same way I did in 7.04, following the macbook wiki page.

Wifi works, but the connectio dies occasionally, more often than in 7.04. Sometimes I am unable to reconnect even though the network is still there.

Here's my iwconfig output when disconnected: 

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate: 1 Mb/s   Tx-Power: 14 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=39/70  Signal level=-55 dBm  Noise level=-94 dBm
          Rx invalid nwid: 659248  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

---

### Post by cyberdork33 on 2008-05-11
are you using network-manager? there have been reposted issues with madwifi and n-m. Try wicd.

---

