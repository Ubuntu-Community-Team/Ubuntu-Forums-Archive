---
title: "Cannot add DNS"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by DrGraeme on 2007-11-25
Hopefully someone can point me in thr right direction.

I am have installed Ubuntu 7.10.  

When setting up the ethernet network card for the internet I set the static IP, subnet and gateway fine.  When I go to put in the DNS IP it will not add/save.

Whenever I've set up a windows computer Iv entered IP, Subnet, Gateway and the DNS IP and I've been off and running.

If anyone can tell me what I'm doing wrong or how to get the DNS IP to save I will be most appreciative.

Graeme

---

### Post by mellowd on 2007-11-25
I'm assuming your're talking about the DNS server you are talking to as opposed to a DNS server running on the machine? Is there a reason you are not using dhcp?

---

### Post by tesserhex on 2007-11-25
Assuming you want to go with static IP (for security, or some other reason) then you could make the changes as below:-

Assumes the network interface is set up as Static, check this by whatever means you know or use

```
$ sudo nano /etc/network/interfaces
```

and look for the interface, it should be like:-

[INDENT]iface eth0 inet static

With details immediately below for
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
network xxx.xxx.xxx.xxx
broadcast xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
[/INDENT]
Setup the DNS servers by opening /etc/resolv.conf file
```
$ sudo nano /etc/resolv.conf
``` 

and removing any legacy DHCP settings and replacing with your own settings for the nameserver(s)

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

---

### Post by DrGraeme on 2007-11-25
Thanks all

I went fixed for my network years ago. It overcame a few issues, and the thing has been running without problems since.

The advice provided about how to solve the problem has worked perfectly.

Graeme :-)

---

