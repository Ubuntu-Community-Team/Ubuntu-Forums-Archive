---
title: "Bittorrent (0 upload rate)"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by qabach on 2007-09-30
I'm a new user of Ubuntu (Feisty) and am trying my first torrent download, but it is very slow because I can't seem to do any uploading. 

Since the info provided by the default torrent handler was limited, I got bittornado and it's suggesting that I'm behind a firewall.

I have Firestarter installed, but it is not running, so I don't think that's my problem.

Is there some other reason that my computer wouldn't be allowing other bittorrent users to start connections with me?


I know very, very little about ports and other such internet/networking related things, so if possible, please keep any responses relatively simple

---

### Post by HermanAB on 2007-09-30
If you have a router, then you have to forward the bittorrent ports to your machine.  

You can check your own firewall rules with:
$ sudo iptables -L

and you can remove all rules with:
$ sudo iptables -F

Cheers,

H.

---

### Post by qabach on 2007-09-30
Should I go ahead and forward the entire range of ports that bittornado uses? (10000-60000 I think)

---

### Post by hotweiss on 2007-09-30
Forget about Bit Torrent. Download Deluge Torrent:

[http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)

---

### Post by qabach on 2007-09-30
Deluge worked fine from a fresh install. Thanks for the tip.

---

### Post by hotweiss on 2007-09-30
> **qabach said:**
> Deluge worked fine from a fresh install. Thanks for the tip.

Plus, Deluge will automatically open the needed ports for you.

---

