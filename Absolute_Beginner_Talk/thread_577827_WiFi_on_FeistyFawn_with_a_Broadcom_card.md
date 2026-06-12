---
title: "WiFi on FeistyFawn with a Broadcom card"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by weed-n-linux on 2007-10-16
hi i have a Presario c300 laptop and i don't seem to be able to connect it to my Wifi BTW my Card is a Broadcom i noticed that the output of iwconfig might be useful so there it is[HTML]fadel@presario:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]
And the output of iwlist scan:

[HTML]fadel@presario:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth1      No scan results
[/HTML]
I Downloaded my card's windows driver from Compaq's Support site and tried to install some file like bcm*****.inf but Windows Wireless Drivers keeps saying that it is already installed and Wireless Assistant finds no network even if my sister's Nokia connects to it easily.

---

### Post by Pumalite on 2007-10-16
Wireless:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

