---
title: "WPA network on RaLink RT2500"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Conny on 2007-01-19
Hi there!

I've been studying earlier postings on problems with wireless network connection using a RaLink RT2500 card and tried doing this

[I]Here's what i have in /etc/network/interfaces

iface ra0 inet dhcp
pre-up iwconfig ra0 essid YOUR-SSID
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPATKIP
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPATKIP="YOUR-WPA-PSK"
pre-up iwpriv ra0 set TxRate=0[/I]

On writing sudo ifup - v ra0
I get an error message after the line * iwpriv ra0 set AuthMode=WPATKIP*:
Interface doesn't accept private ioctl.... set (8BE2): Invalid argument

Any suggestions?

Thanks a lot.

---

