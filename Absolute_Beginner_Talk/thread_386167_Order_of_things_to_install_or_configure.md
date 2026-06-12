---
title: "Order of things to install or configure"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jvslice on 2007-03-16
I have three boxes up and running on a small network at home, working independently.  There are named:

red: New AMD box from System76 running edgy
white: Old Gateway PII - 300 running dapper
blue: Toshiba Laptop - running fiesty and WinXP (dual boot)

In the long run I would like "red" to be my main box, uses as a file and print server. 
Both "red" and "white" can have static IPs, but "blue, is my on the road box and either needs a different static IP or dynamic, for where I am at the time.

I've looked at a few "howto" documents and should be able to follow directions, the main question is which to install first, second, etc?  For example: samba before or after configuring my printer on "red" to be able to share with other Ubuntu boxes.

Additionally, on some of the howto it appears the the clients need a static IP in order to connect to the print server ("red" in my case), no problem with "white", but "blue" is the problem, because I would need to re configure the IP on both XP and Ubuntu all the time, which is a pain.

Hopefully, I have not confused everyone with my question.

---

### Post by Scunizi on 2007-03-16
Unless your router will allow you to set a fixed ip for your blue machine even while the blue machine is setup for DHCP.  That's what I do at home on my network.  I have DHCP on the router with fixed IP's for each box.  If another machine shows up and is configured for DHCP the router knows its not one of the "named" machines and assigns an ip to it.

---

