---
title: "firestarter and iptables"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by te.ss on 2007-04-30
Still having a troubles with the firestarter / iptables.  

After installing Utuntu 6.06 and BEFORE installing firestarter, I could connect to the internet (ADSL) to browse and get emails.  After installing firestarter, the connection was blocked unless I made it inactive(?),   My iptalbes displays that default for INPUT,FORWARD, OUTPUT are ACCEPT.  This is not good, right? 

When I reinstalled firestarter (again), and made firewall active,  my connection was blocked.  
I don't know why I could connect to the internet just after the installation of ubuntu if the default is DROP for all INPUT,FORWARD and OUTPUT.  But at this point, what should I do?
:confused: 

This is the iptables when I deactivate the firewall.
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTAB LISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTAB LISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  66.241.128.10        anywhere            tcp flags:!FIN,SYN, RST,ACK/SYN
ACCEPT     udp  --  66.241.128.10        anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec b urst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             10.0.0.255
DROP       all  --  224.0.0.0/8          anywhere
DROP       all  --  anywhere             224.0.0.0/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min b urst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info pref ix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec b urst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info pref ix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R ST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R ST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R ST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R ST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request l imit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec bu rst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec bu rst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-po rt-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTAB LISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTAB LISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.0.0.6             66.241.128.10       tcp dpt:domain
ACCEPT     udp  --  10.0.0.6             66.241.128.10       udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  224.0.0.0/8          anywhere
DROP       all  --  anywhere             224.0.0.0/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info pref ix `Unknown Output'

---

### Post by Seisen on 2007-04-30
When you run the firestarter wizard what do you put for you detected device(s)? That might be the problem.

---

### Post by te.ss on 2007-04-30
> **Seisen said:**
> When you run the firestarter wizard what do you put for you detected device(s)? That might be the problem.
Detected device: etherned (eth0) and IP address is assigned via DHCP

Being a total newbie to Utuntu/linux, I accepted what the wizard displayed.  

thanx

---

