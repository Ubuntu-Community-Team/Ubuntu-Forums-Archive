---
title: "need help setting up modem !!"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-12
Hello,

I am real new to forums [perhaps fora!] and even newer to Linux. I have installed a XP/ubundu dual boot that is working great. I cannot though get my modem to work. It dials but does not contact the ISP [it is dialup].

I have read and done everything I can do at "dailupmodemhowto". Run scanmodem (ageredsp modem), installed the packages suggested (linux-headers) but to no avail.

Is there a kind soul out there who can help. I have to reboot to XP to use the internet!


tchoklat!

---

### Post by towsonu2003 on 2006-10-12
try dialing with vwdial (instructions at the dialuphowto page). it gives more output, so maybe we can find out what's goin' on... dont forget to copy paste the output for others to see :)

---

### Post by tchoklat on 2006-10-12
Hello,

I tried to run wvtest, this is the response. I do not know the commands or how to run the application wvdial.

Tchoklat

tyLTM0<*1>: ATQ0 V1 E1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 Z -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyLTM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.31
ttyLTM0<*1>: Speed 4800: AT -- OK
ttyLTM0<*1>: Speed 9600: AT -- OK
ttyLTM0<*1>: Speed 19200: AT -- OK
ttyLTM0<*1>: Speed 38400: AT -- OK
ttyLTM0<*1>: Speed 57600: AT -- OK
ttyLTM0<*1>: Speed 115200: AT -- OK
ttyLTM0<*1>: Max speed is 115200; that should be safe.
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Modem Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Modem Port Scan<*1>: S42  S43  S44  S45  S46  S47

Found a modem on /dev/ttyLTM0, using link /dev/modem in config.
wvtest<Warn>: Can't open 'wvtest' for reading: No such file or directory
wvtest<Warn>: ...starting with blank configuration.
Modem configuration written to wvtest.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by towsonu2003 on 2006-10-12
here are the instructions for wvdial:
[https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb)

the modem at ttyLTM0 seems to be working ok. try connecting with wvdial and check out what error it spits... don't forget to try out the examples given in the link above in your wvdial.conf file...

---

### Post by tchoklat on 2006-10-12
Great, I will log off, reboot, boot up linux and see what I can find, BRB


Tchoklat and thanks !

---

### Post by tchoklat on 2006-10-12
[FONT="Comic Sans MS"]YO!

Thanks dude. What you told me has fixed my issue. I am now on line the ubuntu way

:D 
Tchoklat[/FONT]

---

### Post by towsonu2003 on 2006-10-12
great news :)

---

