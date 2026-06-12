---
title: "Best Firewall"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-22
What is the best Firewall?

---

### Post by justleen on 2008-02-22
IPtables.. its alreay installed.. There is also a GUI for it, to configure the rules, but i cant recall the name (fire somthing?)

---

### Post by dje on 2008-02-22
The GUI for iptables is firestarter:
```
sudo apt-get install firestarter
```

dje

---

### Post by miqsu on 2008-02-22
Bitfrost is one. Firestarter is simple (at least UI of it is), but I'm not sure if it's gui for iptables or not.


EDIT: dje answered to that :)

---

### Post by kpkeerthi on 2008-02-22
netfilter/iptables is already setup as firewall (yes, it is more than a firewall) in ubuntu. All the GUIs you hear for linux are just front-ends to netfilter/iptables.

---

### Post by philinux on 2008-02-22
The best firewall is in my router. :)

---

### Post by kpkeerthi on 2008-02-22
> **miqsu said:**
> Bitfrost is one. Firestarter is simple (at least UI of it is), but I'm not sure if it's gui for iptables or not.

I believe you are referring to [Bifrost]("http://bifrost.heimdalls.com/")

---

### Post by kpkeerthi on 2008-02-22
> **philinux said:**
> The best firewall is in my router. :)
+1. Software firewalls are redundant if you are behind a router.

---

### Post by dje on 2008-02-22
> **philinux said:**
> The best firewall is in my router. :)

+1

---

### Post by r4ik on 2008-02-22
Nobody seems to mention Guarddog as far as i know it can be used in Gnome to.

---

### Post by julian67 on 2008-02-22
> **kpkeerthi said:**
> netfilter/iptables is already setup as firewall (yes, it is more than a firewall) in ubuntu. All the GUIs you hear for linux are just front-ends to netfilter/iptables.

No it isn't. By default iptables in Ubuntu is completely unconfigured, it allows all traffic in all directions. If you want to check that (from a default install, or one that has had no firewall set up):

```
sudo iptables -nL
```

this will show you *all* traffic is allowed.

---

### Post by philinux on 2008-02-22
If I were still using wondoze I would have a software firewall too. With linux sudo is the protection.

---

### Post by kpkeerthi on 2008-02-22
> No it isn't. By default iptables in Ubuntu is completely unconfigured, it allows all traffic in all directions.
I didn't know that. I read somewhere that it allows all outgoing traffic and blocks all incoming by default. I'll check that when I reach home (i'm running ubuntu in a VM though). Thanks for pointing it out :)

---

### Post by northern lights on 2008-02-22
> **julian67 said:**
> No it isn't. By default iptables in Ubuntu is completely unconfigured

Fair enough, might allow everything - but it **is** there.

> **philinux said:**
> The best firewall is in my router. :)
=D>

---

### Post by julian67 on 2008-02-22
> **kpkeerthi said:**
> I didn't know that. I read somewhere that it allows all outgoing traffic and blocks all incoming by default. I'll check that when I reach home (i'm running ubuntu in a VM though). Thanks for pointing it out :)

if it did that you wouldn't be browsing the web ;-)  All traffic is permitted by default but no services are listening. It's an ok set up until you start services/daemons (samba server, p2p, web server, vnc host, ssh server, dns server, rsync daemon, dhcp server etc) and then it's not so good.

---

### Post by kpkeerthi on 2008-02-22
Do you mean if incoming traffic is blocked and outgoing allowed, then I will not be able to browse the internet? 

Not quite.

---

### Post by julian67 on 2008-02-22
> **kpkeerthi said:**
> Do you mean if incoming traffic is blocked and outgoing allowed, then I will not be able to browse the internet? 

Not quite.

If no incoming traffic is allowed you won't be browsing anything. If you mean no *unrequested* incoming traffic is allowed that's a different matter (and not how Ubuntu is set up by default) ..... to do that you need to actually *configure* iptables.

---

### Post by jeffus_il on 2008-02-22
I vote for "my router" as well. (Even better than his router)

---

### Post by webjames on 2008-02-22
For interests sake Hardy will be using UFW. here is an article about it: 
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

and some helpful usage tips:
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

i'm not sure if it would be a simple thing to do on gutsy to install ufw but i would seek advice before proceeding.

---

### Post by kpkeerthi on 2008-02-22
> **julian67 said:**
> If no incoming traffic is allowed you won't be browsing anything. If you mean no *unrequested* incoming traffic is allowed that's a different matter (and not how Ubuntu is set up by default) ..... to do that you need to actually *configure* iptables.
I agree. It has to explicity configured to allow "established" connections into the firewalled host.
Now...  for others... back on topic :)

---

