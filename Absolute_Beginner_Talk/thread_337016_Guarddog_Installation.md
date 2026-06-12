---
title: "Guarddog Installation"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by JerrySC on 2007-01-12
I love this operating system so far!  I decided to put a firewall on it so I installed the Guarddog firewall package for Edgy.  The package manager downloaded everything and installed it with no errors.  I checked the package manger and it shows it installed.  Only problem is I don't see any new application or an interface of any kind!  What am I doing wrong?

---

### Post by halfvolle melk on 2007-01-12
Probably nothing.
```
iptables -L
```
should tell whether there are firewall rules in place or not.

---

### Post by jd65pl on 2007-01-12
First of all note guarddog is not a firewall be a gui front end for configure the already installed firewall IPtables. To get it running try

```
gksudo guarddog
```

---

### Post by ComplexNumber on 2007-01-12
> **jd65pl said:**
> First of all note guarddog is not a firewall be a gui front end for configure the already installed firewall IPtables. To get it running try

```
gksudo guarddog
```
i was going to say that - you beat me to it :D. when i was using PClinuxOS, i was using guarddog as a frontend for shorewall. and shorewall is a non-graphical frontend for iptables. so maybe guarddog uses shorewall instead, although i suspect that it was PCLinuxOS that had it as its default firewall backend.

---

### Post by JerrySC on 2007-01-12
Thanks!  I opened up just the ports I needed and she's working fine.

---

