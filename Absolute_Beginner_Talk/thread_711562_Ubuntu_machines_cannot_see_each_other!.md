---
title: "Ubuntu machines cannot see each other!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Luisdesiqueira on 2008-02-29
OK.

I have two Ubuntu machines and a Windows machine.

I want to share via SMB.

I have mounted SMB file shares via GNOME gui on each machine.

They do not see each other!!

My wired desktop ubuntu can ping my gateway. 

luis@luis-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.418 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.382 ms

BUT.... my wireless laptop cannot ping the gateway.  It also cannot access my gateway config via HTTP.  HOWEVER it can access past the gateway (google.com) and is most definitely connected through my gateway.  It cannot ping my other machines at all.

All firewalls windows/gateway are disabled.  I am not aware of any ubuntu preinstalled firewalls.

Anyone have any ideas?

---

### Post by dstew on 2008-02-29
Make sure you set the domain name in the System --> --Administration --> Network --> General tab so that all the computers are on the same domain.

---

### Post by louieb on 2008-02-29
> BUT.... my wireless laptop cannot ping the gateway. It also cannot access my gateway config via HTTP. HOWEVER it can access past the gateway (google.com) and is most definitely connected through my gateway. It cannot ping my other machines at all.

Sounds like your wireless  is accessing your neighbors router. 
Might want to go to System>Network and check it out. 

BTW: Ubuntu has a firewall called iptables Theres a GUI called firestarter if you need to configure it. Personally I've haven't touched the firewall on my  PC.

---

### Post by Luisdesiqueira on 2008-03-05
> **louieb said:**
> Sounds like your wireless  is accessing your neighbors router. 
Might want to go to System>Network and check it out. 

BTW: Ubuntu has a firewall called iptables Theres a GUI called firestarter if you need to configure it. Personally I've haven't touched the firewall on my  PC.


Negative.  Am on my router for sure.

---

