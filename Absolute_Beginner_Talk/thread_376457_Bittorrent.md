---
title: "Bittorrent"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-03-04
Hi All:
I am trying to get bittorrent going here.  It works, but the best I get is yellow.  I have used bittorrent before, on "that other operating system".  I had port forwarding set up correctly then.

I have used the same range of ports with this install, but the best I get is yellow.  Is there somewhere within Ubuntu where I have to open these ports?  I have checked them at shields up, and they are stealthed.

Any help would be appreciated.

Thanks,
Ziffnabb

---

### Post by RomeReactor on 2007-03-04
Hi. Try installing Firestarter; it's a frontend to iptables, so you can manage your firewall graphically. Then add a new rule called Bittorrent (or whatever you like) and open ports 6881-6889.

```
sudo apt-get install firestarter
```

Or search for it in Synaptic.

---

### Post by Kuoi on 2007-03-05
For torrents I can only recommend to use Wine + Utorrent.
Much faster than all Ubuntu torrent clients.
I don't use wine for anything else , but after using about all torrent clients in ubuntu , I just knew that their 'speed' was abnormal low.
I've replied to a treath before that after installing Wine+Utorrent , Utorrent checked the partially downloaded Torrents , and resumed them at much hgher speed.

Just a tip , Kuoi

---

### Post by Drakkor on 2007-03-05
What torrent client are you using ?

---

