---
title: "static ip address thing?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by millatoe on 2007-02-17
ok iam really confused about this static ip thing 

iam trying to follow the directions at this website but not sure exactly what iam doing wrong or if iam doing anything wrong [http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

iam not 100% sure if i need to change the settings according to my network settings as they seem to suitable but again iam not 100% sure ((some clarification would ease my mind)see screenshots)

anyway i went ahead with these settings and restarted the network and this is what happened

alex@alex-desktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:61:e3:b9:8b
Sending on   LPF/eth0/00:0d:61:e3:b9:8b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:61:e3:b9:8b
Sending on   LPF/eth0/00:0d:61:e3:b9:8b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.64 -- renewal in 32822 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/D](http://www.isc.org/products/D)


do i have a static ip now???

as you've probably guessed i havent got a clue what iam doing but iam pretty sure i did something wrong but i dont know what..i went to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) and my ip is the same as it was earlier and also different to anything that appears when i do ifconfig, is that normal?

what i need is someone to tell me what iam doing wrong and how to do it right, coz i cant figure it out


[http://www.ubuntuforums.org/attachment.php?attachmentid=25551&stc=1&d=1171756604](http://www.ubuntuforums.org/attachment.php?attachmentid=25551&stc=1&d=1171756604)

---

### Post by solar george on 2007-02-17
What you have is an ip address that has been assigned to you via DHCP - a dynamic IP.

Why do you want a static IP?

If you connect directly to your isp - i.e not through a router then the isp will have given you that address.

The address that is shown on [http://whatismyipaddress.com/]("http://whatismyipaddress.com/") will be the address of your isp's gateway.
I will try to explain how this works below.

_YOUR COMPUTER_
Has an address on the isp's network e.g 192.168.164
_Your ISP_
Has an address on the internet.
When you access a site the request appears to have come from the isp's address. This is the one shown on whatmyipaddress.
The address that you see in ifconfig is your address on your isp's network.

Hope this makes a little sense.
You should not normally need a static IP - DHCP will work fine.

P.S. If you want to change your network settings go to the 'networking' option in your system menu - it has an easy to use graphical front end.

---

### Post by jonathan.lees on 2007-02-17
If your current IP address is working, do you need a static address? The IP address that is shown to you at [http://whatismyipaddress.com](http://whatismyipaddress.com) is your internet address which will be your router or modem and hence it's different from your computer IP address.

---

### Post by Stephen Howard on 2007-02-17
*> i went to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) and my ip is the same as it was earlier...*That site is only reporting your internet address which is the IP-address assigned by your ISP.  Only your ISP can change that.  Think of that as your ISP-gateway onto the internet.

The dhcp server settings you are playing with only control the IP-addresses on your LAN.  That is entirely your domain, and you can assign any IP-addresses that you want.  They are not seen outside of your LAN.  That said, there are some standards that are best adhered to.

I have some questions for you...
[LIST=1]
[*]Is your LAN working now?  For instance, can you ping other devices on the LAN, can you ping/browse to sites on the internet?

[*]Why do you want static rather than dynamic IP-addresses on your LAN?  What is it you are trying to achieve?

[*]How many IP-addresses do you need?  How many devices are on the LAN?
[/LIST]

---

### Post by millatoe on 2007-02-17
apparently i need a static ip adress to forward ports which iis something i  need to do

---

### Post by millatoe on 2007-02-17
ok really confused now. i thought i needed a static ip to forward a port which i need to do in order to get torrents dowloading as fast as they did in windows, i cant survive on 5 kbs and only a few seeds, 

 can i get good downloads with dhcp?
i have a speedtouch 585 modem is that not a router aswell?
 in reply to stephen howard; 

1; yes 
2; to forward ports
3; theres only one pc here

in reply to solar:

i understand that now, cheers
but iam still not sure what to put in properties in networking ( in reply to the ps)

---

### Post by Daveth on 2007-02-17
have a look at

[http://portforward.com/](http://portforward.com/)

---

### Post by millatoe on 2007-02-17
i spent all day at that site:(

it doesnt say how to get static ip for linux

---

### Post by Daveth on 2007-02-17
ok, then what about

[http://corz.org/comms/hardware/router/static.ip.address.php](http://corz.org/comms/hardware/router/static.ip.address.php)

though written to hack an ethernet router, it is quite clear about the arcane world of networking, and explains about static ips, port forwarding etc etc. 
Time for bed now!

---

### Post by millatoe on 2007-02-17
been on that site aswell, they dont seem to know alot about linux (too much guessing and maybies)

---

### Post by Stephen Howard on 2007-02-17
If you only have one PC on your lan, then the router will likely keep leasing it the same IP number.  In which case you do effectively have a defacto static-IP address and therefore won't need to make any changes.

That said, there is another way to give you the benefits of dynamic IP leasing and the benefit of forwarding.  Log into your router and find the page where the dhcp-server is configured, somewhere on or near that page most modern routers will have an option that lets you assign a static IP based on the unique MAC address of the PC's ethernet card.  Fill in the appropriate details and you'll have a guaranteed static IP.

---

### Post by Stephen Howard on 2007-02-17
oh, when filling in the MAC line on your router, make sure that you choose an IP number that is outside the range the dhcp-server can issue.

---

