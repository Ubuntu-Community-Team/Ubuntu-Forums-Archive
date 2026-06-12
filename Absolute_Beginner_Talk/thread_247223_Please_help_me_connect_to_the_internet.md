---
title: "Please help me connect to the internet"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by apprenti on 2006-08-30
Hi. I'm a complete beginner with Linux. I installed Ubuntu 6.06 on my pc 2 days ago, but I haven't been able to connect to the internet yet. (Firefox keeps giving a "server not found" message.) Although I've browsed others' posts on this forum, I still haven't solved my problem. I'm really eager to get familiar with Linux, and I'd be grateful for any help.

Information about my setup:

My pc is running Ubuntu 6.06 and Windows XP.
It is connected to a router via ethernet.
A Mac is also connected to the same router via ethernet.
There are no problems connecting to the internet with Windows and with the Mac.
The router is a Netgear WGR614v6, and it is connected to a Westell DSL modem.
Windows XP says that my pc has an nVidia nForce Networking Controller Driver, version 50.0.9.0

**System > Admin > Network** shows an active ethernet connection  (interface eth0)

DHCP is selected in Ubuntu Connection settings/configuration

Netgear router manager includes the following information under router status:
Internet Port: DHCP: PPPoE
LAN Port; DHCP: ON

iconfig gives the following:
eth0      Link encap:Ethernet  HWaddr 00:16:17:37:F6:EE
          inet6 addr: fe80::216:17ff:fe37:f6ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:240 (240.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)



Thanks for any help you can provide!

---

### Post by Bachstelze on 2006-08-30
Hi and welcome to Ubuntu :)

Does your router support DHCP or not ?

---

### Post by apprenti on 2006-08-30
Thanks. It's nice to be here:) 

I *believe* my router supports DHCP. The Netgear router manager indicates that DHCP is "on" for my LAN port. Also, I  found the following settings selected in Windows and MacOS, both of which successfully connect through the router:

WINDOWS
Internet Protocol (TCP/IP) Properties: Obtain an IP address automatically
Obtain DNS server address automatically

MAC
System Preferences/Network/ TCP/IP:
Configure IPv4: Using DHCP

---

### Post by antsen on 2006-08-30
Just reporting that I have a similar problem, and I'm also new.

My connection seems to dip in and out for no reason.  It doesn't register in FF or aMSN straight away but the lag on XChat can go to two minutes and more.  My house mate running the same Distro and going through the same router has no problems at all.

It also seems that when I log into the router (192.168.1.1) the connection to the outside world kicks back in.  It's very odd, and steepening the learning curve somewhat!

Cheers,

Anthony

---

### Post by Bachstelze on 2006-08-30
apprenti, could you please paste your network interfaces config file ?

```
gksudo gedit /etc/network/interfaces
```

---

### Post by doobit on 2006-08-30
> **apprenti said:**
> The router is a Netgear WGR614v6, and it is connected to a Westell DSL modem.
Windows XP says that my pc has an nVidia nForce Networking Controller Driver, version 50.0.9.0

**System > Admin > Network** shows an active ethernet connection  (interface eth0)

DHCP is selected in Ubuntu Connection settings/configuration

Netgear router manager includes the following information under router status:
Internet Port: DHCP: PPPoE
LAN Port; DHCP: ON

iconfig gives the following:
eth0      Link encap:Ethernet  HWaddr 00:16:17:37:F6:EE
          inet6 addr: fe80::216:17ff:fe37:f6ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:240 (240.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)



Thanks for any help you can provide!

The router should be set up to act as an ethernet bridge for the Westell DSL box, with the router supplying the username and password for PPPoe that your ISP requires. 
I noticed that no IP is assigned to your eth0, so DHCP is not working. You should open up your router to the DHCP page and see if it is seeing your MAC address. You don't have any sort of filtering turned on do you? I use MAC filtering which only allows computers with the MAC addresses that I specify to connect. Also make sure the DHCP IP assignment range is not too limited. 
It may also be possible that your ISP is limiting the number of MAC addresses that it will allow you to connect at one time?

---

### Post by solar_eclipse2 on 2006-08-30
I don't know if it is of any consequence or not but last night I did my first install of Ubuntu 6.06 on an "old" box I had sitting around and I couldn't connect to the internet at first either. 

The system said my nic was active but I couldn't connect to the web either. I deactivated my nic and reactivated it and I had net.

---

### Post by apprenti on 2006-08-30
> **HymnToLife said:**
> apprenti, could you please paste your network interfaces config file ?

