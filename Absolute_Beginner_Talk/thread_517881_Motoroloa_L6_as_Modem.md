---
title: "Motoroloa L6 as Modem"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by shriah on 2007-08-05
I have problem using my Motorola L6 . I tried googling and find some method to configure wvdial . The wvdial tries to connect to the phone modem but it was not able to make connection I can't guess want the problem . These are my wvdial configuration
```
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,”IP”,”airtelgprs.com”,,0,0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyACM1
Username = bluff
Password = bluff
Baud = 9600

```
 It get the following error whe n I tried Sudo wvdial from the terminal
> sudo wvdial --> WvDial: Internet dialer version 1.56 --> Cannot get information for serial port. --> Initializing modem. --> Sending: ATZ ATZ OK --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK --> Modem initialized. --> Sending: ATDT*99***1# --> Waiting for carrier. ATDT*99***1# CONNECT --> Carrier detected.  Starting PPP immediately. --> Starting pppd at Wed Aug  1 01:33:58 2007 --> Pid of pppd: 7082 --> Using interface ppp0 --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> Disconnecting at Wed Aug  1 01:34:28 2007 --> The PPP daemon has died: PPP negotiation failed (exit code = 10) --> man pppd explains pppd error codes in more detail. --> I guess that's it for now, exiting --> The PPP daemon has died. (exit code = 10)
> sudo wvdial --> WvDial: Internet dialer version 1.56 --> Cannot get information for serial port. --> Initializing modem. --> Sending: ATZ ATZ OK --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK --> Modem initialized. --> Sending: ATDT*99***1# --> Waiting for carrier. ATDT*99***1# CONNECT --> Carrier detected.  Starting PPP immediately. --> Starting pppd at Wed Aug  1 01:26:51 2007 --> Pid of pppd: 6746 --> Using interface ppp0 --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> pppd: [08][11][06][08]@ [06][08] --> Disconnecting at Wed Aug  1 01:26:53 2007 --> The PPP daemon has died: A modem hung up the phone (exit code = 16) --> man pppd explains pppd error codes in more detail. --> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
I tried checking my /var/message for the session 
>   Aug  1 01:57:00 kayal pppd[8014]: pppd 2.4.4 started by root, uid 0  
                              Aug  1 01:57:00 kayal pppd[8014]: speed 14400 not supported            
                    Aug  1 01:57:00 kayal pppd[8014]: Using interface ppp0             
                   Aug  1 01:57:00 kayal pppd[8014]: Connect: ppp0 <--> /dev/ttyACM0
                                Aug  1 01:57:00 kayal pppd[8014]: PAP authentication succeeded              
                  Aug  1 01:57:30 kayal pppd[8014]: IPCP: timeout sending Config-Requests                            
     Aug  1 01:57:30 kayal pppd[8014]: Connection terminated.          
                      Aug  1 01:57:30 kayal pppd[8014]: Exit.    
if anyone who have made it work can tell me wat I am doing wrong. I am using Airtel MobileOfiice (India) .  I am not able to use Ubuntu without a Internet connection so if u can give me any help regarding this it wuld be a great help . Thank you

---

### Post by ddrichardson on 2007-08-05
You can change the length of time it takes to timeout - check the man pages for the option (I can't remember offhand and am at work on a Windows box).

---

### Post by shriah on 2007-08-06
I guess that might work! I will try that out and post the result

---

### Post by mlissner on 2008-01-29
Hmmm...did you ever get this to work? I have an L6 as well, and with this config:```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = 17814524555
Password = password
Username = guest
Modem = /dev/ttyACM0
Baud = 9600

```

I get this error:```
sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*17814524555
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*17814524555
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT*17814524555
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*17814524555
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT*17814524555
WvDial<*1>: Waiting for carrier.
Caught signal 2:  Attempting to exit gracefully...
WvDial Modem<*1>: ATDT*17814524555
WvDial<*1>: Disconnecting at Tue Jan 29 17:53:54 2008

```

Is there any hope of getting it to work?

---

### Post by JoshuaRL on 2008-01-29
I haven't tried this, but here is a thread that might help:

[http://ubuntuforums.org/showthread.php?t=318733](http://ubuntuforums.org/showthread.php?t=318733)

---

### Post by mlissner on 2008-01-29
Hmmmmm.....that is a good thread, but it made me wonder something. I was thinking of using my phone as a DIAL-UP modem, and these settings look like they may be using the phone's data plan instead.

Is what I have in mind remotely possible? It seems like an obvious thing to want to do.

---

