---
title: "ifconfig up|down"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by johnlh on 2007-03-16
I can use ifconfig eth0 down to disconnect my connection.  So logicl told me ifconfig eth0 up to reconnect.  Not the case, I can reconnect through system restart.

System is running behind router (NAT) and router is assigning a static ip.  Connections 
working great, no issues, just wondering how to bring it back up without a restart.  I'm thinking I'm just missing a command.  TY ion advance. :)

---

### Post by zanglang on 2007-03-16
Try using sudo dhclient eth0 after you've brought the interface down. That should query the router for your static IP.

---

### Post by karamba_kid on 2007-03-16
I use sudo ifdown eth0 and sudo ifup eth0.

---

### Post by johnlh on 2007-03-16
Thanks guys - both of those worked :)

---

