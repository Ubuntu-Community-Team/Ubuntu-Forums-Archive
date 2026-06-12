---
title: "ktorrent speed fluctuation issue, everything checked but problem still remains"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-09-05
hello there

i am having trouble in getting full speed in Ktorrent.

my download speed keeps fluctuating. it reaches peak then, descends down, so that avrage speed is always almost half of max.

I have checked following most frequently adviced things:


1. i don't have any router.

2. My isp isnt shaping traffic as i get max speed in utorrent in windows.

3. i have opened both tcp and udp ports by using this command :
   sudo iptables -A INPUT -p udp --dport <port no> -j ACCEPT

4. i am using DHT and connection encryption in ktorrent.

5. have checked with torrents with highest seed to peer ratio. same result.

6. its able to receive incoming connections. have checked with deluge port open checker.

7. have tried using port number greater than 10000 as i read somewhere that this gives better result in ktorrent. but same result.


This speed fluctuation issue has always been there with ktorrent, evn with Deluge.

Where is the problem ? I get full and stable speed in utorrent under windows.

Please help, as this problem makes me boot into windows xp for downloading things (which i really hate).

---

### Post by bone2006 on 2007-09-05
It could be something with your ISP and many are doing things to slow down torrent traffic.  I would get firestarter and then create a rule for your torrents, which should open ports 6881 through 6889 if I'm not mistaken.  Give deluge a try, open up preferences and click on the port testing to verify that the ports are truly being forwarded.  Then take a look at the encryption and try to encrypt in full.

If your ISP is doing something, you should encrypt as on way to bypass the possible thing that your ISP is doing and another thing some people do is change the default ports on your torrent client.
I've had much better speeds with deluge, again check the port forwarding tab and ensure that the ports really are being forward and use the encryption option under preferences.

---

### Post by cyneuron on 2007-09-05
thanks for response....

but i already wrote ports are open, encryption is enabled...

isp isn't throttling my speed.... i am getting max and stable speed with utorrent in windows...

its only under linux specially Ktorrent.... deluge was also no much better...

pls someone help....this problem is really annoying me.....

---

### Post by usererror on 2007-09-05
is there a router involved?

---

### Post by hyper_ch on 2007-09-05
Did you enable UPnP?

---

### Post by cyneuron on 2007-09-05
there is no router. 

yaa have tried enabling upnp, but by the way, is it of any use here as no router is involved ?

---

### Post by afonic on 2007-09-05
Have you tried using Transmission?

I seem to get much better speeds with it than Ktorrent.

---

### Post by hyper_ch on 2007-09-05
If no router is involved then enabling UPnP shouldn't make any difference... since there are not ports required to be (auto-)forwarded.

---

### Post by daverich on 2007-09-05
try deluge.

it made a huge difference to me as it encrypts what it's doing.

literally 10-20x faster.

Kind regards

Dave Rich

---

### Post by bone2006 on 2007-09-05
How are you determining that the ports are open?  For the longest time I thought my ports were open, but have you opened deluge, clicked on preferences and then you'll get this link you can click it will test if your ports are actually open.

---

