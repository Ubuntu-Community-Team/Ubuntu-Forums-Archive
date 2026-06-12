---
title: "Connecting HH and WinXP to Debian File Server"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by loksipan on 2006-11-23
I'm venturing into the esoteric world of linux file servers, setting up  a small office network for my company.  I've sucessfully got a Debian File Server running, the only question now is how do I connect to it with my Hoary Hedgehog Ubuntu and Windows client PCs?

My network is as follows

ISP
MODEM
ROUTER
FIREWALL
HUB
3 x WinXP, 1 x Win98, 1 x HH, 1 x Debian File Server, Aficio 2022 printer

(note1 each device is connected to the device above it in the list)
(note2 the Windows machines are all in Chinese so I am flying somewhat blind until I bring an English system in to use as a reference - I'd be happy just to get the English Hoary Hedgehog unit connected at the moment in order to demonstrate capability)
(note3 the client PC and debian server all use DHCP - so I couldn't find an IP address for the server which I could use on the client)

The clients are connected to our ISP directly through HUB-Firewall-Router-Modem route, but I also want them to log onto the Debian file server as well.

In Windows I recall you can search a local network neighbourhood for a connected server - is there anything similar in Hoary?

Thanks

Stephen

UPDATE1: Tried adding the WORKGROUP name "myserver" with SYSTEM->USERS & GROUPS and setting my User setting for WORKGROUP to "myserver", then used Konqueror->GO->NETWORK FOLDERS->SAMBA SHARES but get the response "Unable to find any work groups on your local network".
UPDATE2: Tried setting the IP address of the server to 192.168.2.255 Submask 255.255.255.0 Gateway 192.168.2.1 (the IP of our router) but got the same result using the test in UPDATE1.

---

