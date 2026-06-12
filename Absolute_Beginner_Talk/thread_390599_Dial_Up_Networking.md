---
title: "Dial Up Networking"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-03-22
Ok so I'm trying to get dial-up Internet working on my laptop (Acer Aspire 1600) for when I'm away for home.

So I ended up at [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto").

After running the scanModem tool, I could not figure out what driver I needed. So I though hey I'll take a guess.

So I tried the [AlsaModem]("https://help.ubuntu.com/community/DialupModemHowto/AlsaModem").

After following those instructions, gnome-ppp could detect my modem so I thought I must be onto a winner.

However it did not work. It complained about No Dial Tone, and Busy Lines etc. I had played around with the settings.

To see if it was even dialing because I could not hear anything, I changed the number from the ISP's to my cellphones. My cellphone starting ringing so it must be getting though.

I rang my ISP number from my land line and I got though. Hearing the computer noise that you normally get.


So could somebody help me out, I have no idea what the problem could be.

[Here]("http://www.paradise.net.nz/standard/pages/main/pdf/regdun95.pdf") is a PDF of how to setup in windows as it might give some clues.

Thanks

---

### Post by guysmiley25 on 2007-03-22
when I run:
```
sudo wvdial
```
I get this output:
```

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
OK
--> Modem initialized.
--> Sending: ATDT086727234
--> Waiting for carrier.
ATDT086727234
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT086727234
--> Waiting for carrier.
ATDT086727234
BUSY
--> The line is busy. Trying again.
--> Sending: ATDT086727234
--> Waiting for carrier.
ATDT086727234
--> Timed out while dialing.  Trying again.
--> Sending: ATDT086727234
--> Waiting for carrier.
NO CARRIER
ATDT086727234
--> No Carrier!  Trying again.
--> Sending: ATDT086727234
--> Waiting for carrier.
NO CARRIER
ATDT086727234
--> No Carrier!  Trying again.
--> Sending: ATDT086727234
--> Waiting for carrier.
NO CARRIER
ATDT086727234
--> No Carrier!  Trying again.

```

This is my /etc/wvdial.conf:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
Modem Type = Analog Modem
Phone = 086727234
; ISDN = 0
Username = my-user-name
Password = my-password
Modem = /dev/ttySL0
Baud = 460800

```

---

### Post by guysmiley25 on 2007-03-22
Now I've got it to work. It was something to do with either the phone number, or my ISP. I got it working with an other ISP.

How ever my problem now is this:
1. I have to run sudo wvdial.
2. gnome-ppp does not work.

When either I try gnome-ppp or wvdial. I get:
```
--> Cannot open /dev/modem: Device or resource busy
```

How can I fix this so I don't have to run wvdial as root.

Thanks.

---

### Post by ieee488 on 2007-03-22
Maybe try physically typing  /dev/ttySL0  into gnome-ppp instead of using  /dev/modem?

to let anyone dial out
**sudo chmod a+s /usr/bin/wvdial**

---

