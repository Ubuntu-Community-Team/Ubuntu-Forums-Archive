---
title: "modem problem"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-25
Hi, I have a problem with my dial-up mode, it disconnects frequently and it auto re-connects, but the matter is that because I use dial-up every connection costs me like a call.
My modem is an external TRENDnet TFM-560k.
Here is the error:
```
--> Disconnecting at Thu Jan 25 20:30:02 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

```
can ayone help me? I am using xubuntu 6.10

---

### Post by ieee488 on 2007-01-25
Do you have the same problem when using the modem from Windows?

I'm on dial-up, and that sort of thing doesn't happen for me.
The only time I got that message was when I had the wrong username/password.

---

### Post by Michl on 2007-03-06
You need
S19=0
in the commands.  Without it, your modem
hangs-up when there are pauses in data
transmission.
Michl

---

