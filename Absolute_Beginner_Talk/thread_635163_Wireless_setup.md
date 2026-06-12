---
title: "Wireless setup"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by faustianoverdrive on 2007-12-08
Now that I finally have ubuntu installed and running fine, I need to set up my wireless. Apparently the hardware is detected, but I'm not seeing any options on the network manager. I keep looking through the helpdocs and getting lost around some point, so I'd appreciate some help. 



After finding my card in device manager, I went to the terminal and used iwconfig to bring up this:

'lo       no wireless extensions.

eth0   no wireless extensions.

wmaster0 no wireless extensions.
wlan0       IEEE 802.11g ESSID:" "
                mode: managed   Frequency: 2.4ghz  Access Point: Not-Associated
                Rety min Limit: 7  RTS thr: off    Fragment thr= 2346 B
               Link Quality: 0 signal level: 0 noise level: 0
               Rx invalid  nwid: 0 RX invalid crypt: 0 Rx invalid frag: 0
               Tx excessive retries: 0 Invalid misc: 0 missed beacon: 0


At this point, the trouble shooting guide said i'd have to enter the ESSID, but linked to something that said something like Gutsy Gibbon should not require ESSIDs to be entered manually.

---

### Post by spiderbatdad on 2007-12-08
mine looks like this:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:0A:C1:17   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-100 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1255   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:0A:C1:17   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-100 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1255   Missed beacon:0

the wireless is working. the network is unsecured.

---

### Post by faustianoverdrive on 2007-12-08
Well, how do I set the SSID manually? I know mine has a wep2 key on it, but I've got the key.

---

### Post by spiderbatdad on 2007-12-08
have you seen this post?

[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

