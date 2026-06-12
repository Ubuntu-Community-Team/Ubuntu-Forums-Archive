---
title: "pppd error connect script failled"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2006-01-28
hi. plz help for the past whole week i have been trying to connect to my isp.
i hav tried gkdial,pppd,wvdial.they all failled just at the last step. first they all dial to the isp correctly , conect and give the username and password correct and then suddenly pppd ends with a exit code 8.
idon't know what to do? plz help. i checked the man for pppd it said connect script failled. what the hell is a connect script .plz help

below is pppd log file and wvdial.conf 


aquarious@ubuntu:~$ sudo wvdial --config /home/aquarious/Desktop/wvdial.conf
Password:
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX0
ATX0
OK
--> Modem initialized.
--> Sending: ATDT0951124882222
--> Waiting for carrier.
ATDT0951124882222
CONNECT
--> Carrier detected.  Waiting for prompt.
CC
***********************************************************************
                        WELCOME TO NICNET Services
                        Unauthorised Access is Prohibited
 DIALUP NO:24882222
         In case of any problem please contact TECHSUPPORT at
                 Telephone #: 2436 0088 , 24360084
                                         THANK YOU
                                           Network Administrator
************************************************************************
User Access Verification
Username:
--> Looks like a login prompt.
--> Sending: anilkumar
anilkumar
Password:
--> Looks like a password prompt.
--> Sending: (password)
Entering PPP mode.
Async interface address is unnumbered (FastEthernet0)
Your IP address is 164.100.35.170. MTU is 1500 bytes
Header compression is on.
--> Looks like a welcome message.
--> Starting pppd at Thu Jan 26 14:27:39 2006
--> pid of pppd: 7305
--> Disconnecting at Thu Jan 26 14:28:03 2006
--> The PPP daemon has died: Connect script failed (exit code = 8)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

followin are the contents of the /var/log/messages file

Jan 26 14:27:40 localhost pppd[7305]: pppd 2.4.3 started by root, uid 0
Jan 26 14:27:40 localhost chat[7314]: abort on (BUSY)
Jan 26 14:27:40 localhost chat[7314]: abort on (NO CARRIER)
Jan 26 14:27:40 localhost chat[7314]: abort on (VOICE)
Jan 26 14:27:40 localhost chat[7314]: abort on (NO DIALTONE)
Jan 26 14:27:40 localhost chat[7314]: abort on (NO DIAL TONE)
Jan 26 14:27:40 localhost chat[7314]: abort on (NO ANSWER)
Jan 26 14:27:40 localhost chat[7314]: send (ATZ^M)
Jan 26 14:27:40 localhost chat[7314]: expect (OK)
Jan 26 14:27:43 localhost chat[7314]: ~^?}#@!}!Z} }4}"}&} }*} } }%}&Al11}'}"}(}"\l~~^?}#@!}![} }4}"}&} }*} } }%}&Al11}'}
Jan 26 14:27:47 localhost chat[7314]: "}(}"}5^?~~^?}#@!}!\} }4}"}&} }*} } }%}&Al11}'}"}(}"Y^_~~^?}#@!}!]} }4}"}&} }*} } }%
Jan 26 14:27:51 localhost chat[7314]: }&Al11}'}"}(}"^P},~~^?}#@!}!^} }4}"}&} }*} } }%}&Al11}'}"}(}"Z1~~^?}#@!}!_} }4}"}&}
Jan 26 14:27:55 localhost chat[7314]:  }*} } }%}&Al11}'}"}(}"}3"~~^?}#@!}!`} }4}"}&} }*} } }%}&Al11}'}"}(}"H|~~^?}#@!}!a
Jan 26 14:27:59 localhost chat[7314]: } }4}"}&} }*} } }%}&Al11}'}"}(}"^Ao~~^?}#@!}!b} }4}"}&} }*} } }%}&Al11}'}"}(}"KR~~
Jan 26 14:28:02 localhost chat[7314]: ^?}#@!}!c} }4}"}&} }*} } }%}&Al11}'}"}(}"}"A~^M
Jan 26 14:28:02 localhost chat[7314]: NO CARRIER
Jan 26 14:28:02 localhost chat[7314]:  -- failed
Jan 26 14:28:02 localhost chat[7314]: Failed (NO CARRIER)
Jan 26 14:28:02 localhost pppd[7305]: Exit.

wvdial.conf

[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATX0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
;Init3 = 
ISDN = 0
Carrier Check = no
Abort on Busy = on
;Stupid Mode = on
Auto Reconnect = off
Modem Type = Analog Modem
Phone = 0951124882222
Username = (Here's the username )
Password = (here is my password i have not printed it)

any kind of help is appreciated

---

### Post by eriefisher on 2006-01-28
It looks like you have your speed set to 460800. I would try to set it to 115200. That seems to be the ideal connection speed for these modems.

eriefisher

---

### Post by anurag_gupta on 2006-01-30
i tried ur suggestion but it didn't worked the same error is occuring.
i there any way i can change the connect script

---

### Post by eriefisher on 2006-01-31
Try to dial from the panel: system>administration>networking>properties.

Activate ppp0 and also disable eth0 so there is no conflict.

eriefisher

---

