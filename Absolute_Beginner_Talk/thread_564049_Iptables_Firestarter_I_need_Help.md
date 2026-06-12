---
title: "Iptables_Firestarter I need Help"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-30
Below I have my firewall listing when Firestarter is installed port 80 is turned off and I cannot get it working, no one is able to log onto my site. I have installed firestarter 3 times and each time port 80 is blocked I have it open in the program but it does not allow it through I delete firestarter and install lokkit and everything works fine firestarter will not work with or without lokkit.
if I try to change setings in lokkit with forestarter installed then it says chains allready installed.

  	 	 	 	 	 	 	 	 	 	  [SIZE=2]sudo iptables -L -v[/SIZE]
 [SIZE=2]Chain INPUT (policy DROP 0 packets, 0 bytes)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
     [SIZE=2]0     0 ACCEPT     tcp  --  any    any     home                 anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN[/SIZE]
   [SIZE=2]159 37057 ACCEPT     udp  --  any    any     home                 anywhere           [/SIZE] 
   [SIZE=2]362  641K ACCEPT     0    --  lo     any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LSI        udp  --  any    any     anywhere             anywhere            udp dpt:33434[/SIZE]
    [SIZE=2]21  2352 LSI        icmp --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere           [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8[/SIZE]
     [SIZE=2]0     0 DROP       0    --  any    any     255.255.255.255      anywhere           [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     anywhere             0.0.0.0            [/SIZE] 
    [SIZE=2]11   440 DROP       0    --  any    any     anywhere             anywhere            state INVALID[/SIZE]
     [SIZE=2]0     0 LSI        0    -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5[/SIZE]
  [SIZE=2]1305 1604K INBOUND    0    --  eth0   any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input'[/SIZE]
 

 [SIZE=2]Chain FORWARD (policy DROP 0 packets, 0 bytes)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
     [SIZE=2]0     0 LSI        udp  --  any    any     anywhere             anywhere            udp dpt:33434[/SIZE]
     [SIZE=2]0     0 LSI        icmp --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward'[/SIZE]
 

 [SIZE=2]Chain OUTPUT (policy DROP 2 packets, 274 bytes)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
     [SIZE=2]0     0 ACCEPT     tcp  --  any    any     Server               home                tcp dpt:domain[/SIZE]
   [SIZE=2]180 12689 ACCEPT     udp  --  any    any     Server               home                udp dpt:domain[/SIZE]
   [SIZE=2]362  641K ACCEPT     0    --  any    lo      anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere           [/SIZE] 
    [SIZE=2]47  3365 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8[/SIZE]
     [SIZE=2]0     0 DROP       0    --  any    any     255.255.255.255      anywhere           [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     anywhere             0.0.0.0            [/SIZE] 
     [SIZE=2]0     0 DROP       0    --  any    any     anywhere             anywhere            state INVALID[/SIZE]
   [SIZE=2]839 84638 OUTBOUND   0    --  any    eth0    anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output'[/SIZE]
 

 [SIZE=2]Chain INBOUND (1 references)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
  [SIZE=2]1251 1581K ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED[/SIZE]
     [SIZE=2]0     0 ACCEPT     0    --  any    any     192.168.10.0         anywhere           [/SIZE] 
     [SIZE=2]2    96 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtp[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:25[/SIZE]
     [SIZE=2]0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:nameserver[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:42[/SIZE]
     [SIZE=2]4   192 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:www[/SIZE]
     [SIZE=2]0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:pop3[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:pop3[/SIZE]
    [SIZE=2]48 22414 LSI        0    --  any    any     anywhere             anywhere           [/SIZE] 
 

 [SIZE=2]Chain LOG_FILTER (5 references)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
 

 [SIZE=2]Chain LSI (6 references)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
    [SIZE=2]69 24766 LOG_FILTER  0    --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]5   224 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '[/SIZE]
     [SIZE=2]5   224 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN[/SIZE]
     [SIZE=2]0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '[/SIZE]
     [SIZE=2]0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST[/SIZE]
     [SIZE=2]0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '[/SIZE]
     [SIZE=2]0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request[/SIZE]
    [SIZE=2]64 24542 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '[/SIZE]
    [SIZE=2]64 24542 DROP       0    --  any    any     anywhere             anywhere           [/SIZE] 
 

 [SIZE=2]Chain LSO (0 references)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
     [SIZE=2]0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere           [/SIZE] 
     [SIZE=2]0     0 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '[/SIZE]
     [SIZE=2]0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable[/SIZE]
 

 [SIZE=2]Chain OUTBOUND (1 references)[/SIZE]
  [SIZE=2]pkts bytes target     prot opt in     out     source               destination        [/SIZE] 
     [SIZE=2]0     0 ACCEPT     icmp --  any    any     anywhere             anywhere           [/SIZE] 
   [SIZE=2]810 79386 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED[/SIZE]
     [SIZE=2]0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED[/SIZE]
    [SIZE=2]29  5252 ACCEPT     0    --  any    any     anywhere             anywhere            [/SIZE]

---

### Post by ruibernardo on 2007-09-30
After removing a firewall you should certify yourself that you flush iptables rules in all tables (iptables -F and iptables -X). Check if it is really flushed running "iptables-save". If you don't know how to flush iptables, reboot the computer without any firewall installed. Then you can install another firewall. Don't use two of them at the same time. 

If you don't do that, the rules and/or tables left by one firewall will still be active when you install the other, or if you run both at the same time, rules and tables will be messed up.

---

### Post by larry Gaminde on 2007-09-30
That is exactly what I have done, but firestarter installs  all of the list I posted and port 80 just will not open. Do you see anything in the above listing that would stop it.

---

