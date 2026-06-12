---
title: "Connect nokia via usb!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by white_eagle-mk on 2007-12-06
Can I connect to Ubuntu 7.10 via usb and how? **I have Nokia 6300...**

---

### Post by philinux on 2007-12-06
I plug in my SE k810i no problems, have you tried it, just plug it in.

---

### Post by AlanR8 on 2007-12-06
Am sitting at Heathrow Airport right now, bored, flight delayed, can't smoke...so am connected to the web via my Nokia 6300!

What do you want to do with your phone connection? If you want to use the phone as a modem, you need to modify the file /etc/wvdial.conf as follows (for the UK) 

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

Next thing, once you've connected your 6300 a message will come up on the phone's screen asking what sort of connection you want. Select Nokia Default. Once done, open a terminal screen, type 

> sudo wvdial

enter your root password and the screen will scroll

> WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Thu Dec  6 19:58:14 2007
WvDial<Notice>: Pid of pppd: 5925
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 10.94.107.141
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: primary   DNS address 10.203.65.68
WvDial<*1>: secondary DNS address 10.203.65.68

You're on the net.

---

