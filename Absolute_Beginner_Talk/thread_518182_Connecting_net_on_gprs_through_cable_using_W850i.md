---
title: "Connecting net on gprs through cable using W850i"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by tech_cheetah on 2007-08-05
I am having some problem in using net through gprs using cable connected to my W850i.
I ran following commands :

1. Configuring wvdial.conf
**#sudo wvdialconf /etc/wvdial.conf**
```
Editing `/etc/wvdial.conf'.


Scanning your serial ports for a modem.


Modem Port Scan<*1>: S0   S1   S2   S3   

WvModem<*1>: Cannot get information for serial port.

ttyACM0<*1>: ATQ0 V1 E1 -- OK

ttyACM0<*1>: ATQ0 V1 E1 Z -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyACM0<*1>: Modem Identifier: ATI -- Sony Ericsson W850

ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK

ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK

ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK

ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK

ttyACM0<*1>: Max speed is 460800; that should be safe.

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

WvModem<*1>: Cannot get information for serial port.

ttyACM1<*1>: ATQ0 V1 E1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK

ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyACM1<*1>: Modem Identifier: ATI -- Sony Ericsson W850

ttyACM1<*1>: Speed 4800: AT -- OK
ttyACM1<*1>: Speed 9600: AT -- OK

ttyACM1<*1>: Speed 19200: AT -- OK
ttyACM1<*1>: Speed 38400: AT -- OK

ttyACM1<*1>: Speed 57600: AT -- OK
ttyACM1<*1>: Speed 115200: AT -- OK

ttyACM1<*1>: Speed 230400: AT -- OK
ttyACM1<*1>: Speed 460800: AT -- OK

ttyACM1<*1>: Max speed is 460800; that should be safe.

ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK



Found an USB modem on /dev/ttyACM0.

Modem configuration written to /etc/wvdial.conf.

ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


```

Then I checked the contents of the file /etc/wvdial.conf :
```
[]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Modem Type = USB Modem

DialCommand = ATDT

New PPPD = yes

SetVolume = 0

FlowControl = Hardware(CRTSCTS

Modem = /dev/rfcomm0
Baud = 460800



[Dialer Defaults]

Modem = /dev/ttyACM0

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"

Modem Type = USB Modem
Phone = *99***1#

Username = aa

ISDN = 0

Modem Carrier Check = No
Password = abc

Baud = 460800

[Dialer GPRS]
Mode = 1

Inherits = Modem0

Password = 1

Username = 1

Phone = *99***1
```


Then I ran the following command :

**#sudo wvdial**
```
--> WvDial: Internet dialer version 1.56

--> Warning: inherited section [Modem0] does not exist in wvdial.conf

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

OK

--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com"
AT+CGDCONT=1,"IP","airtelgprs.com"

OK

--> Modem initialized.
--> Sending: ATDT*99***1#

--> Waiting for carrier.

ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&REVQA#~

--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&REVQ
N~

--> PPP negotiation detected.

--> Starting pppd at Mon Aug  6 00:27:13 2007

--> Pid of pppd: 6252

--> Using interface ppp0

--> pppd: @
--> pppd: @

--> pppd: @

--> pppd: @

--> pppd: @

--> pppd: @

--> pppd: @

--> local  IP address 117.98.46.14

--> pppd: @

--> remote IP address 10.64.64.64

--> pppd: @

--> primary   DNS address 202.56.230.5
--> pppd: @

--> secondary DNS address 202.56.240.5

--> pppd: @




```

Thats fine .. It seems to be connected to the network, but still no website opens up, and connection gets timed out.
NOTE : similar setup is working in windows

Anyone has any clue ??

---

### Post by feistyfirsttimer on 2007-08-05
Ok, when it's stopped typing that text out and seems to be "hanging", open your web browser in another window.  Wvdial isn't really "hanging", it is holding your internet connection open for you.  You can stop it with Ctrl-C.

What I do is open a console with Ctrl-Alt-F1.  I log in there and start wvdial.

Then I switch to my graphic interface with Ctrl-Alt-F7, click on Firefox, and it goes straight online.

Back to console, Ctrl-Alt-F1 when you want to disconnect the modem/phone, and press Ctrl-C.

I use a mobile phone as a modem, and it's very slow.  But it's better than no internet!

---

### Post by Pragmatist on 2007-08-05
[http://digitalife.wordpress.com/2007/07/31/using-your-mobile-phone-as-a-gprs-modem-with-ubuntu-linux-via-dku-2-usb-cable/](http://digitalife.wordpress.com/2007/07/31/using-your-mobile-phone-as-a-gprs-modem-with-ubuntu-linux-via-dku-2-usb-cable/)

---

### Post by tech_cheetah on 2007-08-05
@Pragmatist
The ppp method enables to connect to the network, but in firefox , the connection still gets timed out.

@feistyfirsttimer
I tried ur method also but still the same situation.

---

### Post by Pragmatist on 2007-08-05
> **tech_cheetah said:**
> @Pragmatist
The ppp method enables to connect to the network, but in firefox , the connection still gets timed out.

How does firefox fit in to all of this?  What exactly are you trying to do?

---

### Post by feistyfirsttimer on 2007-08-05
I looked at your /etc/wvdial.conf file and it differs from mine in one major way.  Try adding this line at the end of it:

                          Stupid Mode = 1

I had problems til I googled that somewhere.  I had timing out problems I think, but that solved it.

---

### Post by OuTcRy on 2007-08-30
i have the same problem and i wrote 
Stupid Mode = 1 and nothing happened.
My connection is hanging also.

---