```
gksudo gedit /etc/network/interfaces
```

With pleasure. The following appears in the Terminal window:

[I](gedit:5083): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

And in a separate window ("interfaces") the following:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/I]
 

Thanks again!

---

### Post by Bachstelze on 2006-08-30
Really strange... Try :

```
sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by apprenti on 2006-08-30
> **doobit said:**
> *The router should be set up to act as an ethernet bridge for the Westell DSL box, with the router supplying the username and password for PPPoe that your ISP requires.* 

****That seems to be what it's doing for my pc when it's running Windows, and for my Mac(intosh).
[I]
I noticed that no IP is assigned to your eth0, so DHCP is not working. You should open up your router to the DHCP page and see if it is seeing your MAC address.[/I] 

****I followed your advice. It seems that the router is not seeing the pc's MAC address when Ubuntu is running, but it does see it (the same MAC address) when Windows is running. Also, the router has no problem seeing the MAC address for the Mac(intosh) and printer that are connected to the router. 
[I]
You don't have any sort of filtering turned on do you?[/I]

****I double checked. I don't think so. 

*Also make sure the DHCP IP assignment range is not too limited. *

****The last two digits of the assignment range go from 2 to 51, so that seems to be ok.

*It may also be possible that your ISP is limiting the number of MAC addresses that it will allow you to connect at one time?*

I don't think so, since this problem doesn't occur when Windows (instead of Ubuntu) is running on the pc.

I apologize for not (yet) knowing how to turn off italics for my responses within a quote:confused: 

Thanks for your reply. Any thoughts?

---

### Post by apprenti on 2006-08-30
> **HymnToLife said:**
> Really strange... Try :

```
sudo ifdown eth0 && sudo ifup eth0
```

o.k., here's what I got:
[I]
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:17:37:f6:ee
Sending on   LPF/eth0/00:16:17:37:f6:ee
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:17:37:f6:ee
Sending on   LPF/eth0/00:16:17:37:f6:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]

Thanks for your replies:)  Any other thoughts?

---

### Post by Bachstelze on 2006-08-30
All right, DHCP doesn't seem to be working... You'll have to configure it manually. In /etc/network/interfaces, replace the eth0 line with :

```
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

replace with correct values of coure, "gateway" is the IP of your router. Then edit /etc/resolv.conf so it only contains a single line, like this

```
nameserver 192.168.1.1
```

Once again, replace with the IP of your router, then save all files if not done yet and run *sudo ifup eth0*.

---

### Post by comppsyco on 2006-08-30
Hello,
Firstly, welcome to Ubuntu. 
I had the same problem when I first installed. My connection seemed to go in and out at random times. Try this: shut down, unplug your power cord for about 30 seconds, then plug back in and boot back up. I'm no expert, I don't understand this, but I read that Windows likes to put some kind of gobbledigook in your network card that Ubuntu can't deal with. I'm trying to get someone to help me with a software solution to the problem so that I don't have to do this every time.
Sam

---

### Post by nickpaton on 2006-08-30
i've just done a new install and had the same problem.

My solution was within Firefox:

Edit>Preferences>General Tab>Connection Settings>Auto-Detect Proxy Settings for this network.

OK & Close to exit.

Close Ff and restart it again and eurika!

---

### Post by ShagzModo on 2006-08-30
is the Default Gateway in your XP installation the same as when you boot ubuntu?

---

### Post by apprenti on 2006-08-30
> **HymnToLife said:**
> All right, DHCP doesn't seem to be working... You'll have to configure it manually. In /etc/network/interfaces, replace the eth0 line with :

