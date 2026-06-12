---
title: "what do i need?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by edallica on 2006-06-15
hi everyone!

i would like to try out ubuntu, but i need to know how i can get on the web.

i access the web through a LAN and need to enter specific info for the IP address etc. in windows going to network connections right clicking on the connection and looking at the properties. then IP properties i get asked what the IP address, subnet mask and default gateway numbers are. as well as preffered DNS server.

are these numbers of use to me when i try to overwrite XP with ubuntu? so far i havent seen a box that allows me to type in these numbers!

cheers for any help

---

### Post by sldavid on 2006-06-15
Help me clarify your question. 

Are you asking, How do I enter my network information while installing Ubuntu over and exisiting Windows XP installation?

Once Ubuntu is installed the network settings can ge changed by going to System> Administration> Networking. When the Network Settings windows opens choose your network card and click on the properties button.

I hope this helps.

---

### Post by edallica on 2006-06-16
hey thanks for that!

sorry i wasnt clear enough.

ive loked at screenshots on how to enter your network detials and it looks like there are no field for field equivelents to the way it is in windows. what i was wondering was how do i translate the information i have for my windows setup (ip address, default gateway, etc.) into something useful for ubuntu.

thanks for any help

---

### Post by muep on 2006-06-16
It is really very simple. Have you tried the livecd?

---

### Post by muep on 2006-06-16
I took a screenshot of the network settings windows. Sorry for it is in Finnish ;)

"Kiinteä IP-osoite" stands for Static IP

the number lines are as follows:
IP address
Subnet mask
Default gateway

---

### Post by xenblend on 2006-06-16
the network config file is /etc/network/interfaces.  You can edit it with 'sudo vim nano /etc/network/interfaces'.  Under your network card (usually eth0 or similar) u should have the following fields:

auto eth0 inet static (or auto eth0 inet dhcp)
IP address 192.168.1.100 (or similar)
subnet 255.255.255.0 (sim)
gateway 192.168.1.1 (sim)
network 192.168.1.0 (sim)
broadcast 192.168.1.255 (sim)
dns-nameserver 192.168.0.1 (sim)

WIth dhcp you wont have all these options, with static you need most of them (although i think network and broadcast linux can figure out for itself usually...).

do a 'man interfaces' for more info.

---

### Post by jasonmatt5 on 2006-06-16
Did you figure it out?

---

