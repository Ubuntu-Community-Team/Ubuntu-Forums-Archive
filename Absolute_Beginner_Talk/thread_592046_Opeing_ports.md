---
title: "Opeing ports"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by bump_ on 2007-10-26
Ok I googled plenty before this, but I am hoping my mistake is a dumb one that you can point out.

I am trying to open a port for torrents. I got throttled speeds with every client i tried. I looked around, got firestarter, opened up my port (55555) and the default torrent ports. Here is "sudo iptables -L"

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dslrouter            anywhere            
ACCEPT     tcp  --  dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dslrouter            anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  vahid-laptop         dslrouter           tcp dpt:domain 
ACCEPT     udp  --  vahid-laptop         dslrouter           udp dpt:domain 
ACCEPT     tcp  --  vahid-laptop         dslrouter           tcp dpt:domain 
ACCEPT     udp  --  vahid-laptop         dslrouter           udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  vahid-laptop         anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55555 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:55555 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere  
```

I am pretty sure that shows the ports as open. After opening the ports, I restarted my computer and tried azureus again. But my azureus still says firewalled and i never get green health, only yellow indicating I am getting a NAT error. Any help?

Oh yeah, I turned my modem's firewall off completely. I did this back in windows when it was refusing to forward even though it said it was.

---

### Post by thelocust on 2007-10-26
could be your ISP check them out at [dslreports.com]("http://www.dslreports.com/")

---

### Post by bump_ on 2007-10-26
Oh god, I spelled "opening" wrong in the title.

No thelocust I have verizon and I tested the speeds in windows a few minutes ago as a test. They were fine.

edit: Nevermind. After waiting a day for the damn health to turn green, I gave up and posted here. Of course, 2 minutes after I post, the problem resolves itself. Ahh well, I'm still happy :D.

---

