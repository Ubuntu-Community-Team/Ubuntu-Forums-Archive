---
title: "2Wire USB 802 Setup"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2008-03-15
Just what we need another post about these cheapo 2wire USB adapters right?

Ok so I've searched and searched, and I've only been able to get Ndiswrapper to half work with this hardware. When I installed the drivers, and load them, the USB adapter powers up and sees networks, it however won't connect to any of them. 

At first I thought it was a power issue, but even connected to a powered hub, it sees networks but will not connect to any of them. 

I've set all the proper WEP and ESSID information in the Network Manager in Ubuntu (running 7.10). When I enter in the ESSID and such it sees my router (my ESSID isn't broadcasted), plus several other of the neighbors routers. However the weird part is when I type in iwconfig in the terminal, none of the ESSID information pops up, and it has a bunch of other bogus information, like a link speed of 2 MB? 

Anyone else run into this? Any other options? If it where my computer I'd buy a new 802 card, no big deal, but I'm fixing this PC for some people that don't have much money, so I'd prefer to use their existing hardware if I can, otherwise I have to put XP back on it for them, which I really don't want to do.

---

### Post by OhioYJ on 2008-03-15
Ok I've been reading, and reading about this, and I"m thinking the drivers are probably working since the card can see all the different networks, it just can't connect to them. Going through the Ndiswrapper site, I came across this:

> Remember, if you have a firewall, let it know that wlan0 is an external interface, and allow it to pass traffic. Otherwise you won’t even be able to ping your AP.

Now I'm just using the default 7.10 Ubuntu install (32-bit). I have not installed Firestarter or any other firewall that I'm aware of? Does Ubuntu come with something preloaded to do this?

The only command that seems to do anything at all for me is 

iwconfig wlan0 mode (ad-hoc / managed)

I can flip the mode back and forth, but nothing else will change for me, I can try the essid, rate, key, doesn't matter, nothing changes in iwconfig

When I try ndiswrapper -l, it says driver installed, device present, but to ensure it wasn't the problem, I did blacklist bcm43xx, even though I don't think that was an issue.

---

### Post by OhioYJ on 2008-03-15
Ok I'm not sure what I've changed, but now when I type in the WEP password in the Ubuntu GUI network manager, the security mode and key are now fixed.

However it still won't let me change the ESSID. In fact if I then issue the command iwconfig wlan0 essid (my essid) all the security mode and keys disappear from the iwconfig print out.

---

### Post by OhioYJ on 2008-03-16
Bump.........

---

### Post by OhioYJ on 2008-03-17
One more bump..... Tonight I'm going to try another 802 card I have laying around, I believe its a Ratlink chipset, but I've never been able to get it to work in Linux, but I've never run Ubuntu 7.10 either........

---

### Post by OhioYJ on 2008-03-18
The other card isn't a Ralink chipset, its a Prism 2.5 Rev 01 card, which also doesn't work in Ubuntu.....

---

