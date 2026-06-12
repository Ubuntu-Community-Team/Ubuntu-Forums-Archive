---
title: "WvDial"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by cheezit on 2006-03-06
In the editor I used: ^H to delete <>. Typed in my information on each line, ^O and "Enter" to write, and ^X to exit.

randy@ubuntu:~$ !359
sudo nano /etc/wvdial.conf
Password:
randy@ubuntu:~$ !364
sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
[COLOR="Red"]--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.[/COLOR]
randy@ubuntu:~$

[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = *[COLOR="Red"]70 7182242[/COLOR]
; Username = [COLOR="Red"]randyfyock[/COLOR]
; Password = [COLOR="Red"]****[/COLOR]


The reason I am trying to Wvdial is to see how it works compared to: System>Administration>Networking: "Highlight" modem Properties>General <phone number> OK>Activate. I have to do this everytime I want to activate the modem and go online. I also have to Deactivate and [COLOR="Red"]Unplug[/COLOR] the phone line from the modem or it will not shut off after I log off.

I have [COLOR="Red"]Gnome PPP[/COLOR] installed: It logs in for about 30 seconds to 1 minute before shutting down. And I still have to unplug and plug my modem inbetween. 

Note: The Wiki modem Howto describes  a configure for Wvdial with a 30 second plus shut down.

---

