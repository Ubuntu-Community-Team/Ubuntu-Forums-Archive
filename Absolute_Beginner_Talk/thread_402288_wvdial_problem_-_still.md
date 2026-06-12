---
title: "wvdial problem - still"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by cfpole on 2007-04-05
I tried loading 6.10 - wouldn't work.  Went back to 5.10.  I had wvdial working at one time, but can't get it to work again.  I have it loaded on a Compaq Armada 7800.  Everything else seems to work well, but can't get on line.
Here is what happens when I enter wvdial:

chuck@chuck:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
chuck@chuck:~$

Then I configured wvdial.conf a couple of times.
This is what it looks like:

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 2604123
Username = [email]ckola@ohiohills.com[/email]
Password = esor629

What am I doing wrong?

Thanks for any help,
Chuck

---

### Post by Bachstelze on 2007-04-05
Are you sure you didn't make mistakes copying your wvdial.conf ?

---

### Post by cfpole on 2007-04-06
I have done it several times using:  sano nano /etc/wvdial.conf

Am I doing something wrong?

Chuck

---

