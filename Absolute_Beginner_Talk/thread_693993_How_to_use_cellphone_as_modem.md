---
title: "How to use cellphone as modem?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by vames on 2008-02-11
i just installed ubuntu 7.10 and i like it, but the novelty is wearing off since i can't connect to the internet with my cell. i have a sony ericsson w300i so can someone help me please? i need this to work, cause if it does i'm a hundred percent convert from windows to linux

---

### Post by jrothwell97 on 2008-02-11
Do you have a Bluetooth adapter on your PC? Or are you connecting it using a USB cable?

---

### Post by Gladk on 2008-02-11
I am using Sony Ericsson K750i almost every day as GPRS modem. I am using wvdial. This is wvdial.conf for my GSM-operator:


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3= AT+CGDCONT=1,"IP","hyper.net"
Modem Type = USB Modem
; Phone = <Target Phone Number>
ISDN = 0
Password = A
New PPPD = yes
Username = B
Modem = /dev/ttyACM0
Baud = 460800
Phone = *99***8#
Stupid Mode = 1


This is for MTS Ukraine settings.

---

### Post by vames on 2008-02-11
where do i find wvdial within ubuntu? how do i use it

---

### Post by Zero Prime on 2008-02-11
It should be in the repos.  Of course I was checking the UE repos on my system.  Check the package manager and see if it is there.

---

### Post by vames on 2008-02-12
> **Gladk said:**
> I am using Sony Ericsson K750i almost every day as GPRS modem. I am using wvdial. This is wvdial.conf for my GSM-operator:


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3= AT+CGDCONT=1,"IP","hyper.net"
Modem Type = USB Modem
; Phone = <Target Phone Number>
ISDN = 0
Password = A
New PPPD = yes
Username = B
Modem = /dev/ttyACM0
Baud = 460800
Phone = *99***8#
Stupid Mode = 1


This is for MTS Ukraine settings.

How do i configure wvdial to work with my phone?

---

### Post by Jewfro_Macabbi on 2008-02-12
to install wvdial:

sudo aptitude install wvdial

to use it edit the configuration file:

sudo gedit /etc/wvdial.conf

Here's and example from my wvdial.conf file:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = #777
Password = 
Username = 

then save the file and exit. Connect by running the command:

sudo wvdial

alternately you can set up your connection using pppconfig:

sudo aptitude install pppconfig

then run:

sudo pppconfig

this launches a menu where you can enter your settings. ppp can be set to run at boot up - so that you connect automatically on start up by editing your /etc/network/interfaces file to include:

auto ppp0
iface ppp0 inet ppp
provider provider-name-here

replace provider-name-here with the provider name given during pppconfig. save the file and exit.

---

### Post by vames on 2008-02-15
> **Jewfro_Macabbi said:**
> to install wvdial:

sudo aptitude install wvdial

to use it edit the configuration file:

sudo gedit /etc/wvdial.conf

Here's and example from my wvdial.conf file:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = #777
Password = 
Username = 

then save the file and exit. Connect by running the command:

sudo wvdial

alternately you can set up your connection using pppconfig:

sudo aptitude install pppconfig

then run:

sudo pppconfig

this launches a menu where you can enter your settings. ppp can be set to run at boot up - so that you connect automatically on start up by editing your /etc/network/interfaces file to include:

auto ppp0
iface ppp0 inet ppp
provider provider-name-here

replace provider-name-here with the provider name given during pppconfig. save the file and exit.

HEY i got it to work now. apparently i didn't delete these sign...;

---

### Post by kumarkrishnan on 2008-04-18
Hi,
  Please explain me the each line of the wvdial.conf file. i.e., Say, whether
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
     is same in for the phone in any country?
Update me. Will be grateful.
With Thanks,
KK

---

### Post by kumarkrishnan on 2008-04-24
Find below the steps, how I got GPRS connection with my W810I in Ubuntu.
Note: {} - command
Step 1: Open Terminal.
Step 2: type {wvdialconfig /etc/wvdial.conf} and enter. Output typicaly like below (edited few place to hide my connection details)

Find the modem type with the line contains &#8220;/dev/ttyACM0&#8221; .


Step 3: edit wvdial.conf with vi editor or known editor as below

[Dialer Defaults]

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT = 1,"IP","Type your access point name"
Modem Type = USB Modem
ISDN = 0
Baud = 460800
Phone = Type your Dialup number (contact your service provider & looks like *99# or *99****5#)
Modem = /dev/ttyACM0
Username = [COLOR="DarkOrchid"]Type your username (Contact your service provider)[/COLOR]
Password = [COLOR="darkorchid"]Type your password (Contact your service provider)[/COLOR]
Stupid Mode = Yes (This controls dialing more than once)
New PPPD = Yes

Step 4: type {wvdial} and enter. Typically as below

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT = 1,"IP","[COLOR="YellowGreen"]xyz[/COLOR]"
AT+CGDCONT = 1,"IP","[COLOR="yellowgreen"]xyz[/COLOR]"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&[07]Y[02]$\8~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Tue Apr 22 20:42:36 2008
--> Pid of pppd: 3372
--> Using interface ppp0
--> local IP address **.*.***.***
--> remote IP address **.**.**.**
--> primary DNS address ***.***.***.** [COLOR="Magenta"](first DNS address)[/COLOR]
--> secondary DNS address ***.***.***.*** [COLOR="magenta"](Second DNS number)[/COLOR]

Step 5 : Find the DNS address and notedown it. Typically two numbers. Not local IP address and
remote IP address.

Step 6 : press ctrl + c.

Step 7 : Edit or create (in case not available) /etc/resolv.conf and add below lines.

nameserver [COLOR="Magenta"]first DNS address[/COLOR]
nameserver [COLOR="Magenta"]second DNS address[/COLOR]

Step 8 : edit /etc/network/interfaces as below


#the loopback network interface
Auto lo
Iface lo inet loopback

#The primary network interface
auto ppp0
iface ppp0 inet wvdial


Step 9 : Type {wvdial} and press enter. (Terminal must not be closed until browsing completed)

Step 10 : Open Firefox or kde web browser and browse the web.

Step 11 : Press ctrl+c to disconnect the connection.


Problem 1: Even if connection got connected and Firefox is not responding, then, add [COLOR="Blue"]replacedefaultroute[/COLOR] in /etc/ppp/options file.

---

