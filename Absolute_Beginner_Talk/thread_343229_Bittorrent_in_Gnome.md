---
title: "Bittorrent in Gnome"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by topic58 on 2007-01-21
Hi all, I'm using Ubuntu 6.10. When trying to download files using Bittorrent I'm only allowed to download one file at a time. I have two pc, the other running Ubuntu 5.10. No problem at all in 5.10. Now using a router with both pc online. Can't find any problems in Firestarter, even tried allowing ports for Bittorrent in rules, but no. Anyone got a clue here?? I get this message: Couldn't listen (98, 'Address already in use')

---

### Post by RomeReactor on 2007-01-21
Whenever  i try to download multiple .torrent files i always use the terminal (don't know if it can be done in gui; i store my .torrent files in "/home/sho/torrents", so i do:

```
btlaunchmanycurses /home/sho/torrents
```

Hope this helps you.

EDIT: Oh, sorry: did you mean to download a bittorrent file on two separate boxes?

---

### Post by topic58 on 2007-01-21
I'm not using terminal here, just gui for Gnome BitTorrent. It seem to work in Bittornado though (strange). But Bittornado is so slow compared to BitTorrent. How come is that?

---

### Post by fakingit on 2007-01-21
I used to use BitTorrent then I discovered BitTornado which was better imo. Then I discovered uTorrent. Use it all the time now, superb :D  (uTorrent is a windows app, however it works perfectly under wine).

---

### Post by peresko on 2007-01-21
hmmm...download utorrent (standalone version)
wine utorrent.exe
...
oh yeah :)

---

### Post by Pobega on 2007-01-21
> btdownloadcurses <URL to torrent>

My personal choice.


Or, is this a connection problem between two PCs?

---

### Post by wildkarde on 2007-01-21
I recommend you use another client.  I recommend qBittorrent.  
[http://www.qbittorrent.org/]("http://www.qbittorrent.org/")

---

### Post by topic58 on 2007-01-21
Problem solved. Made a change in .gconf-settings. Max and min port had the same number. Changed maxport. Thanx all. :D

---

### Post by jdarvwill on 2007-01-24
hmm, where can i find this file?

i have the same problem, but i cannot find the darn file :)

---

### Post by jut on 2007-01-26
I have the same problem too!

---

### Post by dougwolfe on 2007-02-03
Here is the solution!
[https://features.launchpad.net/distr...u/+ticket/2364]("https://features.launchpad.net/distr...u/+ticket/2364")

---

### Post by foolswisdom on 2007-02-22
> **dougwolfe said:**
> Here is the solution!
[https://features.launchpad.net/distr...u/+ticket/2364]("https://features.launchpad.net/distr...u/+ticket/2364")

I caught up with dougwolfe online, and as that link is broken, he was generous and told me the solution:

The max_port setting for bittorrent is set the same as the min_port, so there is only one port that can be used.  
1. Type gconf-editor
2. then navigate to apps->gnome-btdownload->settings
3.  Change the max_port to a higher number to allow for more connections.

This seems to be bug # 57039
[https://launchpad.net/ubuntu/+source/gnome-btdownload/+bug/57039](https://launchpad.net/ubuntu/+source/gnome-btdownload/+bug/57039)

---

### Post by rare HERO on 2007-08-19
Solution works great!

---

### Post by Cable on 2007-08-19
I see that you found a solution, great!  I would just like to throw in my suggestion for a Bittorrent GUI:  [Deluge]("http://www.deluge-torrent.org/").  It's an awesome client and is definitely making great progress.  I highly recommend it.

---

