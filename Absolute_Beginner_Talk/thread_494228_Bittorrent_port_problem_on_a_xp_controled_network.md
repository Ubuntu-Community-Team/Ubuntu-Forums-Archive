---
title: "Bittorrent port problem on a xp controled network"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by taps128 on 2007-07-06
Hi, i recentll yinstaled ubuntu and I was amazed by it. But unfortunally I encountetred a problem i was unable to solve. I tried opening the ports on my computer usign the command sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT, i tried guard dog. But nothing seems to work. My download speed on the bittorrent client is to low. 

Ok. My situation is as follows. 

I connect to theinternet over a Lan network. The computer which is actually connected to the internet is my wifes laptop, which runs Windows Xp, witch ICS enabled. My compzuter runs ubuntu 7.06. It as cable, computer to computer neteork. There are no other computers on it. 
Now , what do I have to do to use bittorent nornally. both on my computer, and my wives?

Thanx in advanced.

Nikola

---

### Post by defrex on 2007-07-06
First, make sure your not on the list of people who are getting screwed:
[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)

Other then that, try poking your hole in in the XP firewall on your wife's machine. If that doesn't work, maybe invest in a router? I'm not sure if windows connection sharing dealy has a firewall in it or not.

---

