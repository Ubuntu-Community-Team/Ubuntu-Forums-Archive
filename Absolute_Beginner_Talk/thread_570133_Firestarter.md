---
title: "Firestarter"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-07
Box1
----
eth0 DHCP
eth1 192.168.0.1
Firestarter Inbound Traffic Policy: 'Allow connections from host' 192.168.0.2

Box2
----
eth0 DHCP
eth1 192.168.0.2
Firestarter Inbound Traffic Policy: 'Allow connections from host' 192.168.0.1


And I can't ping. Turn off firewall and I can ping. What did I miss?

---

### Post by bodhi.zazen on 2007-10-07
The defaults in firestarter block pings

See this link : [http://doc.gwos.org/index.php/Firestarter_Guide](http://doc.gwos.org/index.php/Firestarter_Guide)

Start the gui

Go to Firewall -> preferences

click "ICMP Filtering"

Under "Allow following ICMP packet types" tic off teh two echo requests (ping and pong)

Apply settings ;)

---

### Post by ofb on 2007-10-07
The link is down at the moment.

Meanwhile, ICMP filtering is not enabled.

---

### Post by bodhi.zazen on 2007-10-07
Try this link : [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by ofb on 2007-10-08
Yup, that's basic firestarter set-up. I've read that, the manual, and a variety of similar pages. Do you happen to see anything wrong with my stated setup? It looks right to me, and it doesn't work.

---

### Post by ofb on 2007-10-08
I had similar trouble when Box2 was Win. I'm starting to form a 'conspiracy theory'.

Firestarter is a good extremely-simplified interface for iptables -- it's meant to do a few common configurations with very little fuss, and it does. What I'm thinking it doesn't do is handle a second NIC for LAN when you don't used Internet Connection Sharing or DHCP for the local network.

Go Preferences-> Firewall-> Network Settings panel. For mine, the detected device for LAN is correctly shown as eth1. There are two options below: 'Enable Internet Connection Sharing' and 'Enable DHCP for the local network'.

Those options are not checked on mine, because I want neither. This set-up is a LAN of secondary cards with static IPs - the whole point is complete separation from the Internet traffic. This is simple, but less common because people ususally don't have extra cards and a hub lying around.

So I'm thinking that eth1 is blocked by Firestarter until either of the two sub-options is checked. This can probably be confirmed by looking at the iptables, but I don't know how to read iptables.

How's my logic? And can anyone read iptables? It'd be nice to confirm this one way or another, rather than rest on suspicion.

(I got around this previously by using Guarddog. Alas, I need SMTPS now, and it doesn't look like we're going to get Guarddog 2.6 with SMTPS for Ubuntu until sometime after Gutsy. Hence another wrestle with Firestarter.)

---

### Post by ofb on 2007-10-09
Time to experiment. I used a rule from this iptable HowTo to allow all traffic from the other box's LAN card's IP.
[http://wiki.centos.org/HowTos/Network/IPTables](http://wiki.centos.org/HowTos/Network/IPTables)

'sudo iptables -L' before new rule

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh,sftp 
ACCEPT     tcp  --  nsc1.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc1.cv.gv.shawcable.net  anywhere            
ACCEPT     tcp  --  nsc2.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc2.cv.gv.shawcable.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
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
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  192.168.0.2          anywhere            
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

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            

```

new rule: sudo iptables -A INPUT -s 192.168.0.2 -j ACCEPT

'sudo iptables -L' after new rule
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh,sftp 
ACCEPT     tcp  --  nsc1.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc1.cv.gv.shawcable.net  anywhere            
ACCEPT     tcp  --  nsc2.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc2.cv.gv.shawcable.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ACCEPT     0    --  192.168.0.2          anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  192.168.0.2          anywhere            
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

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            

```

Previously 192.168.0.2 only shows up under 'Chain INBOUND'. With the new rule, the IP is added under 'Chain INPUT'.

Still can't ping though. Something else needs changing.

Firestarter configuration is reset by simply starting Firestarter. The Fail2ban entries are lost - presumably these are added to iptables on startup.

Try opening for all packets coming to the local LAN NIC instead:
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -i eth1 -j ACCEPT

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  nsc1.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc1.cv.gv.shawcable.net  anywhere            
ACCEPT     tcp  --  nsc2.cv.gv.shawcable.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc2.cv.gv.shawcable.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc1.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     tcp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net tcp dpt:domain 
ACCEPT     udp  --  S01060001023fcb70.gv.shawcable.net  nsc2.cv.gv.shawcable.net udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  192.168.0.2          anywhere            
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

This new set-up adds the following line to 'Chain INPUT' twice,
ACCEPT     0    --  anywhere             anywhere

/That/ doesn't sound right. Should be an eth1 in there I'd think. Meanwhile, I still can't ping.

Start Firestarter to reset again, and sit back in the chair to ponder more.

---

### Post by ofb on 2007-10-09
The solution is to rubbish Firestarter and reinstall Guarddog.

Then for the SMTPS problem, use this trick I've finally found at the bottom of the linked page, ("on display in the bottom of a locked filing cabinet stuck in a disused lavatory with a sign on the door saying *Beware of the Leopard*.")

[http://www.mepis.org/node/13709](http://www.mepis.org/node/13709)

> For future readers, the specific steps I used are:
1)in Guarddog, advanced tab,click 'New Protocol' then
create name SMTP, type TCP, port 465, click Apply.
2)next, pick 'protocol tab', 'internet zone',
expand the 'user defined' selections and check the
box for SMTP (which was created in step 1) above.
3) click 'Apply' and you should be done.

Do that, and you should finally have the sofa out of your stairwell.

---

