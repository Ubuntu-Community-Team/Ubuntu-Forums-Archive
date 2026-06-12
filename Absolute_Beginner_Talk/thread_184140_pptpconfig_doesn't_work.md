---
title: "pptpconfig doesn't work"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-29
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
anon warn[open_inetsock:pptp_callmgr.c:311]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:123]: Could not open control connection to 218.94.130.29
anon fatal[open_callmgr:pptp.c:402]: Call manager exited with error 256
Modem hangup
Connection terminated.
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1

Above is error log, how to fix it?

---

### Post by cmnorton on 2007-07-14
This is not a solution to your problem. I just kept fiddling, until I got it. 
I still have not been able to figure out exactly causes the signal 16 error.

At one point, my regular wireless connection was "Network not reachable", and I would get modem hung up and 

pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1

I had to deactivate/activate my wireless interface a few times, because I would occaisonally get Network not reachable. This was usually due to my impatience from attempting to start a tunnel, and then not closing it and waiting for the close to complete.

I eventually did connect. There are still a a few pptp config problems, but these do not prevent connecting and full-access inside our firewall.

Here are the settings used:

server: user name password with or without domain name.

routing is client to lan with one route inside the firewall.

dns is automatic

Enryption is Require MPPPE and refuse authentication with eap.

Miscl -- connect-delay 5 for ppd options

---

