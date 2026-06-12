---
title: "routing"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2006-11-20
I am trying to route the Internet connection to eth1 
eth0 = external network(Internet)
eth1 = internal network (192.168.1.1)

Can anyone tell me what is the difference 

 1)
   iptables -A FORWARD -i eth1 -s 192.168.1.2  -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT 
   iptables -A FORWARD -i eth0 -d 192.168.1.2  -m state --state ESTABLISHED,RELATED -j ACCEPT      
   iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

2)
  iptables -t nat -A PREROUTING -i eth0 -j DNAT --to 192.168.1.2
  iptables -A FORWARD -j ACCEPT

---

### Post by steve.horsley on 2006-11-20
1)
This doesn't block any packets at all. You really ought to have a default deny at the end of the chain. 
It allows both your machine and the other (.2) machine to use the interent, making the other machine appear to be at the same address as your machine.

2)
Again, no blocking as such. It does however rewrite **all** incoming packets to address them to the other machine, so your mechine will never see any responses from the internet. 
However, since it doesn't change the source address of the other machine on outgoing packets, the internet would only see the other machine's 192.168 address which is not legal on the internet, so nothing will be able to reply to the other box either.
This breaks internet access for both machines, by my reckoning.

P.S.
#2 requires that you enable IP forwarding. I'm not sure about #1. You can enable IP forwarding with this command:
sudo echo 1 > /proc/sys/net/ipv4/ip_forward

---

