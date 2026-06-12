---
title: "Connectin to the Internet through CDMA"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by path_finder on 2008-02-27
Can someone please tell me reason to get this error message? I am using the same passoword and 
username to connect internet from Windows platform.



bunti@bunti-desktop:~$ wvdial ptcl
WvDial<*1>: WvDial: Internet dialer version 1.56

WvModem<*1>: Cannot get information for serial port.

WvDial<*1>: Initializing modem.

WvDial<*1>: Sending: ATZ

WvDial Modem<*1>: OK

WvDial<*1>: Modem initialized.

WvDial<*1>: Sending: ATDT#777

WvDial<*1>: Waiting for carrier.

WvDial Modem<*1>: ATDT#777

WvDial Modem<*1>: CONNECT

WvDial<*1>: Carrier detected.  Starting PPP immediately.

WvDial<Notice>: Starting pppd at Wed Feb 27 20:02:35 2008

WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied

WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.

WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied

WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.

WvDial<Notice>: Pid of pppd: 5418

WvDial<*1>: Using interface ppp0

WvDial<*1>: pppd: &#65533;+

WvDial<*1>: pppd: &#65533;+

WvDial<*1>: pppd: &#65533;+

WvDial<*1>: pppd: &#65533;+

WvDial<*1>: pppd: &#65533;+

WvDial<*1>: Disconnecting at Wed Feb 27 20:02:40 2008

WvDial<*1>: The PPP daemon has died: Authentication error.

WvDial<*1>: We failed to authenticate ourselves to the peer.

WvDial<*1>: Maybe bad account or password? (exit code = 19)

WvDial<*1>: man pppd explains pppd error codes in more detail.

WvDial<Notice>: I guess that's it for now, exiting

WvDial<Notice>: The PPP daemon has died. (exit code = 19)

bunti@bunti-desktop:~$ 

bunti@bunti-desktop:~$

---

### Post by schmildo on 2008-02-28
I've not tried using a CDMA phone before, or even tried using wvdial to dial through a mobile phone, but;

What's with the strange phone number? I've only ever seen *99#, *99***1# etc.

This might sound lame, but try running wvdial as a root user:     su wvdial ptcl

I'm really surprised you managed to get a carrier detected and progress to PPP authentication, I wouldnt have thought that a CDMA phone would have a carrier signal.

Sorry I couldn't be more help than that,
 Good luck!  :)

---

