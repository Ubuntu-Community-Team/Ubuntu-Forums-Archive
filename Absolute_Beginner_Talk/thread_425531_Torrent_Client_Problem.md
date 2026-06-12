---
title: "Torrent Client Problem"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Kerrisis on 2007-04-27
Hi all. =)

I decided to take the jump and move from XP to Feisty around the day it went gold. So far it seems to be working perfectly... with one small problem. Whenever I'm using a torrent client, it seems to utterly destroy my net connection. I have a 4Mbit ADSL link, but when I have torrents downloading under Feisty, even if they're only consuming 20-40k/sec, I get massive net lag (Ventrilo breaks up, pings of 800+ in CS:S, Google takes 60+ seconds to load in Windows or Linux etc.). I've tried several torrent clients (Azureus, Deluge, Transmission etc), all seem to have the same problem. This never happened under XP running uTorrent, so I can only assume it's something I've not set up correctly in, or something inherent to, Linux.

Any help anyone could offer would be greatly appreciated, please. =)

---

### Post by kelvin spratt on 2007-04-27
use ktorrent its as light as utorrent

---

### Post by BarfBag on 2007-04-27
I believe the torrent clients you listed are all Java based.  Java tends to be a resource hog.  It could be weighing down your Ram and causing your computer to act slow and weird.  Since you don't have connection problems in Windows, I can't think of any other explanation (plus, it's happened to me before).  Give KTorrent a try.

> sudo apt-get install ktorrent

---

### Post by starcraft.man on 2007-04-27
Let me suggest....

```
sudo aptitude install bittornado bittornado-gui
```

Never had any problems surfing even when I was nearly maxxed out on my connection download :)

---

### Post by Kerrisis on 2007-04-27
Looks like you guys were spot on. I installed Ktorrent, and the problems vanished.

Thanks for the help, it's greatly appreciated. ^^

---

