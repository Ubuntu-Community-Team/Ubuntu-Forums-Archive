---
title: "Port Forwarding to Ubuntu Server from ICF"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by CombatGod on 2006-09-07
Ok well. I have a strange problem and I've been looking for a solution for several days now and would appreciate a nudge in the right direction.

I'm running ISPConfig on my Ubuntu Server. Recently I switched from using a router to having a Windows XP run my firewall. 

However, there are no options to forward ports or have a DMZ to my Ubuntu Server.

I've been looking for firewalls with the same functions are routers but it seems like there isn't a single free distro one out there.

Please help.

---

### Post by steve.horsley on 2006-09-07
It seems to me that you have things a little backwards. Using a windows firewall to protect a Linux server? That's a bit like using scratch resistant paint on a bomb shelter.

But anyway, I know that Linux makes a great firewall and could easliy give you a DMZ, do your routing, server load balancing  and so on. Any Linux distro can do it because firewalling capabilities are built into the kernel. The firwall is called iptables, and is configured by scripts. Guarddog and guidedog might be good configuration utilities to look at - they are GUI apps that write the configuration scripts for you - you don't even realise that scripts are beng used behind the scenes. Load balancing - I can't remember offhand how to do that but I know you can. And you only need a low-end PC to run it on.

---

### Post by CombatGod on 2006-09-07
Well the reason my other PC is the one using the firewall is mainly because I'm lazy and have no intention to move the PCs around. The cable modem and server are on separate floors. 

I was just wondering if there is any available software the has the same functionality as a router for windows.

Also, I do use the linux firewall on the server. 

I would prefer not to use the linux server itself as the firewall and server at once because my other computers need many ports open and I would prefer to keep as many ports closed going through my server. 

It also makes monitoring traffic on my server much easier because it's on a separate firewall.

---

### Post by YeahBuntu on 2006-09-08
I do not know for sure if these softwares have the capability your looking for but I think your looking for a program like SMoothwall or ClarkConnect...

smoothwall.org .. clarkconnect.com

---

