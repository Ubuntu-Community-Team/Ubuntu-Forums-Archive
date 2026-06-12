---
title: "DSL internet logon problem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by dbclinton on 2007-10-24
Hi,
I'm trying out the live CD version of Edubuntu 7.10 and can't connect to my DSL provider. My computer accesses the Internet through an internal network adaptor (eth1 - not eth0 which connects to my LAN) connected directly to the DSL modem (not a router).
pppoeconf seems to work properly (it successfully identifies my network card, takes my logon info and reports success), but there is no actual connectivity. I've run plog which reports that the logon was refused, as follows:

Plugin rp-pppoe.so loaded
pppd 2.4.4. started by root, uid 0
PPP session is 7930
using interface ppp0
connect: ppp0 <--> eth1
remote message: request denied
PAP authentication failed
connection terminated

Any ideas?
Thanks,
David

---

### Post by ItsMitsHere on 2007-10-24
did you cleared out 'user name' by hitting back-spaces before entering user name in pppoeconf setting? if not clear-out complet box and enter your user name and then try connecting!

---

### Post by dbclinton on 2007-10-24
Wow! I never thought of that. 
I'll give it a try.
Thanks!

---

