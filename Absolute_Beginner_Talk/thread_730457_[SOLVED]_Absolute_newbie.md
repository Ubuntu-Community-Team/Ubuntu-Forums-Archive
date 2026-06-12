---
title: "[SOLVED] Absolute newbie"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-20
Hi Guys, :confused:

I have just installed latest release of Ubuntu onto spare hard drive in my desktop computer. I am running a D_link DVA-3340S ADSL/VOIP/Router. During install the program was unable to detect the router. I am now trying to figure out how to install it. 

I am using an ethernet connection from this computer. When I check the settings of the router from IP add 10.1.1.1 (using XP) I see that I am using WPA security, 

The WAN settings are
IP control of dynamic, (I am presuming that means DHCP) 
Conn Type PPPoE LLC
Service type = UBR

The LAN settings are
IP add  10.1.1.1
Subnet 255.0.0.0

I am not good with command line stuff, prefer to be able to use graphical interface. 

I have used the 'network tools' GI and set the DHCP to dynamic, and the IP add to 10.1.1.1 I have tried Pinging it, but get no results at all. 

Connection via XP is not a problem 

Any ideas, as I also need to install my HP all in one printer, which is wireless through this router. 

If I can get my hardware up and running I am most likely going to ditch Windows as I hate it!

Thanks in advance

Douglas

---

### Post by macogw on 2008-03-20
Ethernet or USB connection?  USB routers don't usually work...at least not easily.  If the router has an ethernet option, use that.

---

### Post by tropdoug on 2008-03-20
Ethernet connection. 

I can now connect to the router if I put in Http//10.1.1.1 and once in the setup pages can ping an address and get 100% succes in transmission and receieving. That says to me that I should be able to go to a site, but no go. No matter what address i put in, it wont load a page. I have disabled the firewall in the router as well. 

Using ping from the network settings tool, results in total failure. 

:(

---

### Post by tropdoug on 2008-03-21
Ha, solved it, I disabled the ipv6 in both firefox and the network, problem solved, there is a heap on the ipv6 issue on here. 

How do I put the Solved thingy onto my thread so that it shows as solved?
Douglas

---

### Post by herbster on 2008-03-22
Thread Tools.

---

