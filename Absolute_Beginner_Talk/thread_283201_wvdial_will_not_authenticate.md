---
title: "wvdial will not authenticate"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Maxbowd on 2006-10-23
Hi all,
I have an lt soft modem. I compiled and installed the modules ok, and i can conect to my isp through the Gnome networking menu, however, when i try to make this same conection using either wvdial or KPPP, I can't seem to authenticate the conection. KPPP with just die saying there is no secret (password) which will let it use an IP address, Wvdial will fail to authenticate after sending my password. These same login details work through the gnome menu.

here is my wvdial.conf
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 087300777
Modem = /dev/modem
Username = maxbowd
Password = mypassword
Baud = 115200

Any help would be greatly appreciated.

Cheers

---

### Post by Mark_in_Hollywood on 2006-10-23
Dial-up for some linux (disto independent) is a real nightmare. The WvDial/PPPD may have problem with their code.

Please, don't use the Gnome-PPP, just yet.

Open a termnal/console and 

sudo wvdial

it will ask for your password. Enter it. The dialer should start. If that doesn't work, get back to me here.

---

### Post by Maxbowd on 2006-10-24
here is the terminal output when i run wvdial

maxbowd@maxbowd-desktop:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT087300777
--> Waiting for carrier.
ATDT087300777
CONNECT 52000 V42bis
****************************************
***             IHUG                 ***
***  Unauthroised Access Prohibited  ***
****************************************
***         CHC-BCL-NAS1             ***
****************************************
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
Username:
--> Looks like a login prompt.
--> Sending: marama_chris
marama_chris
Password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Username:
--> Looks like a login prompt.
--> Sending: marama_chris
marama_chris
Password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Oct 24 18:56:05 2006
--> Pid of pppd: 26243
--> Using interface ppp0
--> pppd: `&#65533;[05][08]
--> pppd: `&#65533;[05][08]
--> pppd: `&#65533;[05][08]
--> pppd: `&#65533;[05][08]
--> Disconnecting at Tue Oct 24 18:56:19 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
Caught signal 2:  Attempting to exit gracefully...

---

### Post by randiroo76073 on 2006-10-24
I'm having similar prob with wvdial & kppp, will be interested in reply.  Mine is an external modem[serial,ttys0].

---

### Post by Maxbowd on 2006-10-26
I was able to get KPPP working by uncomenting the noauth option in /etc/ppp/peers/kppp-options :-D . No luck with wvdial

---

### Post by Mark_in_Hollywood on 2006-10-26
OK, sorry to be so slow in getting back to you guys.

My modem and associated software are running at 12Kilobaud. I've had to go to a public terminal to get to this forum.

You need help beyond my feeble attempts:

The Linmodems.org page is too slow here at this T1 line. Try the link below:

[http://132.68.73.235/linmodems/index.html#scanmodem](http://132.68.73.235/linmodems/index.html#scanmodem)

download and run the latest version of [COLOR="Red"]scanModem[/COLOR] tool as instructed (gunzip scanModem.gz && chmod u+x scanModem && ./scanModem). look at output of read1st.txt and modemdata.txt that will be created and follow instructions.

There will be an email address to paste the output of a scanModem file into. Cogent experts will get back to you.

---

### Post by seijuro on 2006-10-26
try uncommenting noauth in /etc/ppp/options sometimes it makes a difference and I have read in a few places that kppp will not work proper less it is done.

```

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
noauth
```

another method you can try instead of wvdial is pon/poff.
run:
```
sudo pppconfig
```
create connection fill in your info and write then
run:
```
pon <your_connection_name>
poff <your_connection_name> (to disconnect)
```
one more thing I forgot to add you can check the status pon/poff generate with plog

---

