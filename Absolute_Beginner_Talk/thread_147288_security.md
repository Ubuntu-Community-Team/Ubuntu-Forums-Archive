---
title: "security"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by plexy on 2006-03-19
Hello,

I am looking for firewalls, virus scanner, spyware removals etc. Does anyone know any for linux ubuntu?

I am also using a AMD 64 version. So it is got to support that.

---

### Post by Azrael on 2006-03-19
Haha. Ha. Ha.

The linux kernel already has a builtin firewall called netfilter which you can control from the command line with iptables. If you want you can also configure iptables from a graphical frontend by installing firestarter (sudo apt-get install firestarter).

Linux hardly has any viruses. You don't need any virus scanner.

You *definitely* don't need to worry about spyware. Linux spyware does not exist.

Quite a change from Windows eh? ;)

---

### Post by cilynx on 2006-03-19
Good firewalls are a do-it-yourself proposition.  Read up on IPTables.
Viruses are pretty much a non-issue on *NIX these days, but look into ClamAV if your paranoid or share with Windows boxen.
Spyware is also pretty much a non-issue on *NIX.

---

### Post by dvarsam on 2006-03-20
[QUOTE=cilynx]Good firewalls are a do-it-yourself proposition.  Read up on IPTables.
[/QUOTE]

Can somebody propose some Internet Sites...

... where you can learn how to work/setup/edit IP Tables?

Thanks.

---

### Post by halfvolle melk on 2006-03-20
I found a good document on this. However it's not in English and before IPv6 was used. It asumes the use of a dedicated firewall with external IP 130.89.254.254 and a backend with 192.168.1.x. When I better understand it and find the time I might make a howto on it. Until then check the man page and this example.
```
#!/bin/sh
# basic.firewall
# flush old settings
/sbin/iptables –-flush
/sbin/iptables –-flush nat
/sbin/iptables –-delete-chain
/sbin/iptables –-zero
/sbin/iptables –-zero nat
# IP forwarding
/sbin/iptables --append POSTROUTING --table nat –-out-interface
eth0 --jump SNAT --to-source 130.89.254.254
/sbin/iptables --policy FORWARD ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
# VNC forwarding
/sbin/iptables --append PREROUTING --table nat --protocol tcp -
-destination 130.89.254.254 --jump DNAT –-destination-port 5800
--to 192.168.1.2 –-in-interface eth0
/sbin/iptables --append PREROUTING --table nat --protocol tcp -
-destination 130.89.254.254 --jump DNAT –-destination-port 5900
--to 192.168.1.2 –-in-interface eth0
# ICQ file transfer and mIRC DCC forwarding
/sbin/iptables --append PREROUTING --table nat --protocol tcp -
    destination 130.89.254.254 --jump DNAT –-destination-port
    64000:65000 –-in-interface eth0 --to 192.168.1.2
```

---

### Post by erniewinner on 2006-03-20
:) i was in the same boat... firestarter and avast antivirus are the ones a nooby like me can easily install. give them a go first. i also tried clamav, f-prot and others but no luck with them.:cool:

---

### Post by AndyCooll on 2006-03-20
Maybe because I've come from a M$ background but I always wonder when Linux users say that you don't need anti-virus or firewalls whether they being too complacent. It is true that the chances of a virus infecting a Linux pc are small, but to in my mind it is still better to be safe than sorry.

ClamAV is in the repositories and is easy to install. And as cilynx says Firestarter is a good graphical front end for Linuxes built in IP tables firewall.

:cool:

---

