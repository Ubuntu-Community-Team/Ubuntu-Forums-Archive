---
title: "Internetz only works whent I start Firestarter"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-07-31
Hello. When I try to start any web application (Firefox, Opera, Update Manger) they don't connect to the Internet. However, once I start Firestarter, it works perfectly fine.

I checked the iptables before and after I activated Firestarter and this is what it came up with

Before:
Chain INPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 

DROP       0    --  127.0.0.0/8          anywhere            

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain FORWARD (policy DROP)

target     prot opt source               destination         

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere            



Chain OUTPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     0    --  anywhere             anywhere            

DROP       0    --  anywhere             224.0.0.1           

LOG        0    --  anywhere             anywhere            LOG level warning 

DROP       0    --  anywhere             anywhere

After (sorry if it's really long):
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cns.manassaspr.va.dc02.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.manassaspr.va.dc02.comcast.net  anywhere            
ACCEPT     tcp  --  cns.chelmsfdrdc2.ma.boston.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.chelmsfdrdc2.ma.boston.comcast.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
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
ACCEPT     tcp  --  192.168.1.123        cns.manassaspr.va.dc02.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.123        cns.manassaspr.va.dc02.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.123        cns.chelmsfdrdc2.ma.boston.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.123        cns.chelmsfdrdc2.ma.boston.comcast.net udp dpt:domain 
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
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  169.254.151.75       anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  169.254.7.110        anywhere            
ACCEPT     0    --  169.254.7.110        anywhere            
ACCEPT     0    --  192.168.1.100        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.2.1          anywhere            
ACCEPT     0    --  192.168.2.1          anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
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
andrew@andrew-laptop:~$ sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cns.manassaspr.va.dc02.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.manassaspr.va.dc02.comcast.net  anywhere            
ACCEPT     tcp  --  cns.chelmsfdrdc2.ma.boston.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.chelmsfdrdc2.ma.boston.comcast.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
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
ACCEPT     tcp  --  192.168.1.123        cns.manassaspr.va.dc02.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.123        cns.manassaspr.va.dc02.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.123        cns.chelmsfdrdc2.ma.boston.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.123        cns.chelmsfdrdc2.ma.boston.comcast.net udp dpt:domain 
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
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  169.254.151.75       anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.103        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  192.168.1.123        anywhere            
ACCEPT     0    --  169.254.7.110        anywhere            
ACCEPT     0    --  169.254.7.110        anywhere            
ACCEPT     0    --  192.168.1.100        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.102        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.2.1          anywhere            
ACCEPT     0    --  192.168.2.1          anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.101        anywhere            
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

---

### Post by st33med on 2007-07-31
Bumping.....

---

### Post by st33med on 2007-07-31
May it help if I said PLEASE?

--quoted from 'Lieutenant Johnson' in Halo 2

---

### Post by Lakefall on 2007-07-31
Well, these commands flush all chains and set everything except forwarding (which you don't probably need) to accept everything by default.

```
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
```

This isn't the most secure setting ever.

If you want to have a simple firewall, which blocks unrelated incoming connections, but allows outgoing ones, do this instead.

```
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i lo -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
```

However these settings do not persist over a reboot, so you need to either run a script with the commands at boot or use iptables-save and then run iptables-restore appropriately at boot.

Example:```
iptables-save > /etc/network/firewall.conf
iptables-restore < /etc/network/firewall.conf
```

---

### Post by ayenack on 2007-07-31
Is it a problem having Firestarter starting when you log in? If not take a look at [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_the_Firestarter_GUI_start_automatically_at_startup") it enables Firestarter to start automatically and without you having to type password.

Best of luck. ayenack.

In Firestarter Policy Tab have you blocked anything? I find this strange because Firestarter should already be started as soon as your PC picks up its network. Try this and let me know the outcome. Restart you Comp login but do not start Firestarter from System>Administrator>Firestarter instead In terminal type this.

sudo /etc/init.d/firestarter status

This will tell you if Firestater is already running. If it is this means that you have set some policy in the Firestarter GUI.

---

### Post by st33med on 2007-07-31
Thanks, very much! The fact that I had to restart Firestarter every single time was getting on my nerves!

Also, the script runs in a startup script called /etc/rc.local. It is a custom startup script that runs after everything else.

---

### Post by ayenack on 2007-07-31
That's right. It's the script I use. Still curious why you could not log on without  running the GUI. Don't suppose you tried the other suggestion. Ah well.

L8R's ayenack.

---

### Post by st33med on 2007-07-31
ayeneck, I found that the script would work better and be a bit more secure. However, on the page you gave me, the was a Firefox plugin that I really liked. The MediaPlayerConnectivity really works for me, even on divx when my VLC Firefox plugin wouldn't work. Thank you!

---

### Post by ayenack on 2007-07-31
Cool.

---

