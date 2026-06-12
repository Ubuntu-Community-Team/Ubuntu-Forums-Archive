---
title: "How do I block a range in IPTables?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-12-08
My server was under attack by an IP address that cannot be resolved, easilly, to an ISP:

> inetnum:         128.0.0.0 - 128.255.255.255
netname:         EU-ZZ-128
descr:           Various Registries
country:         EU # Country is really world wide
remarks:         These addresses were issued by
              The IANA before the formation of
              Regional Internet Registries.
              <http://www.iana.org/assignments/ipv4-address-space>

> 128/8   May 93   Various Registries

So I would like to block 128.42.*  or even 128.*


I tried 128.42.* and got an error message saying the ip address was incorrect and had to enter the full IP address. I was using webmin to add the rule.

---

### Post by daniminas on 2006-12-08
```
/sbin/route add -host <ip address> reject

/sbin/route del -host <ip address> reject
```

---

### Post by linuchsan on 2006-12-08
128.0.0.0 or 128.42.0.0 not 128.* or 128.42.*
iptables -I INPUT -s 128.42.0.0/<mask number> -j DROP 
This will be lost after a reboot, so you have to place it, in a startup script

---

