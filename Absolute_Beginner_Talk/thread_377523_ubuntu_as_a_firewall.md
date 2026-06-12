---
title: "ubuntu as a firewall"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Garry_cody on 2007-03-06
Can ubuntu be setup as a firewall. Is there other software needed:popcorn:

---

### Post by frodon on 2007-03-06
Yes, you already ahve a powerfull firewall incuded in the kernel like this for all 2.4 and 2.6 linux kernel series.

Just use iptables or a frontend of iptables (like firestarter for example) to configure your firewall.

---

### Post by Garry_cody on 2007-03-06
where do I get firestarter from?:popcorn:

---

### Post by frodon on 2007-03-06
It's in the repositories so you can install it with synaptic or just apt-get if you wish.

If you don't know how to install software in ubuntu read this :
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Garry_cody on 2007-03-06
How many network cards do you need to setup the firewall

---

### Post by frodon on 2007-03-06
> **Garry_cody said:**
> How many network cards do you need to setup the firewallSorry but i don't get the sense of your question, could you explain a little bit what you are trying to do ?

---

### Post by Garry_cody on 2007-03-06
I want to setup a firewall for a local network. As well as running a DMZ Zone for a email server. do I need a card for each connection.

---

### Post by Village on 2007-03-06
Just so I understand, Linux already has a firewall, which will block all the unwanted attacks, etc, however if you want you can install something like Firestarter and then you get to see them attacking and being blocked. 

I might give Firestarter a go and if it is diverting me from my work I can just take it off as there will still be a firewall in place?

Village

---

### Post by Garry_cody on 2007-03-06
Where do I get firestarter from? Thank you for your help

---

### Post by frodon on 2007-03-06
In this case yes you need 2 cards.

The question after this is do you have a router behind your ubuntu firewall or do wish your ubuntu box to be the router as well ?

Some good reading :
[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)
[http://doc.gwos.org/index.php/SetupUbuntuAsRouter](http://doc.gwos.org/index.php/SetupUbuntuAsRouter)

---

### Post by frodon on 2007-03-06
> **Village said:**
> Just so I understand, Linux already has a firewall, which will block all the unwanted attacks, etc, however if you want you can install something like Firestarter and then you get to see them attacking and being blocked. 

I might give Firestarter a go and if it is diverting me from my work I can just take it off as there will still be a firewall in place?

VillageIf you want to see if you have some firewall rules set just run a "sudo iptables -L" and see if there's some rules defined.
By default i don't think that there's any rules in the firewall but there's no particular risk and no need of a firewall under linux when you don't run services it's more a question of peace of mind.
kernel 
If you want to understand better, netfilter is the name of the firewal embedded in all the 2.4 and 2.6 kernel series like i said before and the most common language to configure netfilter is iptables then firestarter is an iptables frontend which allow you to set an iptables script in 3 clicks. When you install firetarter and start it it configures some iptables rules according to the choices you made in the interface then when you choose to desactivate the firewall in the firestarter interface it removes all the iptables rules which i think is the default behaviour on a fresh ubuntu install but i'm not sure of this.

---

### Post by Village on 2007-03-06
Well I've put Firestarter on, and its already had nearly 100 hits. It is taking up a bit of space on my taskbar, and so I might remove it later. But as you said I should still have a firewall anyway. Even though most of the attacks are for MS Win. 

Thanks

---

### Post by compmodder26 on 2007-03-06
> **Village said:**
> Well I've put Firestarter on, and its already had nearly 100 hits. It is taking up a bit of space on my taskbar, and so I might remove it later. But as you said I should still have a firewall anyway. Even though most of the attacks are for MS Win. 

Thanks

Since firestarter is only a frontend for iptables, you only need to have it open when you want to make changes.  Just close it, no need to uninstall.

---

### Post by frodon on 2007-03-06
Be careful the firestarter log is often misleading, it is not because you see something that you get attacked.

Anyway if you are interested by firewalling you can set a more efficient firewall writting yourself you own firewall script, you can read this guide i wrote on the topic :
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by Village on 2007-03-06
I think its fair to say that if I tried to write anything myself there would be more problems.

I'll keep firestarter on my machine, just not have it running on my taskbar. That should still provide cover and not use any of my valuable screen space. 

Thanks though.

---

