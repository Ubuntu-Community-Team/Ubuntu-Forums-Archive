---
title: "Firestarter picking up dozens of Chinese IPs per hour"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by atorch on 2008-03-19
Hi,

I've started running Firestarter on startup and I've noticed that I'm getting about a hit every 1~10 minutes.  I learned about the 'whois' command today, and I've been running it on some of the hits that Firestarter picks up.  Many of them are from Chinese IPs.  

What's the deal?

Edit:  I'll look for some examples...

I got six hits from this guy, in two minutes:

inetnum:      202.97.192.0 - 202.97.255.255
netname:      CNCGROUP-HL
country:      CN
descr:        CNCGROUP Heilongjiang province network

---

### Post by Xiong Chiamiov on 2008-03-19
So, you're being probed often, probably by zombies looking to infect more 'puters.  I don't think it's anything to be worried about, as long as you're protected.

---

### Post by atorch on 2008-03-19
So how normal is this?  Are most computer on the internet getting tons of pings from zombies?

Also, if my firewall were down (and if I were running windows, I guess), what would happen when someone pings me and decides that my compey is ripe for infection?  How do you go from pinging someone to installing something on their computer?

---

### Post by Xiong Chiamiov on 2008-03-19
I couldn't tell you how normal, because my router stops everything but a few ports open for bittorrent before it even gets to any of my computers.
If you responded to a ping, it would simply alert them that you "exist".  Then they'd try a few techniques to get into loopholes and gain some sort of control over your system.  Even on Windows, if everything's patched (and patches have come out for all known exploits), it's not a big deal, since they can't do anything (not that I would ever run Windows like that!).

---

### Post by sonofusion82 on 2008-03-19
i get this all the time too. it worries me a bit when i first installed guarddog and enabled logging. but at least it is better to be aware of this than just being ignorant as in windows.

---

