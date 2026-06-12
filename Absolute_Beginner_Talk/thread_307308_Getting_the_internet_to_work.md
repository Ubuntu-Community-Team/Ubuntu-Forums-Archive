---
title: "Getting the internet to work"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by confudler on 2006-11-26
Hi, I have just installled edgy and I can't get my internet working. I want to use the connection from my windows PC (using ICS). This worked fine on the live test but does not work now that edgy is installed. 

I didn't consider myself a novice but have to admit this is probably very basic. 

Given that the internet fed through fine when I was using the live CD, I am guessing it is the Ubuntu setting that need adjusting. When I look at the network settings the "DNS Servers" box is empty which is possibly something to go on.

---

### Post by shin on 2006-11-26
Huh. I dont really know how your windows connection ICS works but it's probably just plain dhcp service. Anyway:

try to ping some IP e.g. 66.94.234.13 (yahoo)

if it is pingable, all you need to do is set some DNS servers
edit file /etc/resolv.conf (with root rights, so sudo <any editor here> <file>) and add there dns servers you want to use

You may just want to use dnses from your windows installation.

to check them - 'ipconfig /all' in command line. add them to resolv.conf in such a way:

nameserver <IP>
e.g.
nameserver 127.0.0.1

If yahoo ip is not pingable, post your 'ifconfig' output
and contents of /etc/network/interfaces .

---

