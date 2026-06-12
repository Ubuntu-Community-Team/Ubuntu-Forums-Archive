---
title: "internet setup"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-12-23
here goes ;

i have a router set up as follows;

gateway 192.168.1.254
 dhcp is step up from 192.168.1.64 to 253 

i want another pc (my web server) to be on 192.168.1.2

so under /etc/network/interfaces  on that computer

i have put 

address 192.168.1.2
netmask 255.255.255.0
network 192.168.0.0  
broadcast 192.168.1.255
gateway 192.168.1.254

i realyl am not sure what the "network" or "bradcast" should be these were just guesses ???

when i look at the router (via this pc connected via dhcp on 192.168.1.64) it does see a Unknown user conected to ethernet port 1 on 192.168.1.2  

put the pc (web server) does not conect to internet ???

any help ?

---

### Post by wormser on 2007-12-23
> **lupgop said:**
> i realyl am not sure what the "network" or "bradcast" should be these were just guesses ???


Do you have another machine on the network.  You can run **ifconfig** on a working machine to get the correct information.

---

### Post by lupgop on 2007-12-23
got this computer  but it is running windows (conected via dhcp)
problem i thing is with the broadcast or network setting on other machine - im not sure what they should be...  guess i could copy from this computer... anyone know the dos equiv of ifconfig ?

---

### Post by wormser on 2007-12-23
I believe it is **ipconfig /all**.

---

### Post by carverj on 2007-12-23
> gateway 192.168.1.254
dhcp is step up from 192.168.1.64 to 253

i want another pc (my web server) to be on 192.168.1.2

so under /etc/network/interfaces on that computer

i have put

address 192.168.1.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.1.255
gateway 192.168.1.254

i realyl am not sure what the "network" or "bradcast" should be these were just guesses ???

when i look at the router (via this pc connected via dhcp on 192.168.1.64) it does see a Unknown user conected to ethernet port 1 on 192.168.1.2

put the pc (web server) does not conect to internet ???

try using the network 192.168.1.0

---

