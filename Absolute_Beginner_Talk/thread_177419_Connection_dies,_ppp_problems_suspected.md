---
title: "Connection dies, ppp problems suspected"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by earl gray on 2006-05-16
Hi again,

With your help I've managed to set up my Conexant softmodem under Ubuntu with slmodem drivers, but now I have troubles staying online.

I connect with wvdial to a Croatian ISP, T-Net. Based on my experience on connecting in Croatia on Windows (different dialtone than in US, poor quality lines) I came up with this script:

Modem = /dev/ttySL0   
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 X3 &C1 &D2  +MS=34
Init3 = ATX3
Auto DNS = yes
Carrier Check = no
ISDN = 0
Modem Type = Analog Modem
Phone =  077100000
Username = ***
Password = ***

Then I get the following:

--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 X3 &C1 &D2  +FCLASS=0
ATQ0 V1 E1 S0=0 X3 &C1 &D2  +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Modem initialized.
--> Sending: ATDT077100000
--> Waiting for carrier.
ATDT077100000
CONNECT 50667
 T-Com Internet
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
Username:
--> Looks like a login prompt.
--> Sending: ***
***
Password:
--> Looks like a password prompt.
--> Sending: (password)
ad18>
--> Hmm... a prompt.  Sending "ppp".
ppp
Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP address is 0.0.0.0. MTU is 1500 bytes
--> Looks like a welcome message.
--> Starting pppd at Tue May 16 14:58:15 2006
--> pid of pppd: 8805
--> Using interface ppp0
--> local  IP address 195.29.53.26
--> remote IP address 195.29.53.241
--> primary   DNS address 195.29.150.3
--> secondary DNS address 195.29.150.4


This gets me online without any problems, but after a variable amount of time, anywhere from a few seconds to an hour, I get one of the following:

1. The modem makes a disconnecting sound, and the connection effectively dies, even though wvdial is still running, and nothing is recorded in the var/log/messages.

2. Wvdial dies with an error code 15 (which I found out to mean 'the peer not responding to echo requests').

By the way, when I dial on Windows (I keep a dual boot on my machine) the connection may get refused a few times with an error code 732 ('the ppp negotiation is not converging') but once it gets through, the connection remains stable indefinitely.

I tried to read more about ppp to fix the problem, but it seems I'm too much of a newb (should I spell that 'n00b'?) or just too cerebrally challenged to sort it out on my own. Any help, then, would be much appreciated.

---

### Post by kencoe on 2006-05-16
[QUOTE=earl gray]
...CONNECT 50667...By the way, when I dial on Windows (I keep a dual boot on my machine) the connection may get refused a few times with an error code 732 ('the ppp negotiation is not converging') but once it gets through, the connection remains stable indefinitely....[/QUOTE]

Have you checked to see what the connection speed is for windows? If you have bad telcom in the area, you may need to drop the connection speed to 28k or 32k. I have had that problem with rural connections in the US and surrounding...

B.T.W. Either spelling works for newbie, but I wouldn't concern myself with that as you won't have to use it for long...

---

### Post by earl gray on 2006-05-16
Hey, thanks for the quick reply!

I get about 50k stable connection under windows. Under Ubuntu, the problem persists even on as low as 14.4h.

If it's a bad lines problem, have you any advice on what windows are doing to refuse unstable connections and how to make ubuntu behave like that? I hate "asking people to do my homework", but I have no idea where to start looking...

---

