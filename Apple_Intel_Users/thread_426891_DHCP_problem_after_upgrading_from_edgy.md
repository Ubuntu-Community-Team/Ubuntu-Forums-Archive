---
title: "DHCP problem after upgrading from edgy"
date: 2007-04-28
forum: Apple Intel Users
---

### Post by Kimie Nakahara on 2007-04-28
Hello!

After upgrading ubuntu from edgy to feisty on my macbook, I cant connect the internet using dhcp. Right after the boot, the ifconfig configuration were something like "192.168.0.100", then I've tried:

sudo ifdown eth0

then

sudo ifup eth0

then it returns the configuration that works on Mac OS:

server 10.0.0.138
ip 10.0.0.5

this configuration was working on edgy before, and as I can ping the gateway but not internet ips, I don't know what to do - reinstalling edgy is out of consideration. :-)

Someone could help me?

Thank you

---

### Post by Kimie Nakahara on 2007-04-29
It seemed to be a router problem. Now dhcp server is working properly.

---

