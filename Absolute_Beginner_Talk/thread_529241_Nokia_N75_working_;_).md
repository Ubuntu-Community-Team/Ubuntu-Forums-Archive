---
title: "Nokia N75 working ; )"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-08-19
I finally got my N75 Nokia working with wvdial ; )  I am a happy camper !!  Here's my wvdial.config for Cingular if anyone needs it ! 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=, ,"wap.cingular"
Modem Type = USB Modem
ISDN = 0
Modem = /dev/ttyACM0
Phone = *99***1#
Username = [email]WAP@CINGULARGPRS.COM[/email]
Password = CINGULAR1
New PPPD = yes
BAUD = 460800
Stupid Mode = 1

Hope this helps someone ; )

---

### Post by loell on 2007-08-19
is this  3G or is this GPRS connection?

---

### Post by MrKlean on 2007-08-19
It's a 3G phone...but I'm only in an Edge connection area.  If it works on Edge, it should work on 3G ; )  I get faster than dialup connection, that's all I care about here LOL!!

---

### Post by gatman3 on 2007-11-20
Just want to say thanks, it works great on my N75!  300 kbps download, 100 kbps upload.  Not too bad.  (I posted this using my new N75 dial up connection).

---

