---
title: "how to download torrents"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by ankitguptag18 on 2008-03-27
i m new to ubuntu.....How do we download torrents????
is there ne thing like utorrent

---

### Post by kpkeerthi on 2008-03-27
[http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

---

### Post by Ub1476 on 2008-03-27
Deluge, Azureus, Transmission, Ktorrent .. Lots of bittorent clients. I recommend Deluge if you use Ubuntu, Ktorrent if you use Kubuntu.

---

### Post by kpkeerthi on 2008-03-27
Discussions on best torrent client for Ubuntu:

[http://ubuntuforums.org/showthread.php?t=700571](http://ubuntuforums.org/showthread.php?t=700571)
[http://ubuntuforums.org/showthread.php?t=736098](http://ubuntuforums.org/showthread.php?t=736098)
[http://ubuntuforums.org/showthread.php?t=722179](http://ubuntuforums.org/showthread.php?t=722179)
[http://ubuntuforums.org/showthread.php?t=609055](http://ubuntuforums.org/showthread.php?t=609055)

---

### Post by iSplicer on 2008-03-27
I, on the other hand recommend Azureus.

Run this:
```
sudo apt-get install azurues
```

---

### Post by ankitguptag18 on 2008-03-27
how to download Deluge..........

---

### Post by kpkeerthi on 2008-03-27
Download the two .deb files from [here]("http://www.getdeb.net/release.php?id=2347") to /home/<user>/deluge

Open a terminal and enter these commands
```
cd ~/deluge
```
```
sudo dpkg -i *.deb
```

Launch deluge from Applications -> Internet -> Deluge or simply **deluge** from command line

---

### Post by Google Spider on 2008-03-27
> **ankitguptag18 said:**
> how to download Deluge..........

Applications >> Add/Remove programs

Search for "torrent" and then check the box in front of Deluge. Apply.

---

### Post by kpkeerthi on 2008-03-27
But [www.getdeb.net](www.getdeb.net) has the latest version of deluge

---

### Post by hyper_ch on 2008-03-27
rTorrent is the way to go :)

---

### Post by ankitguptag18 on 2008-04-11
i have installed azureus but is the download doednot start it says there is some prob with UDP port (NAT/firewall).

I cannot open the port of my router as i am not the administrator of the router

---

### Post by kpkeerthi on 2008-04-11
Torrent clients need incoming connections (usually in the range 6881-6999) to be allowed. You need to 'forward' incoming traffic to these ports at the router or have your router admin do this for you. 
If you are running a software firewall (like iptables), you need to configure the firewall too so it does not filter out the packets from reaching your torrent client. 
As far I know, torrent clients will not work if the above can't be achieved or is 'restricted' in your environment. I'm not sure if there are workarounds or hacks to get away with the port forward thing. I'll leave that to others to chime in.

---

### Post by hyper_ch on 2008-04-11
by default, you don't need to alter iptables or install firestarter or something on your linux box. However you must forward the according port(s) from your rouer to your inux box.

---

