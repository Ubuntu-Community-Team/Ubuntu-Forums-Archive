---
title: "[B]Configure Wvdial nano[/B]"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by cheezit on 2006-02-27
I want to try Wvdial but can't seem to get the information to input properly in nano.  I tried Phone = <information here> and Phone = information here: ^O "Enter" ^X.  This is what I see:


[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = [COLOR="Red"]<Target Phone Number>[/COLOR]
; Username = [COLOR="Red"]<Your Login Name>[/COLOR]
; Password = <[COLOR="Red"]Your Password>[/COLOR]

This is what I get:

randy@ubuntu:~$ !362
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
--> Configuration does not specify a valid password[/COLOR].

---

### Post by paulmilliken on 2006-02-27
I'm not sure, however, your baud rate seems too high.  Perhaps you can try with a lower baud rate?

---

### Post by stanz on 2006-02-27
[B]
; Phone = [COLOR=Red]<Target Phone Number>[/COLOR]
; Username = [COLOR=Red]<Your Login Name>[/COLOR]
; Password = <[COLOR=Red]Your Password>[/COLOR][/B] 
*If I remember right:*[B]
;Phone = [COLOR=Red]1234567[/COLOR]
;Username = [COLOR=Red]Dude[/COLOR]
;Password = [COLOR=Red]whatitis[/COLOR][/B]
==================
There's an added 'space' before & after the ' = ' sign.
Don't include or replace brackets or add quote thingy's.
=============
I Believe wvdial tells you your modem speed, when you: *$sudo wvdialconf /etc/wvdial.conf*.
It's good to write that all down, "modem ttyS?, init string, file types & locations", as you 
may need to edit other files & ALL info needs to match!
=========
There's also a kewl dialer & gnome-ppp icon/gui in there- somewhere-
if ya don't wanna use terminal all the time...and it'll dial up,
while your loggin' in!   \\:D/
Let me know if this helps..!!

---

### Post by cheezit on 2006-02-28
In the editor I used: ^H to delete <>.  Typed in my information on each line, ^O and "Enter" to write, and ^X to exit.

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
[COLOR="Red"]; Phone = *70 7182242[/COLOR]
[COLOR="Red"]; Username = randyfyock
; Password = ****
[/COLOR]

The reason I am trying to Wvdial is to see how it works compared to: System>Administration>Networking: "Highlight" modem Properties>General <phone number> OK>Activate.  I have to do this everytime I want to activate the modem and go online.  I also have to Deactivate and [COLOR="Red"]Unplug[/COLOR] the phone line from the modem or it will not shut off after I log off.

I have [COLOR="Red"]Gnome PPP[/COLOR] installed: It logs in for about 30 seconds to 1 minute before shutting down.  And I still have to unplug and plug my modem inbetween.

---

### Post by stanz on 2006-03-01
Hi cheezit,
I was hoping one of the xperts may have stopped in, to help.
It sounds kewl- your working 'nano' that way...I arrow button my way around.
> In the editor I used: ^H to delete <>.  Typed in my information on each line, ^O and "Enter" to write, and ^X to exit. ----------------
Have you 'checked', to make sure- what your changing- is being saved?
---------------
Are you sure- about your modem speed? As wvdial- reported it.
~ *Baud = 460800* ~ Far as i know, modem goes to *115200*, as wvdial will test & include in terminal feedback.
---------------
> System>Administration>Networking: "Highlight" modem Properties> General <phone number> OK>Activate. WHILE IN THERE::
In the "Modem" Tab, have you "_A_utoDetect" & Tells you for sure- modem is: *Modem = /dev/modem ?*
----------------
Wanna try removing the 'semi-colons' ?
[COLOR=Red]_**;**_ Phone = *70 7182242[/COLOR]
[COLOR=Red]_**;**_ Username = randyfyock
_**;**_ Password = ****
  ~~~~
[/COLOR]Phone
User     (backing letters- to boarder)
Pass
----------------
Right clicking the panal, & choosing '+Add To Panal', will give ya a 'shortcut', where ya want it....might be easier. 
I included mine in: Pref->Sessions->StartupPrograms.  It dials while i'm logging in. 
As for your need to unplug the line....maybe a terminal command is what cha need, but i'm not sure...i have external modem- i jus' log out->shutdown, and its good.
The 'gnome-ppp' shutting ya down- in that time, is reported in that 'how to'.
Are ya breezin' thru it?    :grin:   ....I miss 'plain as day' instructions to- LoL.
It sez..
*If you lose connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:*
**sudo gedit /etc/ppp/options**
Find '**lcp-echo-interval30**' and '**lcp-echo-failure4**'(minus my brackets).
Comment out these options by adding a '#' at the start of these lines:
" **# lcp-echo-failure4** ". 
And.. as in the 'How to"...you might need to add " **defaultroute **", as a new line, if your connect- but webpage don't load.
--------------
Printing out- all 13 pages of the howto, is worth the ink, in time saved!! I notice the modprobe stuff...but don't need it- to want to read it.

I Hope This Helps Ya Get Surfing!!!! Sorry it ain't more!

---

### Post by Cubby on 2007-12-02
Hi Stanz,

I too was getting tired of using the pulldown menu from System>Admin>Networking and decided to us wvdial, which gave me the same problem cheezit described, though my stats on the modem showed the correct Baud of 115200.

So, got rid of the semicolons and backed phone username and password up to the border and I was able to log in.  

A big **thank you** for your time and help with this!

Lisa Marie

---

