---
title: "Help with Internet"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by outburst81 on 2007-03-15
I am an absolute newbie, i just installed ubuntu 6.10 as my first Linux OS ever.

I have a wirless network running at home and i was running fin when i was using windows, how ever when i switched to ubuntu i cant seem to connect to the internet.

However for som reason it is finding my wirless network, ip, subnet etc.... all th right stuff but it just doesn't seem to connct to the internet.

My wirless card is TP-LINK WN510G
im running ubuntu 6.10
in the connction properties window it's showin the stats of the wirless as "idle" and it also show that i have about 70% signal strengh.
ive loaded ndiswrapper and tried to load the xp drivers with no luck.
ive disabled the IPv6.

if someone could please help me that would be fantstic, as i have looked throug a lot of other posts and people seem to have similar problems but those solutions haven worked for me.

---

### Post by msaied on 2007-03-15
first open a terminal window and type: ifconfig 
and check how many devices are active 
some times it helps to disable all other network devices . for example if you have a lancard and wireless and you want to use the wireless , disable the lancard by typing: sudo ifdown eth0
assuming that your lancard is  eth0 . also make sure your DNS is set right in the system->administration->netwoking

---

### Post by overdrank on 2007-03-15
> **outburst81 said:**
> I am an absolute newbie, i just installed ubuntu 6.10 as my first Linux OS ever.

I have a wirless network running at home and i was running fin when i was using windows, how ever when i switched to ubuntu i cant seem to connect to the internet.

However for som reason it is finding my wirless network, ip, subnet etc.... all th right stuff but it just doesn't seem to connct to the internet.

My wirless card is TP-LINK WN510G
im running ubuntu 6.10
in the connction properties window it's showin the stats of the wirless as "idle" and it also show that i have about 70% signal strengh.
ive loaded ndiswrapper and tried to load the xp drivers with no luck.
ive disabled the IPv6.

if someone could please help me that would be fantstic, as i have looked throug a lot of other posts and people seem to have similar problems but those solutions haven worked for me.

Hi this thread may help.
[http://ubuntuforums.org/showthread.php?t=377783&highlight=TP-LINK+WN510G](http://ubuntuforums.org/showthread.php?t=377783&highlight=TP-LINK+WN510G)
Good luck!

---