```
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

replace with correct values of coure, "gateway" is the IP of your router. Then edit /etc/resolv.conf so it only contains a single line, like this

```
nameserver 192.168.1.1
```

Once again, replace with the IP of your router, then save all files if not done yet and run *sudo ifup eth0*.


This is the point where my being a complete beginner becomes an issue. I think that I can figure out the correct values, but I have no idea how to access the code that you suggest that I modify. Is there a quick answer that can guide me, or a link that will explain how I can access and modify code? Again, thanks!

---

### Post by Bachstelze on 2006-08-30
THose are just text files you need to edit with whichever text editor you like :) *gksudo gedit /path/to/file* will work fine

---

### Post by epq on 2006-08-30
I am another new user who has also had the problem of my connection going in ad out randomly. 
When I put network properties up it shows that the connection just stalls at 'idle' for periods of time. 
I have now changed to Auto-Detect Proxy Settings and it seems to work.
This problem almost made me give up on Ubuntu, I could not find an answer it before on the forum.
By the sounds of it, it is a general problem and maybe should be addressed somewhere more formally on the site in order to prevent new users being scared away in fear of a slower internet connection than windows.

---

### Post by antsen on 2006-08-30
> **epq said:**
> I am another new user who has also had the problem of my connection going in ad out randomly. 
When I put network properties up it shows that the connection just stalls at 'idle' for periods of time. 
I have now changed to Auto-Detect Proxy Settings and it seems to work.
This problem almost made me give up on Ubuntu, I could not find an answer it before on the forum.
By the sounds of it, it is a general problem and maybe should be addressed somewhere more formally on the site in order to prevent new users being scared away in fear of a slower internet connection than windows.
Ah nice one!

How do I change to Auto-Detect Proxy Settings?

---

### Post by telegramsam on 2006-08-30
Wait you guys, this may not be an Ubuntu problem.  When you have a DSL modem and a ROUTER (as opposed to a switch) you HAVE to have the modem in bridge mode.  If there is more than one computer connected to the router, IT has to handle DHCP.  

Ubuntu should roll with DHCP being issued from the closest piece of equipment.

My suggestion:
1)  Shut down the entire network
2) Hook the modem directly to your machine, and put it in bridge mode.
3)  Reset the router to the factory state
4)  Reconnect your network and start up IN THIS ORDER:  1) modem, 2)  Router, 3)  Computer # 1--use computer 1 to set up the interface (enter your ISP's username, password and DNS servers, if required), and 4) the rest of the network.

---

### Post by apprenti on 2006-08-30
> **HymnToLife said:**
> All right, DHCP doesn't seem to be working... You'll have to configure it manually. In /etc/network/interfaces, replace the eth0 line with :

```
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

replace with correct values of coure, "gateway" is the IP of your router. Then edit /etc/resolv.conf so it only contains a single line, like this

```
nameserver 192.168.1.1
```

Once again, replace with the IP of your router, then save all files if not done yet and run *sudo ifup eth0*.


I tried to do what you indicate, and my lack of success leads me to ask you a few more beginner's questions ](*,) 

1.) when you instruct me to "replace with correct values" in the first bock of code, I'm not sure what the correct ones are for "network" and "broadcast," so I used the ones in your example. I was able (I think!)to confirm the values for "netmask" and "gateway" by consulting my router manager. They seem to be the same as the ones you gave in your example. Likewise, I used 192.168.1.4 for "address" because it is not being used by anything else.

2.)  When I tried to edit/add the second (one-line) block of code, I entered the following *as is* into the terminal:
*gksudo gedit etc/resolv/conf*
This gave me a blank window into which I entered *as is*:
```
nameserver 192.168.1.1
```

After saving, I ran 
*sudo ifup eth0*
and got the following: 
[I]
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"[/I]

3.) Should I try to make changes (e.g., set up a static route) on my router manager as well? I experimented with this, but my router froze up and I had to power it up again.

4.) (For your information, in case it's relevant): When I enter text into the terminal, I often get a message like the following: 

[I](gedit:5213): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

---

### Post by apprenti on 2006-08-30
> **telegramsam said:**
> Wait you guys, this may not be an Ubuntu problem.  When you have a DSL modem and a ROUTER (as opposed to a switch) you HAVE to have the modem in bridge mode.  If there is more than one computer connected to the router, IT has to handle DHCP.  

Ubuntu should roll with DHCP being issued from the closest piece of equipment.

My suggestion:
1)  Shut down the entire network
2) Hook the modem directly to your machine, and put it in bridge mode.
3)  Reset the router to the factory state
4)  Reconnect your network and start up IN THIS ORDER:  1) modem, 2)  Router, 3)  Computer # 1--use computer 1 to set up the interface (enter your ISP's username, password and DNS servers, if required), and 4) the rest of the network.

Thanks for your reply. Before I diassassemble and then attempt reconnect by network (pc, mac mini, printer, (all connected by ethernet to) router, and DSL modem), I have one question for you. Given that when Windows (rather than Ubuntu) is running on the pc and everything else stays the same, no internet connection problems occurr, doesn't this seem to indicate an Ubuntu problem rather than a problem with my home network as a whole. I'm very much a beginner, so I'm very likely to be guilty of some faulty reasoning with these things, but I just thought I'd ask.

---

