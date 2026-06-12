---
title: "network refuses to work"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by dfwcomputer on 2006-08-04
hi all,

I am a noob to ubuntu but have a fair amount of experience with mandriva and red hat.I recently installed ubuntu and for some reason the network refuses to work.I have followed a few tutorials but to no avail.

so far i have;

setup a root password

configured the /etc/network/interface as follows

auto eth0
iface eth0 inet static
        address 192.168.3.101
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
        gateway 192.168.3.1

I have configured /etc/hosts;

127.0.0.1       localhost.localdomain localhost
192.168.3.101   server.ubuntu     server

But when you /etc/init.d/networking restart the system just locks up and you have to reset.


Any ideas would be greatly appreciated.

Dean

---

