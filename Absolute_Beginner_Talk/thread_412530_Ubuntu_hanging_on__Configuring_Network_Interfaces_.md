---
title: "Ubuntu hanging on * Configuring Network Interfaces on startup, not booting"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Auraya on 2007-04-18
I have tried installing ndiwrapper a number of times and every time I do so (following a guide) Ubuntu works fine until I reboot. It is now not rebooting and getting stuck indefinately on *Configuring network interfaces and eventually going to a black screen. 

Im using Feisty but also tried it with Edgy at which it got stuck on * Checking file systems

Any help? Or should I just wait til Feisty is released tomorrow and try it afresh?

---

### Post by jonholio on 2007-04-19
Hi Auraya,
I have also had similar problems on my laptop which is configured to connect to a wireless network. I read somewhere (a while ago and don't recall where sorry) that editing /etc/network/interfaces and commenting out the lines for the wireless connection:

eg change:

auto eth2
iface eth2 inet dhcp

to:

#auto eth2
#iface eth2 inet dhcp

keeping in mind to replace eth2 with the valid one for your connection.
I'm not sure if this is the correct solution but it seems to work for me and leaves the network configuration up to NetworkManager :)

-Jonholio

---

