---
title: "Trouble with my Wifi Card"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by mindkiller on 2006-07-28
Hi

I have a Dell Inspiron 6400 with a Intel Pro Wireless Card and I have the following question about configuring it.

When I start my Kubuntu I have to run the Wireless assistant to select my home Wireless LAN to connect to the internet. I have selected a automatic conection in the KDE control panel, but it doesn't connect automatically at the start of KDE.

I want it to connect automatically to a previously selected Wifi net, but i don't know how it must be done. If anybody knows it, please answer me.

Thank you.

---

### Post by OpsVentus on 2006-07-28
knetworkmanager kan do this for you

---

### Post by mindkiller on 2006-07-28
Thank you for the answer, but i have tried knetworkmanager and when i run it appears the following message:

"NetworkManager is disconnected"

I ran NetworkManager in a shell and restart knetworkmanager and nothing happened.

When i click on the "show networks" option in the knetworkmanager panel, no network is shown.

I don't think the problem is on the wireless card 'cause it works using wireless assistan, but i don't want to configure it on every session.

If anybody knows how to solve the problem, please answer me.

Thank you.

---

### Post by OpsVentus on 2006-07-28
You can put your network in "/etc/network/interfaces"

Something like:
auto eth1
iface eth1 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid COOLNETWORKNAME

or:
auto eth1
iface eth1 inet dhcp
wireless-essid COOLNETWORKNAME

---

