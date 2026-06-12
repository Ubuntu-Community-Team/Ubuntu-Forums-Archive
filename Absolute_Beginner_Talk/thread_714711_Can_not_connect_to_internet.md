---
title: "Can not connect to internet"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2008-03-04
I have a winmodem. I have installed martian. yet i m unable to connect to internet. 
contents of wvdial.config are 

[Dialer Defaults]
Modem = /dev/ttySM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Carrier Check = No

 Phone = <Target Phone Number>
 Username = <Your Login Name>
 Password = <Your Password>



**[SIZE="6"]While the error I get is[/SIZE]**

jamil@jamil-desktop:/etc$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT13177777
--> Waiting for carrier.
ATDT13177777
CONNECT 31200 V42bis
--> Carrier detected.  Waiting for prompt.
NO CARRIER
--> Disconnecting at Wed Mar  5 02:35:04 2008

---

### Post by dstew on 2008-03-04
Try adding **Stupid Mode = yes** to the wvdial.conf file. That sometimes works in situations like this, when the carrier drops after the connection has been made.

---

