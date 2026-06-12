---
title: "exit code = 16"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Novice _na on 2006-01-29
Hi !
I have Ubuntu 5.10(2.6.12-9)
My internet is connected for 3 seconds, afterwards leaves this mistake:

--> pppd:  ATZ
--> Disconnecting at Sat Jan 28 22:27:06 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16) 

I have win-modem Acorp 56k(conexant chipset)
I in the same way tried other modem US Robotics Sprortster voice 33.6 PnP

Mistake remained...
what is it?
As this correct?

---

### Post by bscbrit on 2006-01-29
When you say you have a connection for 3 secs, can you confirm that you have passed the log on / password stage or do you never get to being 'online' as such?  the code indicates (as the message also states) that the far-end modem has hung up on you.  Perhaps it doesn't like your log-on or you are using PAPs instead of CHAPs or vice-versa.

A bit more info please.

---

### Post by Novice _na on 2006-01-29
Connect with internet as such was not. Given were not sent and did not be taken.
I do not know what is a PAP and CHAP. I use Wvdial and Gnome-ppp.

Also tried to prescribe "stupid mode = on" 
This did not help.

My full wvdial log:
---------------------------

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&FW3+MS=V90,1,14400,28800,33600,56000
AT&FW3+MS=V90,1,14400,28800,33600,56000
OK
--> Modem initialized.
--> Sending: ATM1L1DT520211
--> Waiting for carrier.
ATM1L1DT520211
CONNECT 46667 V42B
ATS 55 AS5400
Login:
--> Carrier detected.  Waiting for prompt.
Login:
--> Looks like a login prompt.
--> Sending: guest
guest
Password: 
--> Looks like a password prompt.
--> Sending: (password)
~~~[7f]}#@!}!P} }8}"}&} }*} } }#}$@#}%}&.M:R}'}"}(}"}>A~
--> PPP negotiation detected.
--> Starting pppd at Sat Jan 28 22:27:02 2006
--> pid of pppd: 7919
--> Using interface ppp0
--> pppd:  ATZ
--> pppd:  ATZ
--> pppd:  ATZ
--> pppd:  ATZ
--> pppd:  ATZ
--> pppd:  ATZ
--> Disconnecting at Sat Jan 28 22:27:06 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
---------------------------

---

### Post by bscbrit on 2006-01-29
OK. What was in your /var/log/messages?

> 
......
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


I could be mistaken - but it appears to be trying to log you on as 'guest' which I suspect is not your correct logon and therefore any password you might have used will be irrelevant.  I do not use a dial-up and so I cannot provide any useful advice on the setting up of gnome-ppp or wvdial but please check your settings to ensure that your correct username and password are in the correct fields.

---

### Post by Novice _na on 2006-01-29
Yes, this wvdial under guest does not put in internet.
As me to be, if my login "guest" and password "guest" ?  :confused:

---

### Post by bscbrit on 2006-01-29
I am becoming confused.  :-k 

Are you trying to connect to the Internet?

Who are you connecting to?  Is it your ISP, another local computer, or something else?

Have you been given a username and a password to use for this connection?

:D  :D  :D

---

### Post by Novice _na on 2006-01-29
Presently I was connected to internet, using card of the access, which has login and password.
But me advantageously to use the service to telephone company, 
which gives such access(guest,guest) therefore that payment do together in payment for telephone. This comfortable.
Probably must be some output from given to situations? :-k

---

### Post by Novice _na on 2006-01-29
I have won !!! \\:D/ 

sudo gedit /etc/ppp/pop-secrets

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!

guest   hostname   "*"   -
master   hostname   "*"   -
support   hostname   "*"   -
stats   hostname   "*"   -

We Take away the line with guest and have fun !!!

Thank you, bscbrit !..:-D

---

### Post by bscbrit on 2006-01-29
Well done - I wasn't even aware of that file!  :D

---

