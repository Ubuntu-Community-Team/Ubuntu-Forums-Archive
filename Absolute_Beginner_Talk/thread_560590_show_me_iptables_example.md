---
title: "show me iptables example"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-26
can someone show me how to add port 80 to iptables input

sudo iptables -A   then what

---

### Post by Matt Yun on 2007-09-26
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by darc on 2007-09-26
Are you wanting to block port 80 or allow port 80?

To drop packets coming to port 80:
```

iptables -A INPUT -i eth0 -p tcp --destination-port 80 -j LOG
iptables -A INPUT -i eth0 -p tcp --destination-port 80 -j DROP

```

Change it to ACCEPT to allow them.


Here's my (old) iptables config script which will give you an example of several things:
```

#Set Defaults
iptables -P FORWARD DROP
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT

echo "Applying ppp0 protection..."
iptables -A INPUT -i ppp0 -p tcp --syn -j LOG
iptables -A INPUT -i ppp0 -p tcp --syn -j DROP
iptables -A INPUT -s 10.0.0.0/24 -i ppp0 -p tcp -j LOG
iptables -A INPUT -s 10.0.0.0/24 -i ppp0 -p tcp -j DROP
iptables -A INPUT -i ppp0 -p icmp --icmp-type echo-request -j LOG
iptables -A INPUT -i ppp0 -p icmp --icmp-type echo-request -j DROP
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j LOG
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j DROP

echo "Applying eth0 protection..."
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 99 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 2100:2300 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --syn -j LOG
iptables -A INPUT -i eth0 -p tcp --syn -j DROP
iptables -A INPUT -s 10.0.0.0/24 -i eth0 -p tcp -j LOG
iptables -A INPUT -s 10.0.0.0/24 -i eth0 -p tcp -j DROP
iptables -A INPUT -i eth0 -p icmp --icmp-type echo-request -j LOG
iptables -A INPUT -i eth0 -p icmp --icmp-type echo-request -j DROP

#CUPSD Blocking
iptables -A INPUT -i eth0 -p tcp --destination-port 631 -j LOG
iptables -A INPUT -i eth0 -p tcp --destination-port 631 -j DROP
iptables -A INPUT -i ppp0 -p tcp --destination-port 631 -j LOG
iptables -A INPUT -i ppp0 -p tcp --destination-port 631 -j DROP

```

---

### Post by reckless2k2 on 2007-09-26
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

does that help? not sure why port 80. if you install apache it opens port 80. is that what you're getting at?

anyway, that how to should help.

---

### Post by reckless2k2 on 2007-09-26
geez...you guys are too quick.

---

### Post by larry Gaminde on 2007-09-26
thanks everyone

---

