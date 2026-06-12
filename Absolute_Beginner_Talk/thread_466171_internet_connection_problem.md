---
title: "internet connection problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-06-06
I have recently configured my winmodem by martian . However now when ever I try to connect to internet it produces some sort of error and connection is terminated. This is what happens in the terminal:

[I]jamil@jamil-desktop:~/martian/scripts$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
CONNECT 31200 V42bis
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Disconnecting at Wed Jun  6 21:29:22 2007
[/I]

---

### Post by phr0ze on 2007-06-06
Modems are touchy, especially when one has a setting the other doesn't accept. I'd find the list of registers for your modem and try changing some to enable more compatability... Also if this modem is working in windows see what settings the windows program is sending to the modem. They should be the same.

This is the line I am talking about.
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

---

### Post by jamil_1 on 2007-06-06
This is what modem log shows in windows:

[I]Initializing modem.
 Send: AT<cr>
 Recv: <cr><lf>OK<cr><lf>
 Interpreted response: OK
 Send: AT &F E0 &C1 &D2 V1 S0=0\V1<cr>
 Recv: <cr><lf>OK<cr><lf>
 Interpreted response: OK
 Send: ATS7=60S30=0L0M1\N3%C1&K3B0B15B2N1\J1X4<cr>
 Recv: <cr><lf>OK<cr><lf>
 Interpreted response: OK
 Dialing.
 ATDT########<cr>
 Recv: <cr><lf>CONNECT 37333 V42bis<cr><lf>
 Interpreted response: Connect
 Connection established at 37333bps. [/I]

Now what should i do with wvdial.conf ?

---

