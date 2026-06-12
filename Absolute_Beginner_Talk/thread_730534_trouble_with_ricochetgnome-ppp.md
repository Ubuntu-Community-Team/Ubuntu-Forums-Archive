---
title: "trouble with ricochet/gnome-ppp"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by guymn999 on 2008-03-21
hello
i use ricochet modem for internet and im haveing a minor problem
to set up the modem i used a guide here twice before and had no problems,
i had to reinstall ubuntu and gnome-ppp,
i did set up all the same as before, but i cant fully connect. the window that goes through te process just sits there saying dailing 3333, even though i have internet.
this is what the connection log says...
Quote:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0
WvDial Modem<*1>: ATQ0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATM1L3DT3333
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATM1L3DT3333
WvDial Modem<*1>: CONNECT 460800
WvDial<*1>: Carrier detected. Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}!} }4}"}&} }*} } }%}&k7@[0e]}'}"}(}"}#=~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Thu Mar 20 19:22:39 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 13582
WvDial<*1>: Using interface ppp0
WvDial<*1>: local IP address 168.253.17.254
WvDial<*1>: remote IP address 192.168.1.1
WvDial<*1>: primary DNS address 168.253.8.17
WvDial<*1>: secondary DNS address 168.253.8.18
so i guess the probles lies somewhere in
"WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky."
but i dont know how to fix this cause im a noob 
srry i posted this before but i figured this would be a better place to put it

---

### Post by guymn999 on 2008-03-21
bump

---

### Post by fourscore on 2008-03-21
There is some bug in gnome-pp. Use Kppp instead. Install Kppp and K-logview from Add/Remove programs. This worked fine for me

---

