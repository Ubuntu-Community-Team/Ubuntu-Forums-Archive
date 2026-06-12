---
title: "server in vmware"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-06-08
I noticed that each vmware player has its own ip address. If i wanted to install xp in vmware in ubuntu, and server 2003 in another player. Would i be able to use the server as a dns, dhcp etc server and a domain controller and log into the domain w/ the player running xp?

---

### Post by dmfield on 2007-06-08
Simple answer, yes.. I used Bridged networking and do exactly that, as far as the rest of the Lan is concerned i have 3 Pc's running, 2 Windows and an Ubuntu one, in reality, its a jam packed memory hungry beast running 2 VM servers..

---

### Post by jeff00z28 on 2007-06-11
thats awesome i was using a server and a kvm switch but now ill set it up that way so i can just use one computer. I have 2gb of ram so i figured id split that up. I could get another 2gb if it wasnt enough but that would be sweet having an active directory network all on one computer lol

---

### Post by jeff00z28 on 2007-06-11
this is obviously not a big network just my 3 computers. im just using it to study for mcse

---

### Post by veloce on 2007-06-14
> **jeff00z28 said:**
> thats awesome i was using a server and a kvm switch but now ill set it up that way so i can just use one computer. I have 2gb of ram so i figured id split that up. I could get another 2gb if it wasnt enough but that would be sweet having an active directory network all on one computer lol

If you are running multiple vms, you might want to consider switching to vmware server.  Under Ubuntu it runs multiple machines very well.  I have up to three vms running on my laptop.  I set up an ipcop vm to do the dhcp and dns (and limit access from the vms to the work network).  It's brilliant.

---

