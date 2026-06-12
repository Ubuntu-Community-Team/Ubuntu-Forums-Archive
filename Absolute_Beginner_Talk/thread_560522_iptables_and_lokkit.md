---
title: "iptables and lokkit"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-26
This first line what does it mean is it for the first 50 inputs.
no matter what I do I cannot unlock port 80 using lokkit

Chain RH-Lokkit-0-50-INPUT (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nameserver flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:42 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
REJECT     tcp  --  anywhere             anywhere            tcp dpts:0:1023 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:nfs flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpts:0:1023 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpt:nfs reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpts:x11:6009 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:font-service flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable

---

### Post by Adramelech on 2007-09-26
Have you tried firestarter?

Theres an option to allow services, is really simple with it.

---

### Post by larry Gaminde on 2007-09-26
Yes but sometimes when I make changes in firestarter things do not change even though I have the apply now button checked. I have watched when someone I know tries to log into the web on apache2 access.log file and firestarter shows that my router is trying to connect to different ports like it's not letting 80 though, 80 does show up on the access.log but will not log in. 
I have allowed the router to access all firewalled ports in firestarter so why would it show up in the events log and not allowed

---

### Post by Adramelech on 2007-09-26
You can always try to fix things manually, that way you can be sure the problem is on iptables or somewhere else.

[iptables tutorial]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html")

---

### Post by larry Gaminde on 2007-09-26
Yea I have that tutorial and I can understand a thing. Im very new to this and Im just not sure what's what.
 I can't even get the command 
sudo iptables -t --input 
which is listed in the man iptables pages on page one

---

