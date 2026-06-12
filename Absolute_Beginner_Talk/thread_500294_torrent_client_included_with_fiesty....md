---
title: "torrent client included with fiesty..."
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-13
When can I go to optimize to client included with fiesty? set ports etc.

---

### Post by wildseven on 2007-07-13
Did you check the config file?

---

### Post by woodsonoversoul on 2007-07-13
how can I find that?

---

### Post by woodsonoversoul on 2007-07-15
bump

---

### Post by ron999 on 2007-07-15
> **woodsonoversoul said:**
> When can I go to optimize to client included with fiesty? set ports etc.
I don't understand this question.

---

### Post by woodsonoversoul on 2007-07-15
sorry, when = where

---

### Post by John.Michael.Kane on 2007-07-15
This may be of use.
[HOWTO: open ports (for bittorrent?) from the command line]("http://ubuntuforums.org/showthread.php?t=331161&highlight=torrent")
[command line parameters for BitTorrent]("http://dessent.net/btfaq/cmdline.shtml")
[Tip: Fix extremely slow BitTorrent speeds with port forwarding]("http://ubuntuforums.org/showthread.php?t=287598&highlight=torrent")

Also if you need the gui for torrent app installed with 7.04 run
```
gksudo aptitude install bittorrent-gui
```


If you want to try another torrent program have a look at these guides.

[HowTo - Transmission Bittorrent client]("http://ubuntuforums.org/showthread.php?t=244677&highlight=torrent")
[HOWTO: Transmission Bittorrent client second version]("http://ubuntuforums.org/showthread.php?t=220149&highlight=torrent")
[HOWTO: Install Azureus (newest, non-repo way)]("http://ubuntuforums.org/showthread.php?t=144546&highlight=torrent")
[[HOWTO]Install Deluge 0.5.1.90]("http://ubuntuforums.org/showthread.php?t=487893&highlight=torrent")

---

### Post by woodsonoversoul on 2007-07-15
thanks a lot Plissken, following the steps listed in that first link seem to have helped.

One more quick question (I'm sick of all these torrent questions but...). Why does the speed vary so greatly? Mine might start off at 90 kb/s and then slowly trickle down to 0 kb/s and then eventually work it's way back up. Why is this?

---

### Post by John.Michael.Kane on 2007-07-15
> **woodsonoversoul said:**
> thanks a lot Plissken, following the steps listed in that first link seem to have helped.

One more quick question (I'm sick of all these torrent questions but...). Why does the speed vary so greatly? Mine might start off at 90 kb/s and then slowly trickle down to 0 kb/s and then eventually work it's way back up. Why is this?


It depends on the torrent, As well as your upload capacity, and torrent settings.

It also will depend on other peers' settings and upload speed, 

it will also depend on the number of seeds/peers in the chain. As well as the latency between peers, etc.

in the end your mileage will vary.

---

