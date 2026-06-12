---
title: "how to access internet from vbox guest"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by signalat on 2007-06-19
my system is feisty, i have xp installed as guest with vbox. everything works fine except the network. no network connection available to the guest xp. I use the default setting: NAT. do i need two network connections if i have two network cards (one wireless and one cable)? currently i just included one network connection in the guest xp. 

the ip for xp is:
IP 10.0.2.15
Gateway: 10.0.2.2
DHCP server: 10.0.2.2
DNS server: 10.0.2.3

i can ping 10.0.2.2 but i can not ping 10.0.2.3.

what should i do? thanx.

---

### Post by Golyadkin on 2007-06-19
Do you run your own DNS server in your home network?

---

### Post by signalat on 2007-06-19
no, i don't think i am running any DNS server program

---

### Post by bodhi.zazen on 2007-06-19
With those settings you are using NAT and it should work out of the box.

Can you get to google.com ?

If you want your vitrual machine to be on you local LAN, you will need to do some configuration.

Networking is a little tricky, you can look here :

[http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)

(I know, I know, the networking section is a bit of a mess right now, sorry I need to update it somewhat)

And the virtual box manual, networking section:

[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

---

### Post by signalat on 2007-06-19
i can not connect to google.com. it should work out of box but not :(

---

### Post by Golyadkin on 2007-06-19
If you do not run a DNS server on a machine with IP 10.0.2.3 then you need to change the DNS settings to your ISPs DNS servers.

---

### Post by signalat on 2007-06-19
my host uses ISP's DNS. guest xp uses ISP's DNS also? just tried, doesn't work. can not ping DNS at all.

---

### Post by Golyadkin on 2007-06-19
Why would you want to ping a DNS server? When I run a DNS server, I tell it not to respond to PINGs.

Yes, the guest xp should have the ISP's DNS settings also, it is the only way it can resolve hostnames to ip addresses.

---

### Post by bodhi.zazen on 2007-06-19
Golyadkin: Thanks for your help on this thread, you have been awesome (not to mention you are saving me some typing)

---

### Post by signalat on 2007-06-19
thanx guys, it works now. i use ISP's DNS for the guest and it didn't work for the first time, then i restarted xp, now it works. however, still confiused that i should use ISP's DNS, cause i think my host should take care of it.  anyway, thanx.

---

### Post by Golyadkin on 2007-06-19
> **bodhi.zazen said:**
> Golyadkin: Thanks for your help on this thread, you have been awesome (not to mention you are saving me some typing)

You are welcome, I am just trying to help answer the questions I know the answer to :) just to do something back for the times I asked for help around here.

---

### Post by Golyadkin on 2007-06-19
> **signalat said:**
> thanx guys, it works now. i use ISP's DNS for the guest and it didn't work for the first time, then i restarted xp, now it works. however, still confiused that i should use ISP's DNS, cause i think my host should take care of it.  anyway, thanx.

Alright cool, I am happy it works for you. To explain a little bit about NAT, it works like this:

Your host machine is connected to a router (or modem with a built-in router) which in turn is connected to the Internet. NAT stands for Network Address Translation, which means that if packets come from the Internet to your router, your router knows to which computer in your network the packet needs to go. If you use NAT for the guest operating system, it is the same as if you connect a second physical computer to your router. For the network purposes, the host and guest are not the same computer at all. They are not directly "connected" to each other network-wise. That is why it needs its own network settings.

---

