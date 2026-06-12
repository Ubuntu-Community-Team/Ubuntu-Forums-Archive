---
title: "new ubuntu system, need a firewall? or spyware sweeper?"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by hobnobsandtea on 2005-12-12
as the thread states, do i need a spyware prog, or firewall, or anti virus prog?

---

### Post by e2k on 2005-12-12
You can forget about spyware, as far as I know, they don't exist on this side.. ;)
When it comes to firewalls though, you could use iptables, but I wouldn't say you necessary need one.. I've used linux for about a year now without any firewalls, and to my knowledge I've been safe from hackers..

---

### Post by olieviya on 2005-12-12
As far as I know, not really.

---

### Post by earobinson on 2005-12-12
Not really,
Firewals are available, firestarter is one of the best IMO
Spyware, I read a thread the otherday that clamed armorK was spyware but there is no spyware like in windows.
Viruese, there are programs to scan for windows viruses, You would install these on a linux box that was a email server for example, but there are very few viruses for linux and when a linux virus is made the security hole that let the virus get on the computer in the first place is removed so there is no need for an anti virus.

---

### Post by hobnobsandtea on 2005-12-12
I love linux !

---

### Post by ninotob on 2005-12-12
I just want to reiterate the suggestion for "**firestarter**" as a firewall.  It has a wizard that works and is very easy to setup.  Manually messing with iptables is going to be hard and confusing.  Best get your feet wet first.

To install firestarter, you will have to activate some repositories in Synaptic in addition to those enabled by a base install.  I'm not at any of my ubuntu machines, so I can't recall exactly which one, but just go the repositories popup from synaptic, tell it to show you the disabled repositories, and enable/disable until a search in synaptic shows firestarter.

---

### Post by Biased turkey on 2005-12-12
[QUOTE=hobnobsandtea]as the thread states, do i need a spyware prog, or firewall, or anti virus prog?[/QUOTE]

If your system is the only one ( No local network ) connected to the internet, you don't need any firewall.

---

### Post by earobinson on 2005-12-12
[QUOTE=hobnobsandtea]I love linux ![/QUOTE]
me 2
I run without ne firewall AV or spyware detection and i have been fine.

---

### Post by jwd45244 on 2005-12-12
Firestarter is NOT a firewall. It provides a GUI-based means of manipulating iptables commands.  iptables is a tool to change the rules in the network filter part of linux.  the netfilter rules can perform firewall tasks among many others.

The bigger question is do I need to change the Ubuntu-supplied rules?  The sort answer is that if you are running a server maybe if you are running a desktop probbably not.

---

### Post by earobinson on 2005-12-12
> Firestarter is an Open Source visual firewall program. The software aims to combine ease of use with powerful features, therefore serving both Linux desktop users and system administrators.

We strongly believe that your job is to make the high level security policy decisions and ours is to take care of the underlying details. This is a departure from your typical Linux firewall, which has traditionally required arcane implementation specific knowledge. 
[http://www.fs-security.com/docs/introduction.php](http://www.fs-security.com/docs/introduction.php)

---

