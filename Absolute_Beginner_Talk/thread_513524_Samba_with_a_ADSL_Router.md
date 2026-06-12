---
title: "Samba with a ADSL Router"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by celalo on 2007-07-30
Hi everyone,

I have xubuntu 7.04 installed and using samba server to share files from my xubuntu to my XP with username and password through my router. to put in a simple way, I was just typing \\192.168.1.3 to access my xubuntu machine. there is no problem so far.
But now I want to access my files from xubuntu outside from home. I mean, I have a static ip something like 88.201.xx.xx and I know I might need some port forwarding (I actually doing that for my webserver)
what shold I need to type now? \\88.201.xx.xx is not working. I learnt that samba uses the port 139 and I forwarded the port 139 to my xubuntu machine and tried \\88.201.xx.xx:139 but it was not wroking.

Thanks in advance.

---

### Post by celalo on 2007-07-30
I think I just figured it out. Actually I was doing OK, I just typed \\88.201.xx.xx and did port forwarding to 139.

Like Samba, love ubuntu :)

---

