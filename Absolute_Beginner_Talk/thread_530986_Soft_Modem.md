---
title: "Soft Modem"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by colinpat on 2007-08-21
Hi, 

 Please is there anyone out there that knows about getting soft modems to work.  I have been playing with this for days & days.

Query modem results;  ATI: Smartlink Soft Modem;  ATI 1: Soft Modem, 2.9.11 Smart Link Ltd,  ATI 3: /dev/slamp0 modemap driver.

Have the Initialisation String: ATQ0 V1 E1 SO=0 &C1 &D2 +Fclass=0 &C0 M2 L3 &K3 S7=20.

Modem log; 
Init string
ok
ATSII=71
ok
ATSII=71
ok
ATM1L1
ok
ATX3
ok
ATD01880555 (At this point I can hear system dialing and handshake)
No Carrier  (But then it drops out)

Please, please can anyone help with what I need to do to get the connection to complete - am I missing something in the init string??.  I can connect to the net only by rebooting in windows.

Thanks

---

### Post by cek on 2007-08-22
Please post your /etc/wvdial.conf file (remove the password/username first :) )

Some modems require the following lines:

Carrier Check = no
Stupid Mode = yes

to be added to that file.

---

### Post by colinpat on 2007-08-24
Contents of wvdial.conf are

[Default Dialer]
Phone =
Username =
Password =
New PPPD = yes

I have edited and added info but still no luck.

Not sure if it means anything but when I use KPPP it detects the modem and dials, starts handshake and then drops out with no carrier message.  Have increased carrier detect time to 60 sec but it drops out before then.

When I try and use Gnome PPP as a dialer it won't detect the modem.

Really want to get online with linux and dial-up is all that is possible here in PNG.

Cheers

Colin

---

### Post by _duncan_ on 2007-08-24
can you try entering the following command into a terminal:

```
sudo touch /etc/resolv.conf
```

It will create a blank /etc/resolv.conf file if you don't have it. Sometimes wvdial and gnome-ppp don't work if this file is missing.

Then try dialing out again.

---

### Post by cek on 2007-08-24
Did you add the Carrier Check and Stupid Mode options?

---

### Post by colinpat on 2007-08-29
Have file resolv.conf and have added carrier check = no and stupid mode - yes.

system still dials and does handshake but still drops out with no carrier message.

Guess the best answer is to buy an external modem.  Also hard as only modems sold in PNG are windows only.

Would be really good to get soft modem working.

---

