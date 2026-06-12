---
title: "LAN Problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by guyarye on 2007-11-01
I have been using Ubuntu 7.04 for a couple of months and I suddenly got this problem.

I don't have network, when I'm in nautilus and I don't have Internet in ubuntu. I had that all but it suddenly disappeared without reason and I don't have LAN even with the Ubuntu 7.04 live CD.
So formatted my HD couple of days ago and I have still nothing.
I also have windows XP installed on another HD and there I have everything working.
Note that I'm connected via wires not wireless.
What should I check or do?

---

### Post by hoges on 2007-11-01
When you go to network manager, do you see anything in the connections box? Or has everything disappeared completely?

---

### Post by guyarye on 2007-11-01
The network manger says that I'm connected even when I plug out the network cable.

---

### Post by SpiritIsReality on 2007-11-01
howdy
could be this:
noob12 says here:
[http://ubuntuforums.org/showthread.php?t=557033](http://ubuntuforums.org/showthread.php?t=557033)
> 
This is still on the original tack of something to do with Windows leaving the adapter in a state that the linux driver isn't going to reenable it.

While in Windows, can you navigate to your Network Connections, select your wired connection, then right-click on it and select Properties. Click the Configure .. button next to the driver name. Select the Advanced tab and see if there is any option related to Wake-on-LAN or Wake Up. If there is a setting, check that it is set so that Wake-on-LAN remains enabled after shutting down.
may be worth a try
there is a thread devoted to the problem of some nic cards having this problem.
can't find it right now. will take some time.
trails

---

### Post by SpiritIsReality on 2007-11-01
howdy
found that thread
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
trails

---

### Post by guyarye on 2007-11-01
*bump*

---

### Post by jaybombalous on 2007-11-01
did u lose a DNS server address in your configuration?

Maybe a few screen shots would be helpful.

---

