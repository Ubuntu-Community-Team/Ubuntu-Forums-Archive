---
title: "Powerbook Pismo modem problem"
date: 2005-05-18
forum: Apple PPC Users
---

### Post by karl_kashofer on 2005-05-18
Hi all !

I am trying since several hours to get the internal modem in a Pismo to connect to my dialup account.

I found the modem is connected to /dev/ttyS0

I tried the Administration-> network -> modem tab, but it does not connect
I tried gnome-ppp but it will not connect
I tried various pon, ppp-on scripts, but they do not connect.

This is what happens:
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F\N3&D3&QX3
AT&F\N3&D3&QX3
OK
--> Modem initialized.
--> Sending: ATM1L3DT008456000194
--> Waiting for carrier.
ATM1L3DT008456000194
NO CARRIER
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Wed May 18 23:42:32 2005

I have tried all INIT strings I could find on the web, but it always just gives no carrier.
Same connection with same user/pass/number works from windoze.

I am at my wits end, I dont even know if the modem is dialling at all !
It makes no sound, does anyone know if this can be switched on ?

Any help appreciated,
cheers,
Karl

---

### Post by Ptero-4 on 2005-05-18
[QUOTE=karl_kashofer]Hi all !

I am trying since several hours to get the internal modem in a Pismo to connect to my dialup account.

I found the modem is connected to /dev/ttyS0

I tried the Administration-> network -> modem tab, but it does not connect
I tried gnome-ppp but it will not connect
I tried various pon, ppp-on scripts, but they do not connect.

This is what happens:
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F\N3&D3&QX3
AT&F\N3&D3&QX3
OK
--> Modem initialized.
--> Sending: ATM1L3DT008456000194
--> Waiting for carrier.
ATM1L3DT008456000194
NO CARRIER
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Wed May 18 23:42:32 2005

I have tried all INIT strings I could find on the web, but it always just gives no carrier.
Same connection with same user/pass/number works from windoze.

I am at my wits end, I dont even know if the modem is dialling at all !
It makes no sound, does anyone know if this can be switched on ?

Any help appreciated,
cheers,
Karl[/QUOTE]
 you need to use the pppconfig util (needs root privileges) to set up an account (use the default name "provider") after that use pon (make sure that your user account can access and use the modem device, or that it's in the dip group) to connect and poff to disconnect from the internet. Don't use the gnome modemlights applet it's broken in gnome 2.10. And as for the modem. Apple uses hardware-driven modems in every mac up to the pre-flat panel iMac, early PowerMac G4, early PowerBook G4 and iBook G3 500 MHz, the eMac and all iMac/iBooks, PowerMac/PowerBooks newer than those listed before uses softmodems.

---

### Post by karl_kashofer on 2005-05-18
Hi !

Thank you for your help.

I have just now found the problem. I used the phone cable from my telephone to connect the powerbook to the phone line. Apparently this does not work, i replaced it with a modem cable and now everything works.

Its only a two-wire cable, you would think they manage to keep that the same....

Anyway, I am now happy using gnome-ppp to dial up. Works like a charm and looks nice.

Cheers,
Karl

---

### Post by Banjaxala on 2007-05-17
I have a Powerbook G4 titanium 400mhz--so do I have a softmodem? and if I do, am I out of luck for using it with ubuntu?

I live in the boonies, so for most of the week I only have access to dialup. It'd be a shame if I had to buy OS X just to dial up on a weekday.

---

