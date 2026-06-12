---
title: "azureus help"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mbt12 on 2007-08-22
Is there anyone that can help me with setting this up.  It says i have a NAT error. I think I need to set up a static ip to do the port forwarding.  If we could use aim or msn that would go much quicker. thanks

---

### Post by swoll1980 on 2007-08-22
look in the configurations see if theres a plugin that forwards ports to your router

---

### Post by mbt12 on 2007-08-22
I dont see anything in there.

---

### Post by Ice_Dragon on 2007-08-22
Try this.
[http://www.portforward.com/](http://www.portforward.com/)

---

### Post by mbt12 on 2007-08-22
It does not show how to set up a static ip for ubuntu.  Is there anywhere that shows this?

---

### Post by irish_flu on 2007-08-22
> **mbt12 said:**
> It does not show how to set up a static ip for ubuntu.  Is there anywhere that shows this?

Go to System ---> Administration ---> Network, click on the appropriate connection, and change "automatic" to "static IP".

Your router may or may not be happy with this, you'll have to find instructions for telling it to not use that IP when it's handing out DHCP addresses.

---

### Post by mbt12 on 2007-08-22
If I go there I have to enter all the information in and I don't know what to put there.  How do I figure that out?

---

### Post by SpiritIsReality on 2007-08-22
some bits
in a command terminal apps->accs->terminal
or press and hold Alt,then press 2, type in gnome-terminal, (or konsole)
sudo ifconfig -a
using a router,
you could have your router assign a static dhcp to your computer,
see the router manual, and access the router by typing it's ip address
into a web browser address bar...then leave your eth connection configured
for dhcp.

you could tell your router not to give out an ip address range and then set your
eth connection to a static ip in that range.

links
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
click on linux topics, or scroll down page.
[http://aboutdebian.com/](http://aboutdebian.com/)
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[http://www.firewall.cx/](http://www.firewall.cx/)
[http://openwrt.org/](http://openwrt.org/)
[http://www.google.com/search?q=linux+networking&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux+networking&ie=UTF-8&oe=UTF-8)

irish_flu pardon, my bad

---

### Post by irish_flu on 2007-08-22
> **mbt12 said:**
> If I go there I have to enter all the information in and I don't know what to put there.  How do I figure that out?

That's all going to be dependent on the configuration of your router.  If it has a web administration page, snoop around it for a bit and I bet it'll be self-explanatory.

---

### Post by AndyCooll on 2007-08-22
> **mbt12 said:**
> If I go there I have to enter all the information in and I don't know what to put there.  How do I figure that out?

System > Administration > Network

Choose the "Properties" of your connection and under configuration select "Static IP address". Now input a static IP address. Typically something like 192.168.2.2 (or any other number to 100 that follows). Your subnet mask is more than likely going to be 255.255.255.0 and your gateway address is the address of your router (usually something like 192.168.2.1)

On your router, there will probably be a section which says start dishing out IP addresses beginning with 192.168.2.xx. Manually input 11 or 21 or something like that. That way the first numbers will be reserved (and can be used for fixed IP addresses).

I too had problems with this with Azureus. And once I'd fixed the IP address of my box I then had to forward the port from my router.

:cool:

---

### Post by splintercellguy on 2007-08-22
Some routers can forward based on host name I think.

---

### Post by mbt12 on 2007-08-22
Thanks for the help, but I don't think I will be able to do this.  I don't know which address to put in where and I will most likely just screw it up.

---

### Post by A$h X on 2007-08-22
It's not hard trust me. Goto applications > accessories > terminal then type route -n
Copy the stuff that comes up and paste it here. Also what router are you using? That way we can help if your router needs some extra details (but it probably doesn't so don't worry :))

---

### Post by mbt12 on 2007-08-22
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

I have a linksys WRT54G router.

Also, will this effect other users in the house?

---

### Post by A$h X on 2007-08-22
Your in luck my friend. I have (almost) the same router as you. :KS

Okay first the router stuff: 

Type the following into the firefox address bar: 192.168.1.1

Now you should know your router ID/password. If you haven't changed it then it will be username: admin and password: admin

Now on the first page you'll see a section where it says "local IP address" and subnet mask
Make sure it's says
local IP address : 192.168.1.1
subnet mask: 255.255.255.0

underneath that it make sure DHCP server is set to "Enable"

then make sure the "starting IP address" is set to 192.168.1.2

click "save settings"

Now out of firefox and back in ubuntu click the network icon on the top right (next the speaker icon), click "manual configuration" and it should say "wired connection". 
click it and next to that click properties

Now select "static IP" in configuration
enter 192.168.1.2 in IP address
enter 255.255.255.0 in subnet mask
enter 192.168.1.1 in gateway address

click OK and voila your done! 
Regarding the other computers in your house... all you have to do is give each machine a DIFFERENT IP address- just change the last digit of the IP address... so yours is 192.168.1.2 the next machine will be 192.168.1.3 etc 
The subnet and gateway are the same for every machine. 
If they are windows machines it's very easy to do this as well. Ask if you have anymore questions. Good luck! ;)

---

### Post by mbt12 on 2007-08-22
Thank you very much, I am pretty sure it worked. Now I just have to test it out.

---

### Post by mbt12 on 2007-08-22
It says DHT firewalled, how do I fix that.

---

### Post by A$h X on 2007-08-22
Hey hold on! You wanted to use Azureus right? Just one mroe thing to do:
Go into your router setup like before, then click the tab that says "applications and gaming" along the top.
There it should have a table called "port range". 
In there goto the boxes called "start and "end" and enter 65000.
Make sure the "protocol" is set to "both".
Enter your IP address in the address box, and make sure the "enable" box is ticked.

Now goto azureus and options > listening port. Enter 65000 and click "test" it should test it out and say OK.
Phew! NOW your all set to get high speed d/l's on your torrents. :)

---

### Post by mbt12 on 2007-08-22
Thanks, I already did that thanks to the port forwarding website.  It is working now except for that DHT thing

---

### Post by A$h X on 2007-08-22
Sometimes azureus takes a while to realize everything is working okay- d/l a big torrent and give it 10 mins and you should get green lights and everything working a-okay.

---

### Post by mbt12 on 2007-08-22
No green light yet, but it is downloading fine.  I am getting speeds of like 400kB/s.  I don't know if its good or not but it seems pretty fast.

---

