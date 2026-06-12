---
title: "Iplist/ipblock And Nat"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by ekimregnirps on 2007-12-01
I use IPBLOCK/IPLIST on a ubuntu box set up as a nat router for network client. I use shorewall to configure iptables, and ip_forwarding. The problem, iplist only blocks ips from the server box, not from the clients in the network.
 - the NIC that clients use to access the router/internet is eth1
 - the NIC that that access the outside is eth0
 - (eth9 is a special NIC that is actually a xen DomU, nevermind it)
 - (eth2 is a another NAT NIC that is unused as of now)

I think the problem is that ipblock creates 4 chains ( input_queue/input_match output_queue/output_match ) these are in the INPUT/OUTPUT chains but not on the forward. 

-PS. the shorewall is setup to allow everything to ease troubleshooting

HERE is the ouput from iptables.

```
root@watson:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
input_match  0    --  anywhere             anywhere            MARK match 0xffff 
input_queue  0    --  anywhere             anywhere            state NEW MARK match !0xfffe 
ACCEPT     0    --  anywhere             anywhere            
eth0_in    0    --  anywhere             anywhere            
eth9_in    0    --  anywhere             anywhere            
detect_in  0    --  anywhere             anywhere            
eth2_in    0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
eth0_fwd   0    --  anywhere             anywhere            
eth9_fwd   0    --  anywhere             anywhere            
detect_fwd  0    --  anywhere             anywhere            
eth2_fwd   0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
input_match  0    --  anywhere             anywhere            
ACCEPT     0    --  apache               anywhere            PHYSDEV match --physdev-in eth9 
ACCEPT     udp  --  anywhere             anywhere            PHYSDEV match --physdev-in eth9 udp spt:bootpc dpt:bootps 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
output_match  0    --  anywhere             anywhere            MARK match 0xffff 
output_queue  0    --  anywhere             anywhere            state NEW MARK match !0xfffe 
ACCEPT     0    --  anywhere             anywhere            
eth0_out   0    --  anywhere             anywhere            
eth9_out   0    --  anywhere             anywhere            
detect_out  0    --  anywhere             anywhere            
eth2_out   0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            

Chain Drop (0 references)
target     prot opt source               destination         
reject     tcp  --  anywhere             anywhere            tcp dpt:auth 
dropBcast  0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp fragmentation-needed 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
dropInvalid  0    --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            multiport dports loc-srv,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp spt:netbios-ns dpts:1024:65535 
DROP       tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:1900 
dropNotSyn  tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            udp spt:domain 

Chain Reject (0 references)
target     prot opt source               destination         
reject     tcp  --  anywhere             anywhere            tcp dpt:auth 
dropBcast  0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp fragmentation-needed 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
dropInvalid  0    --  anywhere             anywhere            
reject     udp  --  anywhere             anywhere            multiport dports loc-srv,microsoft-ds 
reject     udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
reject     udp  --  anywhere             anywhere            udp spt:netbios-ns dpts:1024:65535 
reject     tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:1900 
dropNotSyn  tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            udp spt:domain 

Chain all2all (17 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            

Chain detect_fwd (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            
all2all    0    --  anywhere             anywhere            
all2all    0    --  anywhere             anywhere            

Chain detect_in (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            

Chain detect_out (1 references)
target     prot opt source               destination         
all2all    0    --  anywhere             anywhere            

Chain dropBcast (2 references)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            PKTTYPE = broadcast 
DROP       0    --  anywhere             anywhere            PKTTYPE = multicast 

Chain dropInvalid (2 references)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            state INVALID 

Chain dropNotSyn (2 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 

Chain dynamic (8 references)
target     prot opt source               destination         

Chain eth0_fwd (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
net2dmz    0    --  anywhere             anywhere            
net2dmz    0    --  anywhere             anywhere            
net2loc    0    --  anywhere             anywhere            

Chain eth0_in (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
net2fw     0    --  anywhere             anywhere            

Chain eth0_out (1 references)
target     prot opt source               destination         
all2all    0    --  anywhere             anywhere            

Chain eth2_fwd (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
all2all    0    --  anywhere             anywhere            

Chain eth2_in (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            

Chain eth2_out (1 references)
target     prot opt source               destination         
all2all    0    --  anywhere             anywhere            

Chain eth9_fwd (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
all2all    0    --  anywhere             anywhere            

Chain eth9_in (1 references)
target     prot opt source               destination         
dynamic    0    --  anywhere             anywhere            state INVALID,NEW 
all2all    0    --  anywhere             anywhere            

Chain eth9_out (1 references)
target     prot opt source               destination         
all2all    0    --  anywhere             anywhere            

Chain input_match (2 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain input_queue (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp spt:www 
RETURN     tcp  --  anywhere             anywhere            tcp spt:433 
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain logdrop (0 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level info prefix `Shorewall:logdrop:DROP:' 
DROP       0    --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level info prefix `Shorewall:logreject:REJECT:' 
reject     0    --  anywhere             anywhere            

Chain net2dmz (2 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
all2all    0    --  anywhere             anywhere            

Chain net2fw (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
all2all    0    --  anywhere             anywhere            

Chain net2loc (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
all2all    0    --  anywhere             anywhere            

Chain output_match (1 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain output_queue (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:433 
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 1

Chain reject (7 references)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            PKTTYPE = broadcast 
DROP       0    --  anywhere             anywhere            PKTTYPE = multicast 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/4  anywhere            
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     icmp --  anywhere             anywhere            reject-with icmp-host-unreachable 
REJECT     0    --  anywhere             anywhere            reject-with icmp-host-prohibited 

Chain shorewall (0 references)
target     prot opt source               destination         

Chain smurfs (0 references)
target     prot opt source               destination         
LOG        0    --  192.168.11.255       anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       0    --  192.168.11.255       anywhere            
LOG        0    --  192.168.11.255       anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       0    --  192.168.11.255       anywhere            
LOG        0    --  192.168.2.255        anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       0    --  192.168.2.255        anywhere            
LOG        0    --  255.255.255.255      anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       0    --  255.255.255.255      anywhere            
LOG        0    --  BASE-ADDRESS.MCAST.NET/4  anywhere            LOG level info prefix `Shorewall:smurfs:DROP:' 
DROP       0    --  BASE-ADDRESS.MCAST.NET/4  anywhere            

```


Here is output from ipblock -l

```
root@watson:~# ipblock -l
Queue   Policy (mark)   Ranges  Target (mark)   File
0       REPEAT (65534)  236195  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz
1       REPEAT (65534)  236195  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz

Chain input_match (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain output_match (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    5   420 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

```

Any help or advice would be great, let me know if you need more info??

---

### Post by ekimregnirps on 2007-12-10
Go Here for Solution!
[http://ubuntuforums.org/showthread.php?t=631331&highlight=iplist](http://ubuntuforums.org/showthread.php?t=631331&highlight=iplist)

---

