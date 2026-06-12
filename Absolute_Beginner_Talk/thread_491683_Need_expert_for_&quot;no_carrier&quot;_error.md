---
title: "Need expert for &quot;no carrier&quot; error"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by LordxAngel on 2007-07-03
I am new to this forum and I am trying to setup my Ubuntu feisty to work properly for the 'second' time , I already installed Ubuntu the first time and it worked fine for few hours , so I thought it's time for installing the NVIDIA GPU driver , but after I installed it the xserver crashed so I had to get back online from my windows vista and look for an answer on Linux forums found some answers but none of them worked , I ended up erasing the whole partition and installed Ubuntu all over again , used the same driver I used the first time ( driver was downloaded from [www.linuxant.com](www.linuxant.com) ) for conexant hsfmodem 
and it worked fine , I rebooted my machine and something wrong happened now it doesn't make any sound when I try to connect , looked up the Gnome-ppp log file and it shows "no carrier" error and tried to connect again and again , now in some posts online they say gnome-ppp can do that and mess things up sometimes , so I tried to configure wvdial.conf and pppconfig but still nothing , this issue seems to be a common issue with Ubuntu , now I am lost and I don't know how to get online from Ubuntu no post helped me out if anyone can help with this issue I will appreciate it .

---

### Post by Bachstelze on 2007-07-03
Use wvdial.

```
sudo wvdialconf /etc/wvdial.conf
```

will generate a sample config file at /etc/wvdial.conf. Edit it and then tr to dial :

```
sudo wvdial
```

---

### Post by LordxAngel on 2007-07-03
Thanks HymnToLife for the quick reply , but i have already tried that and to be 100%  sure i just tried it again  but it's still the same thing , this is what i got when i ran wvdialconf :
angel@angel-desktop:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
ttySHSF0<*1>: ATQ0 V1 E1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 Z -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySHSF0<*1>: Modem Identifier: ATI -- 56000
ttySHSF0<*1>: Speed 4800: AT -- OK
ttySHSF0<*1>: Speed 9600: AT -- OK
ttySHSF0<*1>: Speed 19200: AT -- OK
ttySHSF0<*1>: Speed 38400: AT -- OK
ttySHSF0<*1>: Speed 57600: AT -- OK
ttySHSF0<*1>: Speed 115200: AT -- OK
ttySHSF0<*1>: Speed 230400: AT -- OK
ttySHSF0<*1>: Speed 460800: AT -- OK
ttySHSF0<*1>: Max speed is 460800; that should be safe.
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 
Modem Port Scan<*1>: SHSF6 SHSF7 

Found a modem on /dev/ttySHSF0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

This what i get when i try wvdial :

angel@angel-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT198111
--> Waiting for carrier.
ATDT198111
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT198111
--> Waiting for carrier.
ATDT198111

---

