---
title: "Broadcom 4318 firmware Installed but Cell: Invalid"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-26
Hi,

Following the advice here

[https://help.ubuntu.com/community/Wi...73a6125139c9d8](https://help.ubuntu.com/community/Wi...73a6125139c9d8)

I have managed to get my Broadcom 4318 working, or at least so it would seem.

Yet, it just wouldn't connect to my wirelss network. I don't know what to do further. I've tried the following:


ovidiu@Ovidiu:/$ iwconfig
lo no wireless extensions.

eth0 IEEE 802.11b/g ESSID:"Ender" Nickname:"Broadcom 4318"
Mode:Managed Frequency=2.437 GHz Access Point: Invalid
Bit Rate=11 Mb/s Tx-Power=19 dBm
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth1 no wireless extensions.

sit0 no wireless extensions.

ovidiu@Ovidiu:/$ sudo iwconfig eth0 mode Ad-Hoc
ovidiu@Ovidiu:/$ iwlist eth0 channel
eth0 14 channels in total; available frequencies :
Channel 01 : 24.12 kHz
Channel 02 : 24.17 kHz
Channel 03 : 24.22 kHz
Channel 04 : 24.27 kHz
Channel 05 : 24.32 kHz
Channel 06 : 24.37 kHz
Channel 07 : 24.42 kHz
Channel 08 : 24.47 kHz
Channel 09 : 24.52 kHz
Channel 10 : 24.57 kHz
Channel 11 : 24.62 kHz
Channel 12 : 24.67 kHz
Channel 13 : 24.72 kHz
Channel 14 : 24.84 kHz
Current Frequency=2.437 GHz

ovidiu@Ovidiu:/$ sudo iwconfig eth0 channel 07
ovidiu@Ovidiu:/$ iwconfig
lo no wireless extensions.

eth0 IEEE 802.11b/g ESSID:"Ender" Nickname:"Broadcom 4318"
Mode:Ad-Hoc Frequency=2.442 GHz Cell: Invalid
Bit Rate=11 Mb/s Tx-Power=19 dBm
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth1 no wireless extensions.

sit0 no wireless extensions.

ovidiu@Ovidiu:/$ sudo iwconfig eth0 ap any
ovidiu@Ovidiu:/$ iwconfig
lo no wireless extensions.

eth0 IEEE 802.11b/g ESSID:"Ender" Nickname:"Broadcom 4318"
Mode:Ad-Hoc Frequency=2.442 GHz Cell: Invalid
Bit Rate=11 Mb/s Tx-Power=19 dBm
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth1 no wireless extensions.

sit0 no wireless extensions.

ovidiu@Ovidiu:/$ sudo iwconfig eth0 ap 00:14:BF:94:07:7B
ovidiu@Ovidiu:/$ iwconfig
lo no wireless extensions.

eth0 IEEE 802.11b/g ESSID:"Ender" Nickname:"Broadcom 4318"
Mode:Ad-Hoc Frequency=2.442 GHz Cell: Invalid
Bit Rate=11 Mb/s Tx-Power=19 dBm
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth1 no wireless extensions.

sit0 no wireless extensions.


but it still wouldn't work. Any ideas?

---

### Post by catlett on 2006-06-27
[http://www.ubuntuforums.org/forumdisplay.php?f=139](http://www.ubuntuforums.org/forumdisplay.php?f=139) Try posting in that section of the forum. It is wireless specific.

---

