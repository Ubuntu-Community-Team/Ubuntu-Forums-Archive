---
title: "networking problem"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-23
Hi friends i'm trying to configure apache2 and squid but when i run this command appear the next error:
root@linux:/etc/postfix# /etc/init.d/networking restart
 * Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
   ...done.

Why ?

---

### Post by Willye on 2007-11-23
anddddd ?????

---

### Post by overdrank on 2007-11-23
> **Willye said:**
> anddddd ?????

HI and I am no expert on virtual machines but you may want to look there first before asking questions. There is also another forum for virtual machines 
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)
You may get better results there.

---

### Post by Willye on 2007-11-23
i don't understand why the problem is virtual machine, i'm running a OS command and apparently main.cf doen't exist, the questions is necesary to install some package to fix the problem or what

---

### Post by Willye on 2007-11-23
then

---

### Post by The Cog on 2007-11-23
It is possible that rather than main.cf not existing, main.cf is running and complaining that something that it doesn't bother to try and name doesn't exist. 

But I don't think that is the root cause of your problems. Your first error messages are complaining that eth0 doesn't exist. What is the output from the command **ifconfig** ?

---

