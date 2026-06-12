---
title: "dialup up in edgy"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by unisol on 2007-04-07
i thought i posted a while ago but i guess i didnt. i installed edgy yesterday and all went well except that i can't dial up at all. i have a diamond supra 56k external serial modem  modem  on ttyS0.,but i cant get it to dial up. i tried minicom, wvdial pppconfig. it dials but drops the connection. i even tried gnome-ppp. it says there is no directory /dev/modem. wvdial appears to be writing to /dev/null. any help would be greatly appreciated. i triple boot with windows,debian etch and edgy. the other two operating systems have no trouble dialing up.

---

### Post by Mark_in_Hollywood on 2007-04-07
Does it die immediately or intermittently? W/O knowing this, I can't help.

---

### Post by Swab on 2007-04-07
> **unisol said:**
>  i even tried gnome-ppp. it says there is no directory /dev/modem. 

Trying creating a symbolic link:

```
ln -s /dev/ttyS0 /dev/modem
```

---

### Post by unisol on 2007-04-07
it says signing in,authenicating,and then it drops the connection.

---

### Post by Mark_in_Hollywood on 2007-04-07
I would suggest using synaptic package manager to remove wvdial, and then to reinstall it and then do your wvdialconf /etc/wvdial.conf

maybe you have to do sudo wvdialconf /etc/wvdial.conf, 

for a long time now, I get strange error message in the log file saying something about a 

;malformed line

but it never causes a problem. Meanwhile I'm hunting up the an alternative solution using dpkg to reinstall wvdial

---

### Post by Mark_in_Hollywood on 2007-04-07
I can't find the original post/thread, but other here will know. You must use dkpg to remove wvdial and then re-install it. This has to do with passwords and file permissions.

Below are links which [U]may[U] help:

[http://ubuntuforums.org/showthread.php?t=269876&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=269876&highlight=wvdial)

[http://ubuntuforums.org/showthread.php?t=231544&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=231544&highlight=wvdial) (long-ish)

[http://ubuntuforums.org/showthread.php?t=283201&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=283201&highlight=wvdial) (authentication problem)

[http://ubuntuforums.org/search.php?searchid=17611665&pp=25](http://ubuntuforums.org/search.php?searchid=17611665&pp=25) (32 posts re dial-up by me)

If this isn't helping please try ScanModem, read the pages carefully and let cogent experts know where the problem is via email to them.

---

### Post by unisol on 2007-04-08
i uninstalled wvdial, reinstalled it make the symbolic link, but wvdial continues to write to /dev/null. im lost. also when i try to edit /etc/ppp/peers, it will not let me. when i uninstalled wvdial should i have deleted the wvdial.conf files.

---

### Post by Swab on 2007-04-08
> **unisol said:**
> i uninstalled wvdial, reinstalled it make the symbolic link, but wvdial continues to write to /dev/null. im lost. also when i try to edit /etc/ppp/peers, it will not let me. when i uninstalled wvdial should i have deleted the wvdial.conf files.

```
sudo apt-get remove --purge wvdial
``` 

That should remove all config files..

---

### Post by unisol on 2007-04-08
it still wont work. in wvdial i dialup it connects says its losing the signal, then i enter the password and get an idle timeout. i cant edit /etc/ppp/peers because it says its owned by root. any other ideas? i feel like im set back 2 1/2 years.

---

### Post by Swab on 2007-04-08
> **unisol said:**
> it still wont work. in wvdial i dialup it connects says its losing the signal, then i enter the password and get an idle timeout. i cant edit /etc/ppp/peers because it says its owned by root. any other ideas? i feel like im set back 2 1/2 years.

What happens when you setup a connection with pppconfig ?

---

### Post by unisol on 2007-04-08
it dials up and then drops the connection. plog says access denied. never had this problem before. i noticed the modem monitor applet is broken it lets you set it up but won't activate. i sent ubuntu a bug report when edgy was in beta. i got an email that it was fixed. i guess not.

---

### Post by Swab on 2007-04-08
Don't know what to tell you.. it's strange you are having problems with a hardware modem.

---

### Post by unisol on 2007-04-08
all my computers in the house are wirelessly  networked, with a cable modem, the one in the garage wont pick up the router, it says cannot associate with access point.so thats why i need dialup for edgy. thanks for your quick responses. do you think maybe i should reinstall edgy? thats why i kept my dialup account.

---

### Post by Swab on 2007-04-08
If it dials and then disconnects it would tend to suggest there is simply something wrong with your settings (username, password, phone number, authentication type)

---

### Post by unisol on 2007-04-09
this is what i get when ji doa sudo wvdialconf /etc/wvdial.conf:Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 56000
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by Simon Bridge on 2007-04-11
[http://www.linuxquestions.org/questions/showthread.php?p=2705233#post2705233](http://www.linuxquestions.org/questions/showthread.php?p=2705233#post2705233)
... this thread is being discussed on linuxquestions.org as well :)

OK - so far we've got as far as configuring wvdial.conf
Notice that wvdial should no longer ne "writing" to /dev/null !

Now I'd like to see the wvdial command run and the resulting output. Without this, it is difficult to know what is actually going on.

I found these posts investigating a suggestion that dialup is broken in edgy.

---

### Post by unisol on 2007-04-11
here it is: -> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*702156874676
--> Waiting for carrier.
ATDT*702156874676
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT*702156874676
--> Waiting for carrier.
Level 3 Comm nas14.phi1 UQKT2
Username:/login:/Login:
Username:/login:/Login:
Username:/login:/Login:
Username:/login:/Login:ATDT*702156874676
Password:

---

### Post by unisol on 2007-04-11
> **unisol said:**
> here it is: -> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*702156874676
--> Waiting for carrier.
ATDT*702156874676
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT*702156874676
--> Waiting for carrier.
Level 3 Comm nas14.phi1 UQKT2
Username:/login:/Login:
Username:/login:/Login:
Username:/login:/Login:
Username:/login:/Login:ATDT*702156874676
Password:
after i enter the password i get this message: idle timeout

---

### Post by dpickwell on 2007-04-11
I'm no expert but...
It looks like maybe you ISP is asking for login information but wvdial isn't responding properly. Is it possible for you to post your wvdial.conf file for us to see. NOTE if you username and password are in it please replace them with something generic.

---

### Post by unisol on 2007-04-12
here;ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 56000
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2 S3 

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by Bushfire on 2007-04-12
> **unisol said:**
> here;ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 56000
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2 S3 

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
No, he means post the actual /etc/wvdial.conf file.

But, yes, blank out user and pass first.

---

### Post by unisol on 2007-04-12
ok:[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
stupidmode = on
Phone = *702156874676
Modem = /dev/ttyS0
Username = [email]username@msn.com
Password =******
Baud = 115200
it connects,then disconnects, and dials again.

---

### Post by X-626 on 2007-04-12
Sounds like a similar problem I was having with my modem. Try removing the line "stupidmode = on" in your /etc/wvdial.conf and see if that helps any.

---

