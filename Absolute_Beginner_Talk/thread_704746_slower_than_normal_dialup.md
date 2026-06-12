---
title: "slower than normal dialup"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by johnwen on 2008-02-22
I finally hooked up to the internet for the first time using Linux......YAY!!!!!!!!!

However, my transfer of info from web sites is extremely slow.  I have included the info from wvdial at the terminal.  I normally connect at 28.8 ( still a few of us left around, lol ) and am using 7.04 fiesty fawn.

I probably didn't set up the connection parameters correctly to cause this but don't know.  I'm thankful for being able to connect and don't want to create more problems than I have at the moment.

Can you tell from the following dialogue if I can make changes to speed up the transfer of info across the web?  I can't connect much faster, just want to speed the downloads and uploads.

The 2 warnings about pap and chap caught my attention and am thinking it is a problem in this area.

Thanks,
John





john@localhost:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT5799738
--> Waiting for carrier.
ATDT5799738
CONNECT 26400 V42bis
CCCCZ
+---------------------------------------------------------+
| Owner: Home Telephone Company, INC.                     |
| Name: SCMCNR-R12                                        |
| Type: Cisco AS5400                                      |
|                                                         |
| WARNING!!!                                              |
|                                                         |
| This systems is restricted to use by employees of       |
| Home Telephone only.  Any unauthorized access           |
| or use of this system will by punished to full extent   |
| under the law.  Use of this system is monitored.  By    |
| using this system, you are automatically consenting to  |
| such monitoring.  Should this monitoring reveal criminal|
| activities, you will be reported to the appropriate     |
| authorities.  If you have arrived at this message in    |
| error, please log out now!                              |
+--
--> Carrier detected.  Waiting for prompt.
-------------------------------------------------------+
SCMCNR-R12 line 5/30 
User Access Verification
Username:
--> Looks like a login prompt.
--> Sending: [email]johnwen@charleston.net[/email]
[email]johnwen@charleston.net[/email]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Entering PPP mode.
Async interface address is unnumbered (Loopback2)
Your IP address is 0.0.0.0. MTU is 1500 bytes
--> Looks like a welcome message.
--> Starting pppd at Sat Mar 22 18:51:41 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 19492
--> Using interface ppp0
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> local  IP address 64.20.21.36
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> remote IP address 64.20.20.1
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> primary   DNS address 206.74.254.2
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]
--> secondary DNS address 204.116.57.2
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]

---

### Post by LowSky on 2008-02-22
CONNECT 26400 

tht right there says youre connecting at 26.4kbps

you nearly maxed out

i didnt think anyone had a modem slower than 56k

Makes me remeber my first internet connection at 2.4k damn was that slow and useless

---

### Post by mgranet on 2008-02-22
I've got a 56k, and I'm lucky to connect at 24k, avg download speeds of 3k.

Same as it was with my old 28.8 back in the mid 90's, :(

---

