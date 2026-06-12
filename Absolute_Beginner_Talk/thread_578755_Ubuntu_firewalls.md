---
title: "Ubuntu firewalls?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by gaz_o_d on 2007-10-17
My new computer got up and running a couple days ago and I instructed my computer guy to put Ubuntu on it after hearing good things from mates....it's brilliant.

I have heard that there's very few, if any, malicious software for linux, so i was at ease about my internet security. However, i thought it would be best to check, is it wise to get a firewall or internet suite for my new computer, and if so..any good ones? Considering i am a complete n00b when it comes to internet settings and that kind of thing.

Any help is well appreciated :grin:

---

### Post by Pumalite on 2007-10-17
You don't need firewalls with Ubuntu, but if you want to install a router, that would be fine.

---

### Post by bsharp on 2007-10-17
There already is a built-in firewall installed called IPtables (or something similar) that has all ports closed by default. There is a gui called Firestarter for this program that you can install through Synaptic, but unless you plan to run some kind of server off your laptop :roll: then there really isn't a need for it

---

### Post by Ozeuss on 2007-10-17
a simple firewall is firestarter, it is available in the repos. there are lots of tutorials out there. there are also AV software for linux, but as a desktop user, you probably don't need one (just stick to software in the repos and don't open silly mails).

---

### Post by gaz_o_d on 2007-10-17
ok cool, saves a load of confusion...

only thing is, i use deluge torrent client alot...not sure if that's putting me at risk :/

---

### Post by oilchangeguy on 2007-10-17
> **Ozeuss said:**
> a simple firewall is firestarter, it is available in the repos. there are lots of tutorials out there. there are also AV software for linux, but as a desktop user, you probably don't need one (just stick to software in the repos and don't open silly mails).

this is not correct. firestarter is not a firewall. for the correct answer see post #3.

---

### Post by Pumalite on 2007-10-17
I might be wrong, but I thought all ports came OPEN by default.

---

### Post by oilchangeguy on 2007-10-17
> **Pumalite said:**
> I might be wrong, but I thought all ports came OPEN by default.

nope, closed. this is one of the many security pluses for ubuntu.

---

### Post by Pumalite on 2007-10-17
Funny, because I've used all kind of ports without messing with the IPTables.

---

### Post by oilchangeguy on 2007-10-17
> **Pumalite said:**
> Funny, because I've used all kind of ports without messing with the IPTables.

see this:
[http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution))

---

### Post by gaz_o_d on 2007-10-17
im not sure whether mine are open or closed, but deluge seems to be downloading files veryyy slowly, don't know if i need to set up a DMZ on my router or UPnP?? i'm getting like 10kb/s on deluge but when i download something straight from a site im getting anything between 200-500kb/s :S:S

---

### Post by Pumalite on 2007-10-17
Thanks.

---

### Post by robert_pectol on 2007-10-17
> **Pumalite said:**
> I might be wrong, but I thought all ports came OPEN by default.
> **oilchangeguy said:**
> nope, closed. this is one of the many security pluses for ubuntu.

Maybe I can clear up some of the confusion.  The packet filtering mechanism in the kernel (netfilter) is configured by default to allow everything.  This does NOT mean that any ports are open.  It simply means that they are not blocked.  A tool such as iptables can be used to change the default configuration of the packet filtering in the kernel.  Since iptables is very syntax-intensive, several configurators such as Firestarter have come about, to assist in manipulating the iptables tool, and ultimately establishing a firewall.  Whether or not ports are open or closed is determined by the applications that require them when they are running.

---

### Post by Pumalite on 2007-10-17
That definitely cleared up MY confusion.

---

### Post by ruibernardo on 2007-10-17
Ubuntu comes with all its ports closed by default, because it hasn't any ports listening. If you install any server on it, for example p2p, share files or install SMB/FTP/SSH/etc servers, then you should install a firewall (configure iptables).

From [http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus):

> **So, do I need a firewall, anti-virus, anti-spyware tools?**
_By default_, _Ubuntu ships with no open ports_ on public interfaces. In other words, a "port scan" would show all closed ports, nothing open....
_A firewall_, _however_, _adds_ the benefit of _peace-of-mind from_ accidentally _installing a server program that opens up a port_ by default.
So, if you install any server, you must set up the firewall.

That is, the (default) firewall security ends when you install a server.

---

### Post by pacsum on 2007-10-17
I'm going to put it straight and simple. 

1.Install Firestarter on   System>administration>Synaptic package manager

2.After the install, open Firestarter  System>administration> Firestarter

3.On the events tab (@ Firestarter) you will see which ports are being blocked.

4.Open your torrent downloader program, then go to settings and see what port is being used by the torrent app.

5.When you'll start to download the torrent, Firestarter will probably show some ports blocked already, check if there is shown the port you just checked on the torrent app. If so, right click> allow inbound service for everyone.

That's it.

*do the same with all peer to peer or software you suspect is being blocked by iptables and allow the port.

---

### Post by Ozeuss on 2007-10-18
> **gaz_o_d said:**
> im not sure whether mine are open or closed, but deluge seems to be downloading files veryyy slowly, don't know if i need to set up a DMZ on my router or UPnP?? i'm getting like 10kb/s on deluge but when i download something straight from a site im getting anything between 200-500kb/s :S:S

You can use port-forwarding on your router instead for the specific ports used by deluge (use a high port number and not 6881).

---

### Post by yashoda on 2007-10-29
Hi, 

I have a problem with downloading torrents.

I've configured my router to open ports 6881-9, yet the downloads are still extremely slow (around 20kb/s).  I've disabled Firestarter.  Still the port seems to be closed.

Please advise how to speed up downloads.

Thanks.

---

### Post by Pumalite on 2007-10-29
Use a port over 45.000

---

### Post by steve.horsley on 2007-10-29
> **Pumalite said:**
> Use a port over 45.000

Why is that? Are they different somehow?

yashoda:
The real proof that the firewall is disabled is to look at the output from the command **sudo iptables -L** and if you see output like this:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
then the firewalling is truly disabled.

---

### Post by ruibernardo on 2007-10-29
> **yashoda said:**
> Hi, 

I have a problem with downloading torrents.

I've configured my router to open ports 6881-9...

If you are using a router, it's not just a question of opening the ports. On the router, you need to forward them to the computer on your network and then, on that computer, to have those ports open.

More info about how to forward ports on routers here:  [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm).

---

