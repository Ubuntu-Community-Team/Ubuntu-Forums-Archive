---
title: "Problem installing modem"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-17
I have a problem with my modem, it is a Trendnet TFM-560X with a dial-up connection, but I think Ubuntu doesn't detect it, I've searched for the drivers but all of them are for windows, mainly they are only a .exe file. I don't know if they can be opened in Ubuntu, or what do I have to connect to internet, Do I have to change the configuration of something? or keep on searching for drivers, or what to I have to do? :-k

---

### Post by Bachstelze on 2006-12-17
[http://www.linmodems.org](http://www.linmodems.org)

Here's anything you'll need to use winmodems on Linux. The website can be a bit confusing so if you don't know what to do, look for the scanModem tool. When you'll run it, it will generate a bunch of textfiles with info about your modem. Send the modemData.txt file to their mailing list and nice volunteers will tell you what to do.

---

### Post by PennYanPete on 2006-12-17
Hi Jorge32

That modem is an easy setup, system-admin-networking

Click properties and fill in all the info, click ok, click activate.

If you have any problems post back.

PYP

---

### Post by Jorge32 on 2006-12-17
and what if I have already filled everything, where do I have to click to connect? or do I need some specific configuration?

---

### Post by Bachstelze on 2006-12-17
First, you need to make sure your modem is detected. Try running

```
sudo wvdialconf /etc/wvdial.conf
```

Than paste the output as well as the contents of /etc/wvdial.conf if it exists.

---

### Post by PennYanPete on 2006-12-17
I thought about it after I posted, you didn't say what version you have.

---

### Post by Jorge32 on 2006-12-17
> **HymnToLife said:**
> 

```
sudo wvdialconf /etc/wvdial.conf
```



With this it detects my modem and everytything, I configured the port, now what do I need to do? I opened the terminal server client, but with that  I could not connect, coud you please tell me what to do?

---

### Post by Bachstelze on 2006-12-17
Edit the wvdial.conf file :

```
sudo nano /etc/wvdial.conf
```

Fill in your username/password as well as your ISPs phone number, save the file and run *sudo wvdial* to dial.

---

### Post by Jorge32 on 2006-12-17
thanks, that almost worked, but when I enter the sudo wvdial, it doesn't dials, it says: "modem initialized" and then "configuration does not specify a valid phone number" and the same with login name and password. The point is that I already wrote ISP's number, login name and password. Do I need to put any extra symbol or letter to dial? or do I need to change anything? It goes like this what appears:

--> WvDial: Internet dialer version 1.56
--> Initializing modem
--> Sending ATZ
ATZ
OK
--> Sending ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
-->Modem Initialized
-->Configuration does not specify a valid phone number
-->Configuration does not specify a valid login name
-->Configuration does not specify a valid password

---

### Post by Bachstelze on 2006-12-17
Please paste your /etc/wvdial.conf, there is stuff that you need to remove at the beginning of those three lines.

---

### Post by Jorge32 on 2006-12-17
this one?

[Dialer Defaults]

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = *****
ISDN = 0
; Password = *****
New PPPD = Yes
; Username = *****
Modem = /dev/ttyS0
Baud=115200

---

### Post by Bachstelze on 2006-12-17
All right, it should be :

Phone = *
Password = *
Username = *


Also, if you get a "carrier lost" message when dialing, add a line like this :

Carrier check = No

---

### Post by Jorge32 on 2006-12-17
this one?

[Dialer Defaults]

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = *****
ISDN = 0
; Password = *****
New PPPD = Yes
; Username = *****
Modem = /dev/ttyS0
Buad = 115200

---

### Post by Jorge32 on 2006-12-17
Ok thanks, I'll tray 
and excuse me for the double answer, my browser hadn't load anything:-#

---

