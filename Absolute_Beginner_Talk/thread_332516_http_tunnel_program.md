---
title: "http tunnel program"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-06
does anyone know of a good http tunnel app for Ubuntu (dapper)?

---

### Post by steve.horsley on 2007-01-06
OpenVPN can do HTTP tunneling, provided the HTTP proxy supports the CONNECT commend.

---

### Post by manutdfan2850 on 2007-01-06
hmm ill give it a shot. im at my university so they block just about all IM programs and the like.

---

### Post by manutdfan2850 on 2007-01-29
ok i installed OpenVPN through synaptic but now I have no idea of how to configure it. Again, I am on a university network which does not allow p2p programs and i wish to tunnel evertying through http to be able to use p2p programs. 

plz help.

thanks in advance.

---

### Post by manutdfan2850 on 2007-01-30
anyone?

---

### Post by eternalsword on 2007-01-31
if your university has ports closed, they likely have a packet shaper as well, so, the chance of this working without encryption via ssh or https is slim to none.  You could look into using proxychains, though this only does tcp, not udp.  Which p2p apps anyways, most of them come with their own proxying capabilities.

---

