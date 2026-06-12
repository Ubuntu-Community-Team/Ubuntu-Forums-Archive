---
title: "Problem Downloading Torrents b/c of Firestarter"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-19
Hi, I was trying to download a torrent file but was lucky if my download speed went above 1kb/sec.  Upon investigation I discovered that firestarter was blocking all the connections.  I tried to figure out how to allow connections from bittorrent, but nothing seemed to work,  not even telling firestarter to stop the firewall...any help? I've attached screen shots of the rule I tried to make and the blocked bittorrent connections.  So far my changes got me up to a whopping 4kb/sec...

help!

---

### Post by seshomaru samma on 2007-05-19
you are using port 6881 for torrents
did you open that port in firestarter?
also are you using a router? you might need to fwd that port to your box as well....

---

### Post by Hallvor on 2007-05-19
Try adding the port under "allow service".

---

### Post by AlexenderReez on 2007-05-19
:lolflag::lolflag::lolflag:

ubuntu itself come default prevent port 6881 because crackers can break to you computer mostly using
that port.....

enable it....terminal
> sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT


don't forget to disable it after use.....:):):)

> sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

---

### Post by OffHand on 2007-05-19
It should be like this:

---

### Post by zhinker on 2007-05-19
Thanks for your input guys, but I still can't be sure about what's working and what isn't.  My download speed's up to 10 kb/sec max at some times, but I know if I was downloading this torrent with Utorrent in windows I'd be getting 50-100 kb/sec download speeds.  Might bittorrent be using more ports than just 6881?  Because firestarter still seems to be blocking a lot of ports and I'm wondering what the heck they are.  

I hate the bittorrent program, it doesn't give you any information at all about what's happening.  I used Azureus before on Ubuntu but now for some reason when I try to open it the program opens up completely but then shuts down at once.  Sorry for adding this problem on here as well, but I'd appreciate it if anyone could give me some help?

Edit: I attached some screenshots as well

---

### Post by Acglaphotis on 2007-05-19
Maybe there arent enough seeders?

-Acgla

---

### Post by zhinker on 2007-05-19
> **Acglaphotis said:**
> Maybe there arent enough seeders?

-Acgla
Nope, I just looked at the tracker's health right now and there are "2574 Seeders / 1192 Downloaders"
It should be downloading really fast (it would have in XP)

---

