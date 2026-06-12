---
title: "Connecting to internet through CDMA"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by path_finder on 2008-02-23
Im a new for Gusty Gibbon, but I have used Feisty. Earlier I connected by typing "wvdial ptcl" after 
configuring wvdial.conf file. but now I get this error message. Is this cause by a bug in Gusty Gibbon?
(please dont consider about the format of this text)

bunti@bunti-desktop:~$ sudo wvdial ptcl
WvDial
<*1>: WvDial: Internet dialer version 1.56
WvModem
<*1>: Cannot get information for serial port.
WvDial
<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem
<*1>: ATZ
WvDial Modem
<*1>: OK
WvDial
<*1>: Modem initialized.
WvDial
<*1>: Sending: ATDT#777
WvDial
<*1>: Waiting for carrier.
WvDial Modem
<*1>: ATDT#777
WvDial Modem
<*1>: CONNECT
WvDial
<*1>: Carrier detected.  Starting PPP immediately.
WvDial
<Notice>: Starting pppd at Thu Feb 21 22:51:31 2008
WvDial
<Notice>: Pid of pppd: 5815
WvDial
<*1>: Using interface ppp0
WvDial
<*1>: pppd: H+
WvDial
<*1>: pppd: H+
WvDial
<*1>: pppd: H+
WvDial
<*1>: pppd: H+
WvDial
<*1>: pppd: H+
WvDial
<*1>: Disconnecting at Thu Feb 21 22:51:45 2008
WvDial
<*1>: The PPP daemon has died: Authentication error.
WvDial
<*1>: We failed to authenticate ourselves to the peer.
WvDial
<*1>: Maybe bad account or password? (exit code = 19)
WvDial
<*1>: man pppd explains pppd error codes in more detail.
WvDial
<Notice>: I guess that's it for now, exiting
WvDial
<Notice>: The PPP daemon has died. (exit code = 19)
bunti@bunti-desktop:~$

---

### Post by bazzawill on 2008-02-24
This looks to me like a problem with the username/password in the wvdial.conf file

---

### Post by spiderbatdad on 2008-02-24
Indeed...check your /etc/wvdial.conf file, also remove any semicolons at the beginning of the lines you don't want commented out.

---

### Post by path_finder on 2008-03-01
No that is not the problelm. I checked it and I use same username and password to connect internett 
in windows platform also.

---

### Post by spiderbatdad on 2008-03-01
That output in your first post looks totally different from what I remember being there. Seems like originally it said no dial tone after after waiting for carrier, and the call terminted...oh well. Looks like now options in your /etc/ppp/options are not configured correctly. Maybe add ```
lock
noauth
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
```

Sorry can't be of more help. Perhaps try a frontend like gnome-ppp or kppp.

---

