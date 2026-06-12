---
title: "ppp on modem or cpu?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-26
I have a lan thats connected to a broadband dsl service behind a firewalled router should my ppp be on the modem or on the cpu.

---

### Post by nitro_n2o on 2007-08-26
ok ppp is point-to-point protocol.. 
what is your question?

---

### Post by southernman on 2007-08-26
My modem is setup for PPPoE connection type. But the modem is bridged so that the router functions.

internet > modem > router > desktops and server

---

### Post by swoll1980 on 2007-08-26
I got the problem now. It's IP tables. Any idea how to permanently diable it

---

### Post by Austin_KW on 2007-08-26
You want to set up ppp on the modem so that the router can share this one connection with all the PCs.

It may also be possible to setup ppp on the WAN side of the router but probably simplest to set up on the modem

What do you mean that the modem is bridged? Do you mean that you have connected it to a LAN port on the router rather than the WAN port? Do you know what layer 2 bridging means?

---

