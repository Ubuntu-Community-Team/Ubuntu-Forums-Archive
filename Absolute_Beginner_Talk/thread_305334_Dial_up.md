---
title: "Dial up"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by frrobert on 2006-11-23
I am traveling tomorrow so I finally am getting around to setup my laptop for dial up.  I am using smartmodem, gnome ppp, and draper drake.

It can connect but cannot access a site.

Any ideas?

Thanks

The log of gnome ppp is

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT235-6705
--> Waiting for carrier.
ATM1L3DT235-6705
CONNECT 28800
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Nov 23 06:54:04 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 7223
--> Using interface ppp0
--> local  IP address 65.43.0.56
--> remote IP address 65.43.5.73
--> primary   DNS address 68.94.156.1
--> secondary DNS address 68.94.157.1

---

### Post by rlozano on 2006-11-23
gateway?

---

### Post by frrobert on 2006-11-23
I can not change my default gateway to ppp my only option is my ethernet card.  My ethernet card is set to a static ip address if I change the ethernet card to dhcp, even if it is not connected.  It allows the ppp connection to work.

So it should work on my trip but I'm not sure what is going on?

---

