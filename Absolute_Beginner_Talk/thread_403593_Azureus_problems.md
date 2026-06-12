---
title: "Azureus problems"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by nichanson on 2007-04-07
Hi
I'm totally confused and lost as to why, when I first installed Azureus on my computer I had no NAT problem but after making a mistake and messing about with BETA versions of video cards (without knowing what I was doing) I had to reinstall Ubuntu. Now though I always get NAT problems BUT not in my root page!!! 
I hope that made sense and if anyone knows anything that could help me fix this problem I would be most greatfull.
Nic

---

### Post by lebabyg on 2007-04-07
I had a similar problem.  basically i solved it by opening up ports in Ubuntu's iptables.  Check what ports are open by:

sudo iptables -L

If this doesn't give anything then I'm pretty sure that you need to open some ports up.  I opened 6883:6884 (one for azureus the other for limewire) with 
sudo iptables -A OUTPUT -p tcp --dport 6883:6884 -j ACCEPT
sudo iptables -A OUTPUT -p udp --dport 6883:6884 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 6883:6884 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 6883:6884 -j ACCEPT
sudo iptables -A FORWARD -p udp --dport 6883:6884 -j ACCEPT
sudo iptables -A FORWARD -p tcp --dport 6883:6884 -j ACCEPT
sudo iptables-save

Now this might be overkill (!) but i'm pretty sure that it's (relatively) safe to open these ports.  This should solve your NAT problem.

---

### Post by nichanson on 2007-04-07
so far so good but as the listening port do I put: 6883 because it give me a error

---

### Post by lebabyg on 2007-04-07
Yer in Azureus use port 6883.  You can put any port you want as long as you open that in your iptables.  Also, do you use a router to connect to the internet??  Have you opened the ports in your router to correspond to the IP address that linux uses????

---

### Post by nichanson on 2007-04-07
Yer I think so but it says the following:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
is that ok?

---

### Post by d_xtremw on 2007-07-01
im reviving this thread cuz im having that same problem and i need to open up my ports as well. does anyone know how to do this?? someone told me something about port forwarding but it was o complicated and confusing and this seems alot simpler. my ports show the same things:

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination 

what does it mean and how can i use it to open ports

---

