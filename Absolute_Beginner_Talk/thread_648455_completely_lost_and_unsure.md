---
title: "completely lost and unsure"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by thrownintothis on 2007-12-23
I got thrown into this and have no idea what to do. I just inherited providing internet access to an apartment building full of college students. In the apartment building, there are 8 floors. Only floors 2 through 8 have internet access, 1st floor only the managers office has internet access and it gets a static IP.

 

Floors 2 through 8, every apartment has a wired LAN connection, and there are 3 wireless AP’s on each floor (Mikrotik 2.4GHz) 

The server is on the 5th floor, there are switches located on every floor, north end of the building and south end.

Each AP has a static IP on it presently, basically for remote monitoring and remote access. Each AP has DHCP running on it as well and have 192.168.x.x IP’s on them. The server (running ubuntu) has dhcp3 running on it with 1 full class c block setup on it. IP tables are also running on the server and things are setup that you can only sh into the server from specified IP’s or you have to be sitting at the server itself. Each tenant of the apartment complex should be able to access the internet via a wired connection in their apartment or via one of the wireless AP’s

 

I just had 2 cable services installed at the location, 8 megs each, in order to replace a 10 meg wireless link that was serving the building. I do know that, although each of the cable services installed have 5 static IP’s assigned to them, the SMC router/cable modems do DHCP as well and assign 10.x.x.x IP’s to each user. On one service, I plan to assign 1 static to the server, and 1 to the managers office. I plan to add another NIC to the server (giving me a total of 2 NIC’s) and assign a second static IP to that NIC. 

 

I believe I need to shutdown the DHCP3 service currently running on the server, then change the IP tables to allow access using IP’s from the cable company. I’m really new to the linux/ubuntu OS and need some guidance.

---

### Post by ChaosParser on 2007-12-23
You'd probably get more answers in the Server Forum.  Try the IRC chat as well?  

Good luck! :)

---

### Post by zach12 on 2007-12-23
> **ChaosParser said:**
> You'd probably get more answers in the Server Forum.  Try the IRC chat as well?  

Good luck! :)
Yes Try ther

---

### Post by blueridgedog on 2007-12-23
Given that the cable modems are upstream of the server, the downstream clients will no doubt not be able to see the dhcp services offered by the cable modems.  The server is undoubtably running NAT via iptables and that would not work with a one hop up DHCP server.  In fact, with static IP's, I assume they will have that feature turned off.  Ultimately you simply need to re-configure the external interface of the server for the one cable modem that you have hooked up this far (ip address, gateway, dns server, subnetmask) then you will need to adjust the script that manages your firewall (hopefully it is a script).

Doing this should get you migrated to the first cable box and you tenants should be happy (assuming 8 megs of cable is better than 10 megs of wireless).

The REAL problem I see lies when you attempt to hook up the second cable modem.  It is your expectation that the server will use each NIC automagically, but I feel the "load balancing" you expect across the two NICs will require some additional configuration.

How is the manager's office given a static IP?  Is it wired upstream of the server or is the server firewall piping a static to it?

You may get more assistance/ideals in the networking forum.

Your core issues are not Ubuntu specific per say, but they will involve a great deal of network understanding.  I have done setups similar and much more complex than what you are dealing with, but it would be challenging to work through some of the issues in the serialized forum that we have here.

---

### Post by The Cog on 2007-12-23
I'm having trouble understanding the IP and routing arrangement needed. What is the Ubuntu servers role in this? How do the users get access to the Internet? Are there routers? Is there a proxy server? How are you hoping to share two internet services out?

---

### Post by thrownintothis on 2007-12-23
blueridgedog
Are you interested in helping me fix all of this and getting this change over made?

---

### Post by blueridgedog on 2007-12-23
I will give you all the advice I can.  However, you have a complicated setup that was put in place by someone who knew what they were doing.  You are heading down a fun path that will be a great learning experience.  Your best bet is to find a mentor in your area who can work with you one on one and help you grow into this network management roll.  What is your location (if you care to share it)?

I am also not certain off hand as to the load balancing the two NICs.

---

### Post by thrownintothis on 2007-12-23
I'm in east tennesse, and as for mentor,  I honestly don't know anyone to call on or assist me on this.

---

