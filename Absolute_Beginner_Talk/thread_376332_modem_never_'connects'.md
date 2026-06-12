---
title: "modem never 'connects'"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by koasati on 2007-03-04
Hi folks. I have what I hope is simple problem. My dialup modem dials up the ISP. I can hear the remote modem answer, but I never get a connection.
I've been reading all day, and have yet to find an answer.

I really hope someone can help with this.............. 

IBM ThinkPad A22m
Lucent winmodem
Ubuntu 6.06 LTS

---

### Post by ieee488 on 2007-03-04
How are you dialing out?

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by koasati on 2007-03-04
Thanks for responding ieee488. I've tried every method on that "DialupModemHowto" page, with not much luck.
Presently using the Modem Monitor. But as I said, it's dialing, but I never get logged-in.

---

### Post by ieee488 on 2007-03-04
I guess you have this driver installed?
[http://www-307.ibm.com/pc/support/site.wss/MIGR-4VFTT3.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-4VFTT3.html)

I always use the wvdialconf method. Run the **sudo wvdialconf /etc/wvdial.conf** in terminal window. Running that command will tell you immediately whether you're going to be able to dial out on you laptop.

---

### Post by koasati on 2007-03-04
When I run the "sudo wvdialconf /etc/wvdial.conf" I get this.....

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttyLTM0 first, /dev/modem is a link to it.
ttyLTM0<*1>: ATQ0 V1 E1 -- OK
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
Modem Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Modem Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Modem Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47

Found a modem on /dev/ttyLTM0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
jules@jules-laptop:~$


To be completely honest, I've no idea what it means. This stuff is still very confusing to me.

I'm trying to figure out how to install the driver you linked to. Have to get my brain wrapped around using these command line prompts.......

---

### Post by ieee488 on 2007-03-04
This link might be helpful for you.
[http://doc.gwos.org/index.php/PCI_Lucent_winmodem](http://doc.gwos.org/index.php/PCI_Lucent_winmodem)
It talks about a PCI modem but should be similar for you.

---

### Post by koasati on 2007-03-04
I appreciate the help ...... appears I have a couple of hours worth of downloading updates (hope I'm doing this right) 

I'll let you know how it goes.

Thanks again!

---

### Post by koasati on 2007-03-05
It's working now. Never did get that driver installed, but I did figure out what was wrong in my "wvdial.conf" thanks to that  last link you gave me. 
I have much to learn.........

Thank you so much for the help ieee488. Have a great day!

---

### Post by dougmorin on 2007-03-06
check out a problem that I am having, and see if it sounds farmilliar

[http://www.ubuntuforums.org/showthread.php?t=374942](http://www.ubuntuforums.org/showthread.php?t=374942)

---

