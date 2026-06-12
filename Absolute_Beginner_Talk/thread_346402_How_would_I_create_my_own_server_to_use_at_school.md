---
title: "How would I create my own server to use at school?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by firezip on 2007-01-25
Hello there Ubuntu Gurus,

I just have a quick question to ask. I wish to set my home PC up as a server so that I can use it as a proxy server (phproxy) . I was wondering which scripts I should download. Some things I wanted on my server setup are 
[LIST]
[*]PHP Support
[*]HTTPS
[*]Apache
[*]Zpanel for management
[/LIST]

I've also heard that people reccommend the XFCE enviroment for resource management.

Computer Specs.
Pentium D 2.8ghz
1gb Kingston Hyper-X ram
500 watt psu
160gb HD
Nvidia 7600gt
[B]
Linksys Router[/B]

Installed OS's:
Ubuntu 6.10
Windows XP

Than you for your help :)

---

### Post by Jussi Kukkonen on 2007-01-25
Unless you really want phproxy, I'd suggest using something from the repositories -- you don't need all of the pieces of software you mentioned to run a proxy...

Take a look at e.g. tinyproxy if you want small size or privoxy for privacy features. No need for php or apache, just install ssh-server if you really want access from outside (you can still run graphical apps if you use "X forwarding").


EDIT: I just noticed that you said that apache, php et al were something you wanted, not something needed for the proxy software. So don't mind my comments. But if you are new to those softwares, do take the time to get familiar with them -- apache and PHP are easy to setup insecurely...

---

### Post by TehMark on 2007-01-25
If you just need a proxy and have a windows box around install psiphon on it.  I don't think it gets much ezier

[http://psiphon.civisec.org/](http://psiphon.civisec.org/)

---

### Post by firezip on 2007-01-25
Thanks for the links and tips :)

---

