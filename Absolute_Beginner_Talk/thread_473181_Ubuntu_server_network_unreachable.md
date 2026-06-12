---
title: "Ubuntu server: network unreachable"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-06-13
I'm getting the above when I attempt to ping out. Any advice on how to proceed?

I have an eMachine T5226... All cables are plugged in correctly.Any advice appreciated - Thx. I've installed Server64.

---

### Post by Cheese Sandwich on 2007-06-13
Hmm, might be router-related (I swapped out my old computer for a new - perhaps a MAC address issue...)

Hold off on any replies is you were so inclined, let me fiddle some more...

---

### Post by Sushubh on 2007-06-13
is your problem related to mine?

[http://ubuntuforums.org/showthread.php?t=457184](http://ubuntuforums.org/showthread.php?t=457184)

---

### Post by Cheese Sandwich on 2007-06-13
> **Sushubh said:**
> is your problem related to mine?

[http://ubuntuforums.org/showthread.php?t=457184](http://ubuntuforums.org/showthread.php?t=457184)

Unlikely, ping errors out immediately with the error message,

I think I also recalled an Intel pre-boot message about trying to get DHCP. I think I just need to fiddle with my router... Hopefully ubuntu recognizes my machine's network card.

---

### Post by Cheese Sandwich on 2007-06-13
Ok, when I do "lspci -v", the ethernet device comes up as "unknown". :( Any advice?

---

### Post by Cheese Sandwich on 2007-06-13
The following seems have fixed it:

sudo dhclient eth0

after having brute-forced an IP address via:

ifconfig eth0 inet 192.168.etc...

:?

---

### Post by Cheese Sandwich on 2007-06-13
...but not after a reboot! :?

---

### Post by Cheese Sandwich on 2007-06-13
Ok... I re-installed server64, and during the network configuration phase it managed to do so successfully (probably due to the router changes I made.

Problem solved.

---

