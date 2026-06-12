---
title: "Internet acces"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by frogaroo on 2005-11-12
I have installed Ubuntu 5.04 on my 2nd pc (intel Pentium4 1.5ghz 256MB)

The install went ok but can't connect to internet I have an AdSL connection with a modem router and my first pc running on windows xp connected to it too (and running well accessing the net). All lights on modem are saying it's working ok ( port 1 &2 plus ADSL).

Can I do thet have 2 pcs with different OS connecting through the same modem !:confused:  If yes please help!

---

### Post by grim918 on 2005-11-12
i had that problem when i first tried to install some other linux distro. for some reason it would install with a different default ip address. you should check your ip address on the linux box and see if it falls within the ip range of your windows box.

---

### Post by xequence on 2005-11-12
For me, when I install ubuntu I have to go to connection settings or something and activate eth0.

---

### Post by guipipia on 2005-11-13
I would ensure that your ISP has your modem configured to give out more than 1 IP address (meaning more than 1 computer connected to your Internet connection).  Some ISPs (Internet Service Providers) configure their modems to allow one single computer to connect to the internet and bind them to the MAC address of your PC and when you try to connect another computer it will not get an IP address via DHCP.

---

