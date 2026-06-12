---
title: "Is this possible?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-04-28
I have 3 PCs connected. 1 WIN, 1 UBUNTU (3 LANs) and 1 (call it GGG) with some small linux which can be used for traffic control only. I put my internet connection in UBUNTU. Is it possible GGG to control traffic between WIN and UBUNTU?

---

### Post by Koybe on 2006-04-28
Why not? It depends on the way you're connected. I mean what network hardware is used?
Hub? Switch? Is GGG a router? Direct connection?

---

### Post by Blagomir on 2006-04-28
I have a LAN cable from my ISP. But GGG does not have directo connection to internet. It connect first to UBUNTU.

---

### Post by Koybe on 2006-04-28
I'm sorry but I can't find a way to help you. You need to be more specific.
Anyway if you place you're GGG between the other PC and catch all the traffic, it should work.

---

### Post by Sarisar on 2006-04-28
I think you're trying to say you have Ubuntu on one machine with 3 network cards and it connects to the internet, the windows machine and the 'ggg' machine. Like so


Windows
   |
Ubuntu---------Internet
   |
ggg


If that is the case I don't think there is any way it can control what goes between your windows machine and the ubuntu one because it isn't directly connected to both.  If it was ubuntu <-> ggg <-> windows then it COULD control that.  In fact if you could put the network cards into ggg and have it running as a type of router / switch that would be my thoughts.

Of course I've only read about this so I could be talking out of my rear end!

---

