---
title: "Linmodem won't dial"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by MitchCanuk on 2007-04-18
Hello,

I've just installed Dapper on an old 550Mhz machine. It has an internal modem that has the Conexant chipset. I did a lot of reading and I see it is probably the most difficult to get working but I think I have the driver installed. I still can't get it to work. I'm new to this so maybe it's the driver or the .conf file. I'm not sure.

Here is what I see when I try to dial out;
user@bunker:~$ wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT95551212
--> Waiting for carrier.
ATDT95551212

I can hear the dial tone but there is no dialing. It just sits there with the dial tone until I hear the "off hook" beep. I then CTRL-C to get the prompt back.

Any ideas wich direction I should be searching, the driver or the wvdial.conf file?

Thanks!

---

### Post by klytu on 2007-04-18
> **MitchCanuk said:**
> Hello,

I've just installed Dapper on an old 550Mhz machine. It has an internal modem that has the Conexant chipset. I did a lot of reading and I see it is probably the most difficult to get working but I think I have the driver installed. I still can't get it to work. I'm new to this so maybe it's the driver or the .conf file. I'm not sure.

Here is what I see when I try to dial out;
user@bunker:~$ wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT95551212
--> Waiting for carrier.
ATDT95551212

I can hear the dial tone but there is no dialing. It just sits there with the dial tone until I hear the "off hook" beep. I then CTRL-C to get the prompt back.

Any ideas wich direction I should be searching, the driver or the wvdial.conf file?

Thanks!

Since the modem is responding but not dialing, I would guess that your driver is OK but the generic initialization string in wvdial is not initializing the modem properly. There is [[COLOR="Red"]_a good resource here_[/COLOR]]("http://www.modemhelp.org/inits/rockwell.html") for some strings you can try for your modem.

---

### Post by MitchCanuk on 2007-05-04
Hello klytu,

Thanks for the information, much appreciated. Unfortunately I wasn't able to get the modem to dail. Some of the strings pointed to generate an error, the others take the line off-hook but still no dialing (same results as the original command string I was trying).

I may have to start looking for a serial, external modem.

Thanks again!

---

