---
title: "how do I control my firewall?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by buyj3llo on 2005-12-10
okay, I'm trying to get a p2p program called "aMule" to work. But my firewall is stoping me from recieving files. I didn't even  realize I had a firewall so i'm geussing that umbuntu has a deafult one. So now I wanna know how to get access to the firewall so I can open up some ports on it. If turning the firewall off alltogether would be easier than I could do that too. So, does anybody know how I can get to my firewall?:???:

---

### Post by towsonu2003 on 2005-12-10
unless you installed a gui front end like firestarter or guarddog (or set up iptables yourself), you do not have a firewall in a default ubuntu install... your ISP (mine does) or your router may be blocking the ports...

---

### Post by buyj3llo on 2005-12-10
is there anyway i can turn it off?

---

### Post by towsonu2003 on 2005-12-10
[QUOTE=buyj3llo]is there anyway i can turn it off?[/QUOTE]

Firewall? you don't have it if you did not set it up using firestarter or guarddog or iptables -> no

ISP -> no

router -> have no idea sorry :( you might wanna wait for a reply from someone else on this (more experienced than I am on routers and networking)

---

### Post by chajuram on 2005-12-10
Hi,

I am not sure if I can help. But this is what I do. 

My router (netgear) has a firewall. 

To access it I have to type 192.168.1.1 in firefox addressbar. Some routers have the address 192.168.0.1. You will need a login and password. Once you login there should be a place to forward ports. 

I am not sure what exactly aMule does but for a BitTorrent client you will need to open ports 6881 through 6889. 

If you don't have a router then that is a different story and I cannot help you with that. 

Chajuram.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=buyj3llo]okay, I'm trying to get a p2p program called "aMule" to work. But my firewall is stoping me from recieving files. I didn't even  realize I had a firewall so i'm geussing that umbuntu has a deafult one. So now I wanna know how to get access to the firewall so I can open up some ports on it. If turning the firewall off alltogether would be easier than I could do that too. So, does anybody know how I can get to my firewall?:???:[/QUOTE]
Open a terminal and type:
```

$ sudo iptables -nL

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
If your output looks like the above, your computer's firewall is not blocking anything-- it is accepting all traffic.

---

### Post by buyj3llo on 2005-12-11
I typed it into the terminal and I got the same response back

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 
```

---

### Post by buyj3llo on 2005-12-11
> To access it I have to type 192.168.1.1 in firefox addressbar. Some routers have the address 192.168.0.1. 

yea, Mine has a different IP adress. it's from a company called westell.

---

### Post by chajuram on 2005-12-13
Hi,

Then you have to look at the manual and log into the configuration location. There you will have an option of forwarding ports. Next, read up aMule docs and find what ports it uses and open the correspodning ports on your router. 

Chajuram.

---

