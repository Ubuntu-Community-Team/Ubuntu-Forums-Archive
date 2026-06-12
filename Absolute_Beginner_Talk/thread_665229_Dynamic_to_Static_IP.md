---
title: "Dynamic to Static IP"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-01-12
Specs of computer:

1.6ghz Intel Core Duo
100gb HD
2gb RAM
256MB Nvidia geforece go 7400

ubuntu Gutsy

My wireless router: Buffalo WHR-G54S

Basically we have an internet connection that is shared using the Bufallo wireless router (5 people share it). We all use DHCP to get an ip address from the router.

Basically I want to change my IP address to a static one.

I used the Static IP for Xp guide provided by portforwade.com ([http://portforward.com/networking/static-xp.htm](http://portforward.com/networking/static-xp.htm))

But of course this didn't really help.

So I want to be able to use nm-applet, to set up a location that use static IP (when I'm at home), and one location that is Roaming (for when I take my laptop to say university).

So basically I need to know all the various IP addresses and DNS and subnet mask. The problem is doing ifconfig I get the following:

eth1      Link encap:Ethernet  HWaddr 00:13:02:52:8C:10  
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe52:8c10/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:408 dropped:4573 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:12779530 (12.1 MB)  TX bytes:3823480 (3.6 MB)
          Interrupt:18 Base address:0x6000 Memory:8c000000-8c000fff 

also my router info page is giving me various other numbers:

IP Address  	86.20.XX.XXX **[different to default gateway below]**
Subnet Mask 	255.255.252.0 
Default Gateway 	86.20.XX.X (Via DHCP)
DNS1(Primary)	194.168.X.XXX (Via DHCP)
DNS2(Secondary)	194.168.X.XXX (Via DHCP)
Host Name 	XXXXX (Manual Setup)
Domain Name 	XXXXX (Via DHCP)
MTU Size 	XXXX
DHCP Server Address 	62.255.XX.XX

MAC Address 	XX:XX:XX:XX:XX:XX

LAN 	
IP Address 	192.168.11.1
Subnet Mask 	255.255.255.0
DHCP Server 	Enabled
MAC Address 	XX:XX:XX:XX:XX:XX

(sorry if it looks stupid if I blocked out things that are completely unnecessary, don't really know what most of it means!)

also when I right-click on nm-applet and click on connection information I get:


Interface: Wireless Ethernet (eth1)
Speed: 54 Mb/s 
Driver: ipw3945
IP Address: 192.168.11.3
Brooadcast Address: 192.168.11.255
Subnet Mask: 255.255.255.0
Default Route 192.168.11.1
Primary DNS: 192.168.11.1
Secondary DNS: 0.0.0.0
Hardware Address: [different to above MAC addresses]

So basicall all these numbers have got me confused and I don't understand what numbers I should put into the different boxes...any help would be appreciated! 

Also it is vital that I can switch between the static and the roaming (as this is a laptop!)

---

### Post by MobiusNZ on 2008-01-12
You'll probably have to do this switch manually. Even on windows this is the case. (well to be perfectly honest in windows you can set a static ip address to use if DHCP fails but that won't help you in this situation).

If you really don't want to switch manually, the best bet would be to have a DHCP address reservation assigned to your computer so you're guaranteed to get the same IP address every time. Note that not all routers will let you do this... but if you have a proper server dishing out IP's its easy enough

---

### Post by mikemn84 on 2008-01-12
Another option is setup your router for "static dhcp".  Which Essentially uses dhcp but then for certain mac addresses on the network, you can assign a permanent ip.  Ive set this up on my network and its pretty great.  

What you'll need to do is flash your router to a new firmware, the open source - linux based dd-wrt firmware.  It can be installed on any number of routers included the one you listed.  When doing this however, there is some risk of bricking your router in the process if you do it incorrectly.  Visit the wiki here: [http://www.dd-wrt.com/wiki/index.php/Main_Page]("http://www.dd-wrt.com/wiki/index.php/Main_Page")
 to read how to install it on your router properly and all of its benefits.  Being open-source, this firmware sports a ton of cool features apart from static dhcp, look at the tutorials section in that link  to see what is possible.

Good Luck

---

### Post by MobiusNZ on 2008-01-12
static dhcp = dhcp address reservation when reading the two previous posts ;)

---

### Post by dcstar on 2008-01-12
> **abhiroopb said:**
> 
...........
Basically I want to change my IP address to a static one.

I used the Static IP for Xp guide provided by portforwade.com ([http://portforward.com/networking/static-xp.htm](http://portforward.com/networking/static-xp.htm))

But of course this didn't really help.

So I want to be able to use nm-applet, to set up a location that use static IP (when I'm at home), and one location that is Roaming (for when I take my laptop to say university).

So basically I need to know all the various IP addresses and DNS and subnet mask. The problem is doing ifconfig I get the following:
............
So basically all these numbers have got me confused and I don't understand what numbers I should put into the different boxes...any help would be appreciated! 

Also it is vital that I can switch between the static and the roaming (as this is a laptop!)

The only important things to know for your manual settings are:

IP: 192.168.11.x (something not already used by the DHCP, choose 200 upwards to be safe)
Gateway: 192.168.11.1
DNS: 192.168.11.1
Subnet mask: 255.255.255.0

---

### Post by abhiroopb on 2008-01-12
Thanks guys....

A few things:

1. I don't mind doing it manually (providing I can figure out how to do it!!)
2. I don't want to mess around with the firmware as other people in my house use it as well, and this isn't essential so I'd rather do whatever needs to be done using my computer!
3. Again I don't want to mess around with static DHCPs on my router.

What I was looking for was what dcstar mentioned:

Basically I clicked on Manual Configuration, selected Wireless, Properties, I switch off the Enable roaming mode:

Network name (ESSID): [mynetwork name]
Password Type: WEP (i changed it today)
Network Password:
Connection Settings
Configuration: Static IP
IP Address: 192.168.11.203
Subnet Mask: 255.255.255.0
Gateway: 192.168.11.1

Then I press OK, select the DNS tab and add a DNS Servers: 192.168.11.1

Then I see two computer monitors on the top screen, instead of the usual wireless bar monitor. 

When I try and select a website, I just get "looking for..."

So, any thoughts? I'm guessing its just some of these numbers have to be different...

---

### Post by MobiusNZ on 2008-01-12
Try pinging things, like your router. Try pinging 72.14.207.99 and google.com. If the IP address works but not google.com then you've got a DNS problem

---

### Post by abhiroopb on 2008-01-13
I tried the same settings, nothing worked, tried pinging 72.14.207.99: 

```

abhiroop@Vanimo:~$ ping 72.14.207.99
connect: Network is unreachable

```

---

