---
title: "Network Card"
date: 2007-03-04
forum: Apple PPC Users
---

### Post by innocentson67 on 2007-03-04
I installed Ubuntu 6.10 on my new iBook G4 and all went well until I tried to load a web page in firefox...no page would load. I check the settings in the network menu and even put in the DNS numbers. still not able to connect. it shows that it sees my network card. i would like to continue with ubuntu but with no ability to get online I fear I will have to scrap th idea and put back OSX

---

### Post by VorDesigns on 2007-03-17
It would be nice if someone had something to say about this post; I have just installed 6.10 on an iMac G4 which seemed like everything was ok.  Then I ran into the same problem, can't patch, can't ping, can't web browse.
Interestingly, I did get an IP and DNS information from the DHCP server.

---

### Post by keifer on 2007-03-17
I've had this problem starting with 6.06. I also haven't gotten anyone even remotely interested in looking into it, but it is good to know it is not just me. For consistency, I'm also running a iMac G4.

I also get the IP/DNS information from the server, but can't do much else.

---

### Post by VorDesigns on 2007-03-17
I haven't had time to dumpster dive this whole post but, in the interests of adding any value to this one;  [Ping works, but no internet ]("http://www.ubuntuforums.org/showthread.php?t=317996") 
This link is related to the use of a proxy but it at least provides ANY avenue of investigation.
I wish us all luck and will post back if I find anything better.
Lucky for the Mac folks that an anal retentive Windows support technician decided to branch out even further than Linux.

---

### Post by VorDesigns on 2007-03-17
OK,
First, I think I have an iMac circa 2000 (it's blue) I don't know if it's a G4 or a G3.  It supports PC100 RAM so I think it's a G4.  256MB of RAM, it's pokey.
--
This system gets it's IP from a firewall including DNS information.
At first I could not ping the development LAN interface, had to adjust the firewall to allow ping to it.  Problem solved.
Ping works but no internet.  on to the next issue which is clearly DNS, I hope.
-
I know that the DNS servers offered by DHCP work because I have two DNS servers running on the production LAN and they use the same servers to forward calls from LAN clients.  So, I changed the servers offered by DHCP to the Production LAN DNS servers and created rules allowing DNS calls to them from the development network to the production network.  Uh-oh, it didn't work, it seems that the DHCP lease hadn't expired so the client renewal process post reboot didn't refresh any settings.  Sadly, while I'm pretty good in the Win32 environment and a passable fair troubleshooting Mac equipment blind.  I don't know how to release renew the IP on Linux.  I manually adjusted the DNS server information in the Network control panel and I can now resolve DNS on the system.

---

### Post by VorDesigns on 2007-03-17
Breaking this post up because I don't want to have a time out issue.
-
If you likewise can ping but are not getting DNS through your preferred DNS provider; there is a well known server at 4.2.2.2 that you might consider using for testing although I would not make this your permanent DNS server.

---

