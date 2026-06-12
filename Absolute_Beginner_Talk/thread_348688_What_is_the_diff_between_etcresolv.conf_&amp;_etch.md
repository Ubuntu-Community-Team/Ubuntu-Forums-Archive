---
title: "What is the diff between /etc/resolv.conf &amp; /etc/hosts?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-29
Hello!

I would like to know what do the following files do:

1. /etc/resolv.conf
2. /etc/hosts
3. What is the diff between 1 & 2?

Thanks.

---

### Post by dmitry on 2007-01-29
/etc/resolv.conf contains ip of DNS servers.
/etc/hosts is simple file that associate ip address of hosts with host names. One ip per line.

BTW for more information try 

~$ man hosts
~$ man resolv.conf

---

### Post by movies1978 on 2007-01-29
Hi,
in /etc/resolv.conf you can specify a nameserver with a line like
```
nameserver 123.456.789
```

In /etc/hosts you can make static pairs of ipaddress and canonical names. This file is preffered by the nameresolution overt the dnsserver.

Greetz
Mathias

---

### Post by dvarsam on 2007-01-29
[QUOTE=movies1978]In /etc/hosts you can make static pairs of ipaddress and canonical names. 
This file is prefferred by the nameresolution over the dnsserver.
[/QUOTE]

So, can I edit the file "/etc/hosts", and add the following:

192.168.1.2 dimitris-desktop.workgroup
192.168.1.2 dimitris.workgroup

# Both representing the same IP but each using a diff user name.

I am asking this, because sometimes I want to open up a Web browser & type:

[https://dimitris/apt-cacher](https://dimitris/apt-cacher)

Instead of having to type:

[https://dimitris-desktop/apt-cacher](https://dimitris-desktop/apt-cacher)

OR having to type: [https://192.168.1.2/apt-cacher](https://192.168.1.2/apt-cacher)

I would like to be able to use both of these notations...
Is that possible?

Thanks.

---

