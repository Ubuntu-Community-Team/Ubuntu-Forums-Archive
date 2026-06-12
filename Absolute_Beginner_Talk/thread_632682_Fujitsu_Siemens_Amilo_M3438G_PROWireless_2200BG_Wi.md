---
title: "Fujitsu Siemens Amilo M3438G PRO/Wireless 2200BG Wireless not working"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Shunt on 2007-12-05
Sorry about the long title to the post, but... hopefully I get help, and it'll help others...

Anyway:

I have a Fujitsu-Siemens Amilo M3438G laptop, XP / Ubuntu dual boot, and I can't get the wireless network to work.. the same network that works with no problems on my XP installation.. 

My wireless router is an Siemens SE505, and I've tried all kinds of settings on it, and my XP-machine mirrored the settings without any problems...
It seems like my Ubuntu (7.10) finds my wireless card, which finds my router, and there it stops... I've read up a bit on the forum, but... no luck for me.

So:

```
lspci | grep -i network:
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

```
sudo lsmod | grep ipw2200
ipw2200               149320  0 
ieee80211              35656  1 ipw2200
```

```
iwlist scanning

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Scan completed :
          Cell 01 - Address: 00:01:E3:46:F5:D7
                    ESSID:"RylosNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=73/100  Signal level=-55 dBm  
                    Extra: Last beacon: 212ms ago
          Cell 02 - Address: 00:02:2D:BE:D7:AA
                    ESSID:"WaveLAN Network"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 112ms ago
          Cell 03 - Address: 00:0F:B5:EC:33:1A
                    ESSID:"FETERN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 1232ms ago
          Cell 04 - Address: 00:1B:2F:54:BF:6A
                    ESSID:"asmara"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6644ms ago
          Cell 05 - Address: 00:14:BF:B0:ED:17
                    ESSID:"wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=18/100  Signal level=-87 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5576ms ago

```

(I'm RylosNetwork, the rest are neighbors.... wlan for everyone...)

```
iwconfig:

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

```

After setting Wireless Security, Key, Auth... (by selecting my ID from the list above (wlist scanning)).

```
iwconfig:
eth1      IEEE 802.11g  ESSID:"RylosNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:01:E3:46:F5:D7   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-59 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
```

After about 20-30 secs, I get the "Wireless Network Key Requiered" again, and iwconfig goes back to:

```
iwconfig:
eth1      unassociated  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
```

I can try to log back to the network, but the network icon is stuck at 0% staples, and 0% connection.

I've tried with ASCII/HEX 64/128 bits, the mac-address is correct (for the router)....

---

### Post by Shunt on 2007-12-06
Nevermind, I got it working by manually setting up eth1 with iwconfig, forcing the router to give this computer a static ip based on it's MAC...

---

