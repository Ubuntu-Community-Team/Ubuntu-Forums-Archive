---
title: "ktorrent - No incoming connections (possible firewalled)"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-01-15
Ok so I first downloaded Ktorrent and got an error of No incoming connections (possible firewalled).  I then read on the net and downloaded firestarter to see if i could forward the ports.  Ktorrent is set to download on a port other than the default.  Is this possible or do I have to stay in the 6800 range?  I've opened the port on my router and set a policy in firestarter to allow that port.  what have I done wrong?  I've also opened 4444 for the UDP tracker port.

---

### Post by rbrittner on 2008-01-15
I've set the default port in ktorrent back to 6881 and it's still blocking incoming traffic.  I've updated firestarter and my router to reflect the port 6881.  I've allowed both UDP and TCP on my router on port 6881 so I dont know what's going on.  Anyone?

---

### Post by rbrittner on 2008-01-15
Anyone have any ideas?  Do i need some sort of other software since ktorrent is made for kde?

---

### Post by Drakkor on 2008-01-15
I used the ktorrent plugin to automatically forward ports, it's in Settings>Configure kTorrent>Plugins

---

### Post by rbrittner on 2008-01-15
Ok I tried that and it couldn't find anything to forward, I thought i'd take the router out of the equation so I connected my computer directly to the modem and disabled firestarter.  I also set my ip from static back to roaming mode.  I'm still getting the incoming connection error so it's definitly a setting within ubuntu or ktorrent.

---

### Post by vikram on 2008-01-15
can you check if iptables is blocking the packets ?

sudo iptables -L

---

### Post by Drakkor on 2008-01-15
Did you try the "plugins" directory, like in my screenshot ?

---

### Post by philinux on 2008-01-15
Nothing wrong with kde apps.

But deluge has never been a problem.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by rbrittner on 2008-01-15
Ok so I solved the problem.  I looked on the torrent site that I use [www.torrentleech.org](www.torrentleech.org) and read that DHT and PEX has to be disabled.  Disabling DHT is easy but PEX has to be done for every torrent.  (kind of a pain but definity do-able) I was also reading a post on the ktorrent site

[http://ktorrent.org/forum/viewtopic.php?t=2178&highlight=&sid=04f11a09279b69da08ba3f206df5289e]("http://ktorrent.org/forum/viewtopic.php?t=2178&highlight=&sid=04f11a09279b69da08ba3f206df5289e")

topic was disabling it globaly anyways, a site admin said they are going to impliment so hopefully it will be released soon.  Anyways, thanks to everyone for the reply's.  Ubuntu would be a lot harder without everyone's help.  Especially from a 10+ years windows user.  Thanks

---

### Post by Claus7 on 2008-01-19
Hello,

glad you solved your problem. I have to tell you that I was able to get rid of this message by port forwarding the 6881 port in my modem rooter. The bad thing is that almost every time I open my computer I have to do this. Just FYI.

Regards!

---

### Post by FrooziE on 2008-03-24
I have DHT enabled and UPnP plugin enabled (but no ports being forwarded). The icon is still there and it still says that I have no incoming connections, but I download and upload fine so I'm not sure if it matters that Ktorrent tells you that.

---

