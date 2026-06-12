---
title: "wvdial problems"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by tollbooth on 2006-06-12
I have my driver installed, wvdial sees it, but I can't dial out. 
heres the error I get, I'm not sure what I'm doing wrong.

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

And yes I did put in the phone number and so forth, and I still get this.

---

### Post by loell on 2006-06-12
are you sure the missing pieces are in /etc/wvdial.conf  ?

---

### Post by tollbooth on 2006-06-12
I'm pretty sure it is, I did install the driver and everything checks out. But I'm not sure whats wrong. Could the reason why its not working is I tryied to get the free conexant driver thing to work but I never did so I downloaded the free limited 14.4k driver. And I may of not uninstalled the other stuff right.


Edit:I should also mention I'm on Breezy Bager 5.10.

---

### Post by brentroos on 2006-06-12
.

---

### Post by loell on 2006-06-12
[QUOTE=brentroos]Are you using a Winmodem or a hardware modem? Winmodems are not easily compatible with Open Linux Distros  like Ubuntu.

A hardware modem, such as an external *_serial_ *modem will for sure work, and can be purchased at a very inexpensive price  on EBay.

Lastly, I would suggest using Gnome-PPP for dial-up. Also, the net-speed  panel applet is nice too, to show the network connection throughput.```
sudo apt-get install gnome-ppp
```and```
sudo apt-get install netspeed
``` Then add netspeed to the panel.
:razz:[/QUOTE]

[-X    
how can he install those things via apt?
if he can not dial to have an internet connection? :rolleyes: 

not unless he's got another connection..

i believe wvdial can have a differnt config by using wvdial -conf "filename.conf"

---

### Post by tollbooth on 2006-06-12
[QUOTE=loell][-X    
how can he install those things via apt?
if he can not dial to have an internet connection? :rolleyes: 

not unless he's got another connection..

i believe wvdial can have a differnt config by using wvdial -conf "filename.conf"[/QUOTE]

The modem I have is the conxant HCF 56k modem, and I downloaded the free driver from linuxant. And I did try to do the one driver that has no limitations, with the pciid changer thing, but I dident get that to work.

---

### Post by croak77 on 2006-06-12
You got something like this in /etc/wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttyS1
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
Phone = 555-1212
Username = my_login_name
Password = my_login_password

---

### Post by loell on 2006-06-12
have you tried dialing via root user?

sudo wvdial

and see if there is any change...

---

### Post by tollbooth on 2006-06-13
[QUOTE=loell]have you tried dialing via root user?

sudo wvdial

and see if there is any change...[/QUOTE]

no I've havent tried with the root user, just thru the normal terminal, and I'll try that.

---

### Post by tollbooth on 2006-06-13
I tried it again under root and I still got the same thing.

---

### Post by loell on 2006-06-13
try to look again in your /etc/wvdial.conf

I think you already know this, well if not, try

sudo nano  /etc/wvdial.conf


and see if the  phone to be dial is correct or if it has retained your previous configuration

also your username and password try to check it..

we could also try pppconfig if wvdial fails

---

### Post by tollbooth on 2006-06-14
wvdial seems not to be working, and with ppponconfig I'm not sure if I'm starting it right or not.

---

### Post by loell on 2006-06-14
with pppconfig's main menu you are asked to create connection etc..
there is a part there to autodetect your modem, just fill it up and save those configurations..

after that, you can use "pon" and "poff" to dial and to hang-up respectively..

---

### Post by tollbooth on 2006-06-14
ok I'll try that and see what happens, and thanks for your help so far.

---

### Post by tollbooth on 2006-06-14
I have very good news, its working, I did the pppconfig and its working right now. Now one thing though, since its a conxant HCF modem I had to download the free 14.4kpbs driver so its really slow right now. And thanks for the help.:D

---

### Post by brentroos on 2006-06-14
*

---

