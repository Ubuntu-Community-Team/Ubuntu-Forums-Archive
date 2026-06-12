---
title: "Wine and WoW behind ISA"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by belaflek on 2007-06-05
Ok...I slapped ubuntu on the 2nd partition of my computer. I am using 7.04. I am behind an ISA Server and trying to play World of Warcraft. When I'm in XP there are no problems. Game starts up and runs fine. When I boot to ubuntu, I run it via wine and get to the logon screen but all I get is disconnected from server. I think its a network thing but I setup both firefox and setup the network proxy settings under system. I am able to get to said internet but its just WoW that doent seem to want to connect up. I'm also not using authentication for ISA...its set up as a insert proxy and continue

---

### Post by Chayak on 2007-06-05
Is your XP part of the same domain that the ISA server is on?  If it is that explains why you can connect in windows and not linux as ISA will authenticate users via Active Directory.  It all depends on how the ISA server is configured though.  On the network I administer if you don't authenticate on the domain you get no connection what so ever.  The easiest way I can think of is to put in a rule on ISA for your linux machine's IP to allow those ports.

---

### Post by belaflek on 2007-12-19
nah..Im not authenticating. I can set up the browser to point and it shows up on my logs but when I run wow on wine it doesnt even show a denied connection...somehow the wine is not getting the point that it has to send it to the proxy.

---

