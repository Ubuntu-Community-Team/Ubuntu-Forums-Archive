---
title: "Zoom USB Modem and NO CARRIER"
date: 2006-06-10
forum: Apple PPC Users
---

### Post by tomos on 2006-06-10
I am using a G4 powerbook.  I noticed that I was no longer getting the yaboot option of L, X or C and had to hold down the option key to get dapper.  I rebooted several times and every time, the machine booted into os x.  Then when I did boot into dapper by holding down the option key, my Zoom USB modem would not connect.  I get a NO CARRIER message.  Here is the modem script (in /etc/wvdial.conf) that a kind ubuntu user passed on to me.

[Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0V1E1M0L0S0=0S38=13&C1&D2
Phone = (my dialup number)
Dial Prefix =
Dial Attempts =
Dial Command = ATM0L0DT
Ask Password = off
Password = (my password)
Username = (my username)
Auto Reconnect = off
Abort on Busy = on
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
;Minimize = off
;Dock = on

It worked fine until whatever? happened.  I ran "wvdialconf" and it changed the script slightly, but I still got NO CARRIER.  I also have successfully used this script with my Cube, but now it getS NO CARRIER.  I tried using the Zoom modem on os x.  It worked fine as a mac os x modem.  I am confused.


TIA
tomos

---

