---
title: "No Connection"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Nashy on 2007-11-09
Hey All.

Just installed Ubuntu, and I can't connect to the Net.

In Admin > Network I have my Wireless connection showing up.

In Properties I have:

Network Name (Found my router)
Password Type : WEP key (ascii) (Mines a 10 digit number)
Network Password: Filled In

Config:  Static
IP: 192.168.2.10
Subnet:  255.255.255.0
Gateway: 192.168.2.1 (Router)


When I go to Network Tools, under eth1 it shows Transmitted 3.3KiB, and Rec 84.

Link Speed is 54MB so I assume I'm looking at my wireless.

Any ideas on how to get it working?

I'm on a Toshiba M70.

---

### Post by intelligentfool on 2007-11-09
if you go to the terminal and type "ping 192.168.2.1" do you get replies? 

if so, try 'ping [www.google.com](www.google.com)'

if you cant ping the gateway, then something is up with the connection on your pc. if you can ping the gateway, but not google, try either power cycling the router, or pointing your browser to that IP (192.168.2.1) and go to "status".... see if it has a "WAN" area, it should have an address. if not, look around for a "DHCP Release" & "DHCP Renew" button to try to get a WAN ip address and DNS server addresses.

hope that helps :)

---

### Post by Nashy on 2007-11-09
No Good.

No Ping to router, (Dest Host Unreach) on Static.

DHCP says Network UnReachable

Power cycled, with no avail.

---

### Post by Nashy on 2007-11-09
Anyone able to help further?

---

### Post by intelligentfool on 2007-11-09
if you cant ping the gateway, then are you positive your connected to the network? also, is there a reason why your IP is set to static? try changing it to DHCP... your ip and the router's are in the same subnet, but something funky is going on. you should at least be able to ping the gateway, even if you cant get out to the net.

i know on alot of routers, they are set for DHCP, with the range starting at .100 (so, 192.168.2.100, .101, .102, etc). if your IP is outside of that range, it could be dropping packets because it views it as an invalid address.

edit: now that i think about it more, this cant really be a static/dhcp and/or addressing thing, it has to be a wireless issue. try playing around with ascii vs hex key's on your machine. i'm thinking the router is set for one, and the pc is set for the other.

---

### Post by Nashy on 2007-11-10
She's all good now thanks.  Turns out I had the WEP settings wrong.  I changed it to 128 and away she went.

Sorry to bother you :-)

---

### Post by intelligentfool on 2007-11-10
awesome. glad i could help :)

---

