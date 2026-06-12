---
title: "warning message in modem log about chaps and pap-secret"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2005-12-09
Hi ,
  I just installed gnome PPP as before I was connection using Networking. My connection is working OK (60k+ on a 56k  modem thats above isdn speed when checking with ZDnet modem speed page), but I get this message in the log about not being able to modify pap-secrets or chap-secrets. Can anyone explain what's going on?

Thanks 
Jock

> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S10=1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S10=1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT179
--> Waiting for carrier.
ATM1L3DT179
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
CVX Access Switch.
Access is restricted to authorized users only.
login: 
--> Looks like a login prompt.
--> Sending: pmnw22254
pmnw22254
password: 
--> Looks like a password prompt.
--> Sending: (password)
Exiting shell, and starting PPP session.
~[7f]}#@!}!}!} }<}!}$}%\}"}&} }*} } }%}&[02]-[08][7f]}'}"}(}"}1}$}%bEp~
--> PPP negotiation detected.
--> Starting pppd at Fri Dec  9 13:46:26 2005
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 8618
--> Using interface ppp0
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> local  IP address 213.48.230.45
--> pppd: TZ
--> remote IP address 213.48.230.2
--> pppd: TZ
--> primary   DNS address 193.38.113.3
--> pppd: TZ
--> secondary DNS address 194.117.157.4
--> pppd: TZ

EDIT
 Your line speed:

65.1 Kbps

8 K bytes/sec

these figures from ZDnet just now

---