### Post by apprenti on 2006-08-30
> **comppsyco said:**
> Hello,
Firstly, welcome to Ubuntu. 
I had the same problem when I first installed. My connection seemed to go in and out at random times. Try this: shut down, unplug your power cord for about 30 seconds, then plug back in and boot back up. I'm no expert, I don't understand this, but I read that Windows likes to put some kind of gobbledigook in your network card that Ubuntu can't deal with. I'm trying to get someone to help me with a software solution to the problem so that I don't have to do this every time.
Sam

Hello and thanks for the welcome. I'm delighted to have joined Ubuntu. Now if only I could go online with it:???: 
I tried your advice, but unfortunately it didn't work for me. I wish you luck in finding a software solution.

---

### Post by apprenti on 2006-08-30
> **nickpaton said:**
> i've just done a new install and had the same problem.

My solution was within Firefox:

Edit>Preferences>General Tab>Connection Settings>Auto-Detect Proxy Settings for this network.

OK & Close to exit.

Close Ff and restart it again and eurika!

Alas, I tried your advice, but no luck. I'm glad it worked for you, though.

---

### Post by apprenti on 2006-08-30
> **ShagzModo said:**
> is the Default Gateway in your XP installation the same as when you boot ubuntu?

In Windows XP, the "Advanced TCP/IP" settings window shows DHCP enabled and no default gateway.

My Ubuntu had also been set for DHCP, but was apparently failing to receive DHCP and connect to the internet. Following the advice of another respondent on this thread, I've configured my connection settings to a static IP address. The gateway address in Ubuntu currently matches the LAN IP address of my router (the latter obtained from my router manager). I still can't get online, though! ](*,)

---

### Post by apprenti on 2006-08-30
> **solar_eclipse2 said:**
> I don't know if it is of any consequence or not but last night I did my first install of Ubuntu 6.06 on an "old" box I had sitting around and I couldn't connect to the internet at first either. 

The system said my nic was active but I couldn't connect to the web either. I deactivated my nic and reactivated it and I had net.

In Ubuntu, how can I tell if my nic is active and deactivate/reactivate it? I'd like to try what you did and see if it solves my problem.

---

### Post by apprenti on 2006-08-31
**Success at last!**

After spending the better part of the day trying to get access to the internet, I finally did it. I did the following three things, some of which were suggested by responses to this thread:

1.) reset settings in **System/Administration/Networking**to (as far as I could remember) their original state when I installed Ubuntu

2.) turned the power off on the pc and unplugged it for 30 seconds (in order to resolve any Windows XP-generated weirdness on the network card) before rebooting

3.) unplugged the power and modem connection to the router for 30 seconds before starting it up again

I don't which of these (or combination of them) did the trick (or why the problem originally arose), but if the problems happens again, I'll experiment and share what I find.

Anyway, thanks to everyone who generously offered their advice (especially the many replies by HymnToLife). The first thing that I did when I suceeded in getting online was to bookmark this forum, which seems to be a terrific community. By reading the various threads and playing around with the operating system, I learned many helpful things about Ubuntu, Linux, and computers today, and I'm eager to find out more. Now, though, it's time to sleep.

---

### Post by telegramsam on 2006-08-31
> **apprenti said:**
> Thanks for your reply. Before I diassassemble and then attempt reconnect by network (pc, mac mini, printer, (all connected by ethernet to) router, and DSL modem), I have one question for you. Given that when Windows (rather than Ubuntu) is running on the pc and everything else stays the same, no internet connection problems occurr, doesn't this seem to indicate an Ubuntu problem rather than a problem with my home network as a whole. I'm very much a beginner, so I'm very likely to be guilty of some faulty reasoning with these things, but I just thought I'd ask.

No, if you have an internet connection now, on another machine, this isn't the problem.  If you were having this problem, you would get no internet on anything.

---

### Post by telegramsam on 2006-08-31
GOOD job getting it fixed, though!!

---

### Post by dimitryp on 2006-08-31
****I have same problem with Ubuntu.

I have DSL router with **DHCP** server and Laptop with XP.
It works **fine** with XP and **Kubuntu** - but not works with **Ubuntu** :evil:

(kubuntu and ubuntu = liveCd last version loaded default)

**Ubuntu**:
 - I can ping sites by IP or Name in terminal. 
 - I can input IP in brovser - but see only site name on browser`s top bar.
 - I can`t open any site - only my router setup WEB page!

What the :evil:?

---

### Post by antsen on 2006-09-01
dimitryp did the stuff mentioned here not work for you?

---

