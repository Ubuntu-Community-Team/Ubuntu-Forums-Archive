---
title: "Do I need a firewall if I have a router with....."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ginnie6 on 2007-02-13
nat firewall enabled?

---

### Post by etank on 2007-02-13
A firewall on the host is probably not needed. If you want one though try installing firestarter. Here is a description:

> Firestarter is a complete firewall tool for Linux machines. It features an easy to use firewall wizard to quickly create a firewall. Using the program you can then open and close ports with a few clicks, or stealth your machine giving access only to a select few. The real-time hit monitor shows attackers probing your machine.

---

### Post by oilchangeguy on 2007-02-13
you shouldn't. and ubuntu comes with a built in firewall. firestarter is just a control panel that allows you to configure (not needed) the existing firewall.

---

### Post by r4ik on 2007-02-13
Not really but if it makes you feel safe ( does that to me )
by all means do.

---

### Post by MCSE_Crossover on 2007-02-13
Also, keep in mind that Linux by default loads with all default public ports in a closed state. Any portscanner run on your machine should show that all ports are closed - unless you have enabled some sort of webserver or something locally.

---

### Post by MCSE_Crossover on 2007-02-13
> **oilchangeguy said:**
> you shouldn't. and ubuntu comes with a built in firewall. firestarter is just a control panel that allows you to configure (not needed) the existing firewall.

That is in reference to the native IPTABLES, right? Firestarter is just IPTABLE's front-end gui if I understand correctly...

---

### Post by dexter on 2007-02-13
> **MCSE_Crossover said:**
> That is in reference to the native IPTABLES, right? Firestarter is just IPTABLE's front-end gui if I understand correctly...

That's what i've read yes.

---

### Post by r4ik on 2007-02-13
Try Shields UP ! to scan you're machine.

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

