---
title: "quick iptables question"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ubunuby on 2007-08-28
I see the following rule listed near the top of my INPUT chain for iptables

> ACCEPT     0    --  anywhere             anywhere

As I understand, the "0" means any protocol, and this rule would allow all packets to be accepted.
If this is true I don't understand how the rules beneath this one are being applied. Can anyone please give a quick explanation?

---

### Post by bogolisk on 2007-08-28
> **ubunuby said:**
> I see the following rule listed near the top of my INPUT chain for iptables



As I understand, the "0" means any protocol, and this rule would allow all packets to be accepted.
If this is true I don't understand how the rules beneath this one are being applied. Can anyone please give a quick explanation?

huh... I don't have exactly the same thing in my rules. You probably have to show the whole list b4 ppl can explain it to you.

---

### Post by ubunuby on 2007-08-28
here

> Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  (DNS server)  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  (""             "")  anywhere            
ACCEPT     0    --  anywhere             anywhere            
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
NR         0    -- !10.0.0.0/8           anywhere            
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             10.255.255.255      
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 


I used firestarter to generate the table.

LSI is the logging chain, INBOUND checks against authorized IP's and NR is the chain to block reserved LAN ip's coming from the WAN,

---

