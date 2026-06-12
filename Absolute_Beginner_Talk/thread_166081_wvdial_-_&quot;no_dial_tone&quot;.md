---
title: "wvdial - &quot;no dial tone&quot;"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-04-25
I posted this in Networking but with no respnse. Maybe someone here can help?

Trying to use my newly enabled linmodem, I try to connect to ISP, using wvdial. Here is the output:

> t0p@lapt0p:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT08456042086
--> Waiting for carrier.
ATDT08456042086
NO DIALTONE
--> No dial tone.
--> Disconnecting at Tue Apr 25 20:11:45 2006
t0p@lapt0p:~$



Here's my wvdial.conf file:

> [Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 08456042086
Username = foobar
Password = foobar



Anyone here got a clue why I'm geting this damn "No Dialtone" error? I've listened to the line with a phone and there is normally a dial  tone. Any suggestions/solutions? Thabks.

---

### Post by Mark_in_Hollywood on 2006-04-25
Here is mine:

	[Dialer Defaults]
		Modem = /dev/ttyS14
		Baud = 115200
		Init = ATZ
		Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
		ISDN = 0
		Modem Type = Analog Modem
		Phone = xxx-2021
		Username = state-your-username
		Password = state-your-password
		

	[Dialer phone2]
		Phone = xxx-2021


	[Dialer phone3]
		Phone = xxx-2021


	[Dialer shh]
		Init3 = ATM0

	[Dialer Tone]
		Dial Command = ATDT

you can google:

wiki ubuntu dial-up and get a just OK how-to, but I've used it and got on-line with the info in it.

Good luck.

---

