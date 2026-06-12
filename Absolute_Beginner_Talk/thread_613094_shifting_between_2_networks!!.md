---
title: "shifting between 2 networks?!!?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by tettayes on 2007-11-14
ok, here is the situaion

i have one network which is non-secure connection, and the other one is WPA enabled network which i own. 

both connection works fine, but whenever i am connected to the non-secured one, i can never get back to my own WPA network unless i restart my computer.  

and even if i did restart my system, it is more likely to start off by having non-secured network (8 out of 10 i would say, but it is random)...  

therefore, if i have non-secured network when i boot, i cannot connect to my own network.

i find that i have dhcp enabled therefore my dns servers and search domain is always re-written by resolv.conf.

is there any way i can choose which network i want to connect to?? (my own network in this case)

---

### Post by tettayes on 2007-11-14
bump

---

### Post by oilchangeguy on 2007-11-14
you need wi-fi radar. it's in add/remove, or synaptic. and how did you setup your connection? you should be presented with a list of available networks when configuring the wireless connection.

---

### Post by tettayes on 2007-11-14
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0E:3B:06:EC:42
                    ESSID:"CTY18_BH4"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0F:66:A5:E3:2E
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:90:4C:7E:00:6E
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:1B:2F:4C:A3:78
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101000e0000
          Cell 05 - Address: 00:1A:70:ED:C3:CF
                    ESSID:"78787788"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:13:80:A9:FE:00
                    ESSID:"bsu_frat"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
          Cell 07 - Address: 00:16:B6:42:61:F1
                    ESSID:"nointernetforyou"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 08 - Address: 00:15:E9:EC:CF:4E
                    ESSID:"dlink"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:13:46:1D:7F:60
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 10 - Address: 00:60:B3:C9:CC:CF
                    ESSID:"CTY18_BH3"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 11 - Address: 00:1A:70:F9:E9:7C
                    ESSID:"Wayne Manor"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:11:50:40:2B:2B
                    ESSID:"123 Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 00:16:B6:C7:83:E5
                    ESSID:"MatchPoint"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 14 - Address: 00:1A:70:E3:C5:FA
                    ESSID:"Apt 206"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 00:1A:70:F9:EE:86
                    ESSID:"mcmonster"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 16 - Address: 00:19:5B:5F:A2:B7
                    ESSID:"lajidahe"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=44/70  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 17 - Address: 00:1C:10:14:DB:5A
                    ESSID:"Whatever"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: 00:1A:70:E3:C3:ED
                    ESSID:"Waynes World"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 19 - Address: 00:1A:70:50:26:33
                    ESSID:"BOY"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```

that is my result for sudo iwlist scan
i wanna connect to cell 16 which is "lajidahe"
i tend to fail getting ip address somehow, but i still can connect to it on boot...
i am trying wifi-radar, it gives me an error of saying "could not get IP address!" or says "connected, IP address: NONE".
I really have no idea how to set things up!!
someone??

---

### Post by tettayes on 2007-11-14
> **oilchangeguy said:**
> you need wi-fi radar. it's in add/remove, or synaptic. and how did you setup your connection? you should be presented with a list of available networks when configuring the wireless connection.

yes, but when i choose that network, it says acquiring IP address for like a minute, and it fails.  i know there is nothing wrong with settings since it can connect once in a while.
whenever i succeeded to connect, i had some IP addresses shown in my System>Administrator>Network>DNS tab.  however, it goes away after sometime, and never gets back until after reboot.

how could this be??

---

