---
title: "need some help with DHCP"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by ovistanciu on 2007-01-17
Hi!

I'm doing a school project about creating a network profile utility. My linux networking knowledge is kinda limited, so i have some questions:

1) How do i start/stop the DHCP client (i need the commands)?

2) Do i have to stop networking to perform changes (such as, let's say, stop the dhcp cilent, change to static IP and the adresses for the dns servers and gateway, and viceversa) ? When I restart networking, will the changes I made while it was stopped be loaded?

That's it, for now.

Thank you!

---

### Post by jvc26 on 2007-01-17
2/ when altering settings you dont have to stop the computer/router etc. you just go to system->administration->networking and select the option 'static IP' from the drop down menu from the device you are using to connect (usually eth0 or your adapter) then put in the IP, the subnet mask, the router address and then under another tab go to the DNS server and add in your DNS server addresses... then you're all ready to go, you dont need to disconnect.

Another idea - have you tried linux? It might be a good lesson and help you with your homework assignments to try a dual boot or something :)
Il

---

### Post by ovistanciu on 2007-01-17
Thank you for your interest.

In my first post I omitted a few things. I am using Ubuntu 6.10 (that's why I posted here) and I know I can do all those things from the GUI, but i need the commands to run them from my app. 

Basically, all I need to know is how to start/stop the dhcp client. I thought I would find it in /etc/init.d/ and just stop it, but it isn't there.

---

### Post by Lucardo Mamones on 2007-01-17
try ```
man dhclient"
```from the console that will control the client.

Also you might want to try to edit the "/etc/network/interfaces" and running "/etc/init.d/network restart" to have the settings take place.

I assume that if you want to disable dhcp you will also want to assign an IP manually.

---

