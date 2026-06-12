---
title: "Need help with ppp- pap/chap files permissions"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2007-04-15
Running Ubuntu 6.06 Dapper, just added my wife as a user on my puter but can't get her account online using gppp.  Keep getting error msg as follows, no matter what I set file permissions at, even setting them at "rwxrwxrwx".

--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT18177259412
--> Waiting for carrier.
ATM0L0DT18177259412
CONNECT 42666 V44
--> Carrier detected.  Waiting for prompt.
GlobalPOPS
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: my name
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 72.251.11.52
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Sun Apr 15 09:13:16 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8220
--> Disconnecting at Sun Apr 15 09:13:16 2007
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

Can someone help me out of this quandry please?

---

### Post by speeves on 2007-04-15
Hi,

Do the instructions on this page help?
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

Let me know.

thanks,

---

### Post by randiroo76073 on 2007-04-16
Thanks for reply speeves, have already passed that point, I can establish a viable connection when logging in as myself, but when I login as my wife I get the above message and ppp fails to establish a viable connection.

---

### Post by randiroo76073 on 2007-04-17
My hair is starting to get thin from pulling it out, have not found the problem yet, it should WORK, but it doesn't.  File permissions set back to:  Owner= root, group= admin, rwxrwx. Both of us belong to admin, dip, dialout.  What in the hell am I missing???

---

### Post by Lyneve on 2007-04-30
:roll: Randy, please read your pm's !!
Eve mpc

---

### Post by mperrin on 2007-05-09
I had the same problem using wvdial on 6.10. Changing the pap-secrets ownership to root.dialout and permissions to 660 didn't help. I can connect as the user if I change wvdial permissions so it runs with root privilege (sudo chmod +s /usr/bin/wvdial). That is an ugly fix but it's the best I've come up with so far.

---

