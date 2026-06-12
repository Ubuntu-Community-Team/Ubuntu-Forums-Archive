---
title: "ping does not return"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by m_atif on 2007-08-23
hi,
I am facing a weird problem. From one of the ubuntu workstations I can Ping some workstations (all ubuntu feisty) but not all. To elaborate further: 
I can ping a set of systems say a, b, c
If i try to ping some IP which doesnot exist, ping gives me correctly "Destination Host Unreachable". 
But again there are some hosts (say x,y,z) to which ping simply does not return anything and it gets stuck and returns nothing. I have to do ctrl+c to break it and then it gives me "xxx packets transmitted, 0 received, 100% packet loss". 
All the workstations have same subnet, netmask etc.

Can anyone through some light?:confused:

---

### Post by ikonia on 2007-08-23
try leaving it for a while and I'm sure it will time out.

something is potentially blocking the requests to those hosts, be it your own firewall, a network firewall or the clients having a firewall (firewalls could be also say a router with icmp turned off).

---

### Post by heimo on 2007-08-23
> **m_atif said:**
> Can anyone through some light?:confused:

Is this behaviour consistent if run from another computer? Is there any firewall software running on those computers? It's possible to block ICMP (which ping uses) packets in firewall.

---

### Post by m_atif on 2007-08-23
Thanks for the reply. 
I have tried leaving the ping for more than 5 mins... no coming back. there is no firewall present in the setup. I am using a switch (layer 2). 
can you guide me how to start trouble shooting the problem. strace ping xxx.xx.xx.xx isnot much useful here.

---

### Post by m_atif on 2007-08-23
Anther thing.. the computers this specific workstation cannot ping can be reached by all the other workstations. I can ping them from other workstations, even ssh to them. 
Its like some of the workstations donot want to communicate with this specific workstation. Others do comunicate with ease. 
I am hell confused now.

---

### Post by m_atif on 2007-08-23
okay... I think one of the problems is switch is running two subnets at the same time. Although these machines have same subnet. VLAN is not used, can it be due to some sort of confusion?

---

### Post by heimo on 2007-08-23
> **m_atif said:**
> okay... I think one of the problems is switch is running two subnets at the same time. Although these machines have same subnet. VLAN is not used, can it be due to some sort of confusion?

Don't know, but I know how I would try to diagnose it. Run wireshark on both ends while pinging. Of course, also check that subnet masks are correctly set.

EDIT: Erhm.. As we're on Absolute Beginner forum (I think this is quite advanced topic though) - let's add that WireShark is protocol analyzer available at least for Linux OS and Windows. On Ubuntu, it's in repositories. And here's link to its homepage:
[http://www.wireshark.org/](http://www.wireshark.org/)

---

### Post by m_atif on 2007-08-23
thanks for the links... btw is there any command line based network/protocol analyzer? Not using GTK stuff?

---

### Post by heimo on 2007-08-23
> **m_atif said:**
> thanks for the links... btw is there any command line based network/protocol analyzer? Not using GTK stuff?

I don't know any as good as WireShark, but there's tcpdump...
[http://www.tcpdump.org/tcpdump_man.html](http://www.tcpdump.org/tcpdump_man.html)

---

### Post by m_atif on 2007-08-24
Solved. Thanks to tcpdump, The issue was indeed having two subnets on one switch. Unfortunatly for one of the IP address 192.168.x.y was equal to 192.168.z.y. The ARP was getting answer from x.y insead of z.y.
To cut short, I used VLAN to solve the issue. Thanks for all the help and support.

---

