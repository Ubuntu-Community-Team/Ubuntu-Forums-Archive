---
title: "Anyone else disable ipv6 in Firefox, it just speeded up page loading  significantly"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-19
I was getting very slow page loading so set 

network.dns.disableipv6 to true

Wow what a difference, major speed up. I read this [http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)

and thought well it's only a setting that can easily be changed back. Anyway what a result.

---

### Post by skymera on 2007-10-19
hey

mine was already disabled, so i disabled in a file etc.

also i just added  this :

```

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```

to /etc/sysctl.conf
and WOW, that made a difference, before i got 7second loading time, now 0.5secs.

i done lots of other stuff too, pipelining in about:config

lots out there :)

---

### Post by philinux on 2007-10-19
This is what's in my file, not a lot,  can you paste yours in a message or attach the file so I can compare.

---

### Post by skymera on 2007-10-19
sure :D
heres mine
just added what i posted above and swap=0

---

### Post by philinux on 2007-10-19
Tried those settings - no diff on my machine at all, bit slower if anything

---

### Post by davidjmayo on 2007-10-19
I disabled IPv6 in Firefox quite a while ago and found an improvement.

BTW another one I find cuts down page loading time is to use the NoScript plugin for Firefox and not allow google-analytics as this can waste a few (or more) seconds on some pages, Don't remember exactly what google-analytics does but something like a traffic tracker for the site host.

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

### Post by philinux on 2007-12-05
> **moe_syzlak said:**
> this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching


This thread was started 19th Oct - your solved thread was only started 2 weeks ago. :confused:

---

