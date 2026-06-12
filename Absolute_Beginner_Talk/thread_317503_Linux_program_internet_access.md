---
title: "Linux program internet access"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by gregorio on 2006-12-12
Well, here we go.  I've been living in the windows world for too long.  With windows, I have found that besides the firewall that the router provides, I need to use a software firewall.  Why?  I do not fear anyone gaining access to my system, rather, I find that many programs, once installed, try to access the internet.  Now, for many programs, that is fine or even necessary.  But, by using a software firewall, I can control what programs can have such access. 

Now, I do understand that as long as you use the programs in Ubuntu's repositories, one should have no worries.  But, I'm hoping that in the future, many commercially produced programs will also be available.  I'd love to see a good CAD/CAM program that is available now on windows be designed for (not just ported) Linux.  And there are many other types of software that it would be great if the company designed it for Linux.  I do truly believe that many programmers would see a great benefit for  using Linux.  But, I'm sure that is years away for now.  So, the questions is, can you control a programs access to the internet in Linux?  Can you see if it is even trying to "phone home"?

---

### Post by adaptr on 2006-12-12
> So, the questions is, can you control a programs access to the internet in Linux?
With **iptables** (a kernel component) you can control any and all access to the network.

Mind you, doing so for any given situation may not be trivial, but there are a lot of decent interfaces available (like firestarter or fwbuilder).

> Can you see if it is even trying to "phone home"?
That is quite easy, yes.
There are two tools you can use to see what any program is doing:
**netstat** will show you what kind of network connections any program has, and where to, and
**lsof** shows you any file or socket a program has open while it is running.

---

