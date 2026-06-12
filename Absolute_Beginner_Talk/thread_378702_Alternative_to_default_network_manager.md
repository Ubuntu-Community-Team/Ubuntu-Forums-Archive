---
title: "Alternative to default network manager?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-03-07
I am on a wireless connection and hav had a lot of problems with Ubuntu freezing for a few seconds. I have not found anything that could explain this behavior. Today, however, I tried disabling all network connections, and everything worked fine. No freezes every 20 minutes. 

What I need is software to bypass my connection settings at System>Administration>Network, leaving me a working connection while the default network manager is disabled/uninstalled. I tried Wifi-radar, attempting to bypass the freezes of the network manager, but it stopped working as soon as I disabled my connections in the network manager.

I really have no idea what to do next. These freezes cause dropped connections, and it bothers me if I watch a movie. If I manage to solve this problem, my Windows XP partition will be wiped clean, with a fresh install of Ubuntu over it. I am so close, and help would be greatly appreciated.

---

### Post by moshuptrail on 2007-03-07
What makes you think that Network Manager is freezing?
Network Manager is just a configuration utility.  Once it exits, it's no longer involved.  Same as Wifi-radar.

I suggest looking at the wireless driver.

Can you compare wireless with wired behavior?

---

### Post by Hallvor on 2007-03-08
I have tried two different drivers (rt61) for my wireless card - both the native in Ubuntu and the windows driver through Ndiswrapper. Both show the same behavior. However, there is no such behavior under Windows XP.

The short freezes only occur when there is an active connection under the network manager. If i disable all connections, the freezes are gone.

Just try to configure a new connection in the network manager, and click OK when you are done. The system will then freeze/hang for a couple of seconds, and your connection should be fine. It is this same freezing/hanging that repeats itself every 20 minutes on my system and drops all connections.

I have no experience with wired connection and Ubuntu, and it would take me hours just to test it. I know of another person with the same problem, and he was also on a wireless connection.

---

### Post by Hallvor on 2007-03-08
Found a solution to the short freezes: [http://www.ubuntuforums.org/showthread.php?p=2266847#post2266847](http://www.ubuntuforums.org/showthread.php?p=2266847#post2266847)

I had to edit /etc/network/interfaces. Details in the thread above.



Hallvor

---

