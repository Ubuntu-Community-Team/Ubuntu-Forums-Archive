---
title: "Wireless Card Keeps Fading in, and out."
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by burstroo on 2006-05-09
I'm using my Compaq Presario 2500 and have Ubuntu on on partition and XP on the other. (I'll completely convert to Ubuntu if I can get this problem fixed.) Anyways, I have a Dell 1300 Wireless Mini-PC card built in the system. When I bring Ubuntu up, I get this crap >>

1. I click the network activity icon.
2. Every two or three seconds it goes from being Idle to the amount of active
3. Two or three seconds after that it goes back to being idle.

Thus I cannot get to the net. Meaning, I'm not able to get any diagnostics from the terminal for you guys to look at. Do you know of anything to fix this, possibly just from what you've heard? 

Thanks

---

### Post by Sendervictorius on 2006-05-09
Sounds to me that your PC is doing a DHCP request broadcast, and not getting a reply from your access point. Possibly an encryption problem.

Fire up a terminal, and type in the following commands, then post the results of each back on this forum thread:
  iwconfig
  ifconfig xxx
(where xxx is the wireless port name from the iwconfig command - e.g. wlan0, or ath0)
  lspci | grep Ethernet

---

### Post by sailor2001 on 2006-05-09
I had the same problem.....after a few months of this, pulled the card and hot wired direct to router........Don't know if it was the just the card being bad or what..but haven't had any problems since and I have another box wireless with the same card and it works fine........possibly that one card was using too much bandwith

---

