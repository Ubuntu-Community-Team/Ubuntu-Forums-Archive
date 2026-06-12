---
title: "Setting DNS"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by yme on 2007-02-21
Hi:

I have just set up ubuntu 6.06 and made an internet connection via pppoe. 

This involves setting the DNS in 'network connections'. I did this but everytime I start up the system has 'forgotten' and I need to start again. Strangely it remembers the hostname. 

I guess I am missing something very simple ...

me!

---

### Post by taux on 2007-02-21
I would recomend you editing /etc/resolf.conf file directly. It is the list of DNS servers. The structure is this:

nameserver [server1 IP]
nameserver [server2 IP]

---

### Post by kerry_s on 2007-02-21
You have to put your settings in /etc/dhcp3/dhclient.conf.

---

### Post by zvacet on 2007-02-21
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with  Exec=gksudo tkpppoe
If you still are not able to get gui to work just ```
cd /opt/rp-pppoe
```
and then```
./go
```

---

### Post by r4ik on 2007-02-21
Manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

---

### Post by yme on 2007-02-21
Just to clarify: this is using the GUI ...

---

### Post by yme on 2007-02-24
It is quite bizarre but out of the last three times I have turned the system on, on the first and the third, of the three DNSs I had set one did remain and there was also another one that I didn't set that had appeared! What is happening here?

On the second time I started up it was just as I initially reported: the three DNSs I set were gone and the DNS was given as a default which I think is on the install CD.

Mystified,

me!

---

