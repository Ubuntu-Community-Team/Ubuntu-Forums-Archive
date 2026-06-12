---
title: "Ok, let's start from the beginning:"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by OfficeLinebacker on 2006-04-08
How do I use an Ubuntu box with two ethernet NICS in it to share the internet connection from a cable modem to a bunch of other computers via a switch?  (No crossover cables involved)

---

### Post by OfficeLinebacker on 2006-04-08
Current output from iptables -L :

```

Chain INPUT (policy DROP)
target     prot opt source               destination
DROP       all  --  127.0.0.0/8          anywhere
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP      !udp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
DROP       icmp -f  anywhere             c-69-140-50-55.hsd1.md.comcast.net
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             c-69-140-50-55.hsd1.md.comcast.net state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             c-69-140-50-55.hsd1.md.comcast.net icmp echo-request limit: avg 1/sec burst 3
ACCEPT     tcp  --  anywhere             c-69-140-50-55.hsd1.md.comcast.net tcp dpt:www flags:FIN,SYN,RST,ACK/SYN state NEW
ACCEPT     tcp  --  anywhere             c-69-140-50-55.hsd1.md.comcast.net tcp dpt:ftp flags:FIN,SYN,RST,ACK/SYN state NEW
ACCEPT     tcp  --  anywhere             c-69-140-50-55.hsd1.md.comcast.net tcp dpt:ftp-data flags:!FIN,SYN,RST,ACK/SYN state NEW
REJECT     tcp  --  anywhere             c-69-140-50-55.hsd1.md.comcast.net tcp dpt:auth reject-with tcp-reset
ACCEPT     all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Fell off input chain: '

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  192.168.0.0/24       anywhere            state NEW,RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Fell off forward chain: '

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  c-69-140-50-55.hsd1.md.comcast.net  anywhere            state NEW,RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Fell off output chain: '

```

---

### Post by OfficeLinebacker on 2006-04-09
hoping some of my fellow insomniacs might be up

---

### Post by 5-HT on 2006-04-09
[LEFT]Insomniac here:
Haven't done this myself, but what about going the easy route and setting it up with Firestarter? It's a firewall but also has internet connection sharing abilities, and what looks like DHCP serving as well.
[/LEFT]

---

### Post by OfficeLinebacker on 2006-04-09
5-HT, that was my first thought, but the error I get is that the secondary (inward-facing) eth device is not working, or that "an unspecified error occurred."

---

### Post by NeghVar on 2006-04-09
I'm not positive but I think this is what your looking for.

[https://wiki.ubuntu.com/ShareInternetConnection?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/ShareInternetConnection?highlight=%28CategoryDocumentation%29)

---

### Post by OfficeLinebacker on 2006-04-09
Whoa, I saw another page just like that:
 
[https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing?highlight=%28firestarter%29]("https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing?highlight=%28firestarter%29")
 
Mind if I ask which one you suggest?

---

### Post by NeghVar on 2006-04-09
If you can use the firestarter method Id go for that. Im no expert btw, just looked around the on thiki for sumtin that resembled what u were lookin for.

---

### Post by OfficeLinebacker on 2006-04-09
the thiki?
 
Is that some new internet slang?

---

