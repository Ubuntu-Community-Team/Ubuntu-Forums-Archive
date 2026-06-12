---
title: "Wireless network scan result?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Saul Zaddik on 2007-03-25
Hi,

Can anyone tell me what the following things mean? They are part of a scan of available wireless networks. The complete scan can be found below the three things I want to know about.

Extra:bcn_int=100
Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
Extra:ath_ie=dd0900037f01010008ff7f


saul@Mnemosyne:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:12:17:A2:AF:F8
                    ESSID:"linksys-g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/94  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010008ff7f
          Cell 02 - Address: 00:18:39:76:1C:12
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:B3:33:CC:D9
                    ESSID:"ACTIONTEC"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 04 - Address: 00:17:3F:80:66:08
                    ESSID:"RYAN.T"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:16:B6:5C:30:7E
                    ESSID:"ms-wap-1"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
Thank you, to anyone that can help my quest for knowledge!

---

