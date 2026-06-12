---
title: "Mystery Wireless Interface"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-03-28
Here is my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
	wireless-essid blahblah
	wireless-channel 1
	wireless-mode adhoc
	wireless-nick Ubuntu
	wireless-rts 2304
	wireless-frag 2304

My problem is not so much a problem but more of a curiosity. My wireless network works fine, however when running knetstats to view the network information it shows that two interfaces are active (wifi0 and ath0). This puzzled me because wifi0 is not even in the interfaces file?!?!

When browsing a webpage (committing obvious network traffic) they both show data being transmitted and recieved!

I should mention that when trying to get my network card to work, I did mess around with ndiswrapper and I think I installed it.

Hope someone can shed some light on this issue. Thanks for your time

---

### Post by Gannin on 2007-03-28
What does it show if you type "sudo iwconfig"?

---

### Post by tommy1987 on 2007-03-28
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"blahblah"  Nickname:"Ubuntu"
          Mode:Managed  Frequency:2.417 GHz  Access Point: MYMACADDRESS
          Bit Rate:11 Mb/s   Tx-Power:13 dBm   Sensitivity=0/3
          Retry:off   RTS thr=2304 B   Fragment thr=2304 B
          Encryption key:off
          Power Management:off
          Link Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

