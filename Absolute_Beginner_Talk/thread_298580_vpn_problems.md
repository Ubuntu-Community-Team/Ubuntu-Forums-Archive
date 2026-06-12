---
title: "vpn problems"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-11-12
I really need to connect to my university's vpn, but vpnc is acting strange.  When I try to connect it says:
> vpnc-connect: binding to port 500: Address already in use

I've rebooted my computer thinking that some other program was using that port, but the same thing happened.  Can someone help me out with this?  It's really important for me to get connected.

---

### Post by truscotty on 2006-12-01
try this command in the terminal:

sudo vpnc-connect

and then when you are done:

sudo vpnc-disconnect

---

