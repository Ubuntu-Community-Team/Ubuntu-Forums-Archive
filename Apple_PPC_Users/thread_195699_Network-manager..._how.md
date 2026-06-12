---
title: "Network-manager... how?"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by calum on 2006-06-13
Anyone have network-manager working on Dapper/PPC?  All it ever does is tell me I have no connection, even though I have several set up in /etc/network/interfaces (and regularly switch between them manually).

Somebody told me I actually have to comment everything out in /etc/network/interfaces to get it to work, which I haven't tried yet... is that true, and if so, where does it tell you this because I can't find it in any docs or the manpages?  (If it is true, I'm not sure I'd want to use it anyway, as apps shouldn't be abusing standard configuration files like that IMHO.)

---

### Post by plexi50 on 2006-06-13
I don't use a Mac, but I assume the basics would be the same. Follow the instructions to comment out and disable your configured connections. Network manager will not run if you have connections preconfigured. It wants to do the work for you. After I did that, the icon came up on the taskbar and takes over. You will have to enter a keyring password for the connections that are encrypted, and it will prompt you each time for that password, which is kinda tedious, but may be fixed in the next release.

---

