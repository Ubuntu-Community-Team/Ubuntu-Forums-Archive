---
title: "Configuring Shorewall??"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Gales on 2007-08-24
How to configure Shorewall?
what to do? what to configure?
i already installed shorewall.
i have no idea at all...
need help down here please.. :confused:

---

### Post by ramjet_1953 on 2007-08-24
Firstly, why have you installed an iptables configuration GUI?

Do you understand that Shorewall is merely a GUI for iptables?

Do you have some port forwarding to configure?

If not, you should leave your iptables firewall well alone.

By default, all portsa re closed and your system is secure.

Regards,
Roger 8)

---

### Post by OoooMatron on 2007-08-25
shorewall isn't a GUI. It uses IP tables as it's core but it has an easier way of setting up its config files, in my opinion.

in the manual it tells you where the default config files are. copy out the files to /etc/shorewall

there are 4 files you need to deal with.

The first is the interface file. This is the physical card. 

```

net eth0 detect routefilter,logmartians,nosmurfs,tcpflags,blacklist

```

then you set up the zone file
```

net ipv4
fw firewall

```

next is the policy file. This file sets the default rules between the fw interface and the network card.
```

fw net ACCEPT
net all DROP info
all all REJECT info

```

and lastly the blocking rules you want to put in place

```

ACCEPT net:192.168.0.0-192.168.255.255 fw tcp 
ACCEPT net:212.97.0.0-219.97.255.255 fw tcp 3306

```

This above is just an example.Tbe first line lets all the ips of my local network through. The last line, using an IP range, allows access to the mysql port (3306). If you have a wireless and a network adapter you need to duplicate the the info in the above files but for eth1 or whatever they are defined as in your network configs.

---

