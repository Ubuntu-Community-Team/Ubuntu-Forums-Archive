---
title: "Help! Wireless problems!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-15
For some reason, my wireless is going on and off. It work, and has been working, but randomly it will just "shut off."

My connection is good, and all other computers are accessing the internet flawlessly (Windows OS's).

My router is literally right next to me, too.

Can someone help!?

---

### Post by Bachstelze on 2007-06-15
What kind of wireless adapter do you have ?

---

### Post by alecwh on 2007-06-15
```

Marvell Technology Group Ltd.
88w8335 [Libertas] 802.11b/g Wireless

```

As far as I know, nothing triggers it. Randomly, it just stops working. It says I'm still connected, and I can reconnect to my network, but I can't get on the internet. NOR can I access my router's web interface at 192.168.0.1.

---

### Post by alecwh on 2007-06-15
Augh! It's really annoying, I have to restart my PC every time to even see this thread!

---

### Post by alecwh on 2007-06-15
:( Anyone? {bump}

---

### Post by silverglade00 on 2007-06-15
I had this problem on another distro with my wireless card. It turn out the driver for it had the power turned down so much that it would barely connect. Once I switched to using ndiswrapper and the windows driver, it worked fine. Maybe that will work for you. Sorry I can't help more, I have never owned a Marvell wireless.

---

### Post by alecwh on 2007-06-15
I'm using ndiswrapper right now, so I don't think that's the problem.

---

### Post by alecwh on 2007-06-15
bump, last time.

---

### Post by incredibleironman20 on 2007-06-17
Personally, I must say that I've got the same chipset in my card and it ain't that great. I have the same problem on mine...it can be working perfectly one minute and then I have to reconnect seven or eight times before I get the signal back. I am thinking it is the driver itself, not ndiswrapper, and literally just gave up trying to figure out why it wasn't stable since it seems to be something we can't really do much about at the moment. :(

---

### Post by ncappel1 on 2007-06-17
I don't have the same card as you, but my desktop shows the same symptoms when connected to my family's apple network. It seems as if it is online, gaim doesn't get disconnected, I can see the router with iwconfig, but it isn't getting any signal. 

I don't really have a 100% solution, but I found that I could give it a kickstart if in a terminal I told it to reconnect to the essid and accespoint, with iwconfig <wireless device> essid any, and iwconfig <device> ap auto. It has saved me from having to reboot countless times, hope that works until you find a better solution!

---

