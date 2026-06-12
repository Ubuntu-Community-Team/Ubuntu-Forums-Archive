---
title: "Samba? NFS? NFSv4?"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by Knyven on 2005-09-22
Im confused on what to use :? 

I have 2 Ubuntu PC. And i want to link them, and i cannot locate each other in the Places>Network Servers. I want it to enable each other to browse each other. What is Samba, NFS and NFSv4 what should i use between those 3?

---

### Post by drogoh on 2005-09-22
First of all, rule out Samba.  You don't need Samba unless you're working in a Windows environment and want to play nicely with Windows machines.

Second of all, NFS simply means "network file system".  See [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/) for more details but these are not "Ubuntu-ified" instructions.

To be honest, I would choose plain "NFS" and not v4.  My reason for saying this is I've not tried v4 as of yet.

Hope this helps.

---

