---
title: "Ubuntu and Windows home network..."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Murxidon on 2006-11-24
I just installed Ubuntu, but I can't set up a "simple" home network between this computer and another one on my home network.
I connect with a USB Cable Modem, which Ubuntu detected automatically, and connect to the other computer with a NIC on each machine. The other computer is running Windows XP SP2, I want to be able to share my internet connection, files and a printer with the XP machine but I really have no idea how....

Please help.

---

### Post by kd_pease on 2006-11-24
Samba will do the File and Printer sharing. There's a guide on how to set it up [here]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Murxidon on 2006-11-25
Will Samba share the internet connection too?

---

### Post by louieb on 2006-11-25
There is the hard way and the easy way to share the Internet.
The hard way is to set the machine connected to the modem up as a router and DHCP server. I have never done it but know friends that have.  

The easy way is to get a router and plug the modem and both computers into it. That how my home network is set up for Internet, printer and file sharing.

I use Samba for for file and printer sharing. It kinda a pain to set up between Linux and XP. Nothing hard but both XP and Linux have to be setup for it to work.

---

### Post by Xappe on 2006-11-25
it's not that hard setting up a router box with iptables since there are many very nice frontends. 

The easy way should be to use the graphical frontend firestarter (available in the universe repos iirc) 

Another very nice way is to use shorewall (editing text files for your needs, but there is a nice documentation and good examples that do follow the package to your hdd :))

---

