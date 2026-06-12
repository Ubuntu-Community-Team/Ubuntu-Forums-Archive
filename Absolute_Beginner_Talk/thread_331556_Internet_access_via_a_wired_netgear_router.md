---
title: "Internet access via a wired netgear router"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-01-04
Hi
i am new to linux but an experienced windows user.
I have a netgear router (wgt634) and an netgear gigabit Ethernet adapter (ga311)
I want share files to windows machines and browse the internet via the Linux box
If you could please give me some info or a How to page that would be great.

---

### Post by Jose Catre-Vandis on 2007-01-04
Assume your router is up and running, already connecting your windows boxes to the net and serving up dhcp

Assume you can connect your Ubuntu box and router together with wire/s

Does Ubuntu automatically recognise your adapter? If so you should be connected to your LAN and the internet, assuming a fairly default setup on your router. Although your adpter may be recognised, Ubuntu may not have activated your adapter, so:
System>Administration>Networking and check the settings for the "Ethernet Connection" (normally eth0)


If not recognised, you will need to identify the chipset for the adapter and find linux drivers. Being netgear this is unlikely though?

If you do a fresh installation of Ubuntu with the box already connected up to the router, Ubuntu should automatically detect and setup your ethernet connection, giving you instant internet access.

For the file sharing you are best off using samba to share files from Ubuntu> Windows and vice versa. You will need to have Fat32 partitions available to share on your Ubuntu box.
Start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba), then search the forum for samba related howtos and posts if this doesn't fit the bill.

---

### Post by G_force on 2007-01-04
`Cheers

---

### Post by Jose Catre-Vandis on 2007-01-05
And how's it going ?

---

