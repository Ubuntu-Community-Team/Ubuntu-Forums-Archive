---
title: "Internet settings"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by harrydee on 2007-04-06
I find that I have to re-enter the DNS settings every time I start Ubuntu, to log on to the internet.I expect it's a simple job to save these settings but I can't seem to find info on it. Any help much appreciated.:confused:

---

### Post by zvacet on 2007-04-06
system>administration>network settings>highlight your modem>propertoes>choose your type of connection>chek upper left box>close Go to the DNS tab>replace address with your nameserver>close
```
pppoeconf
```

---

### Post by sirhalos on 2007-04-06
The manual way also would be to add your DNS settings to /etc/resolv.conf

nameserver 192.168.0.1

Just as an example.

---

### Post by ScooterDMan on 2007-04-07
OK, that makes sense.

How would I go about determining my nameserver?

---

### Post by LaurelLynn on 2007-04-07
Dear ScooterDMan,

Open up:  System->Administration->Networking

Click on the DNS tab. It will list the IP addresses of whatever name servers you are currently using.

Adding them to /etc/resolv.conf   will make them permenant (till you remove them).

Laurel Lynn

---

### Post by zvacet on 2007-04-07
Nameservers are address of your internet provider.If you don´t know your nameservers you can use this
[http://opendns.com/start/ubuntu.php]("http://opendns.com/start/ubuntu.php")

---

