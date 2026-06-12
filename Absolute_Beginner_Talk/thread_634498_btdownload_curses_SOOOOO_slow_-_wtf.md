---
title: "btdownload curses SOOOOO slow - wtf?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by jhunt3r on 2007-12-07
got a Gutsy box here and I'm downloading the same torrent side by side with a windows box. in comparison my windows box is downloading a VERY well seeded file @ 70kb/s, while btdownloadcurses (GG)  is downloading @ 2.3kb/s. I'm limited to command-line based BT clients, and this is the only client I've tried thusfar.

what args do folks use when running btdownloadcurses to get it to perform to the best of its ability? I've tried limiting max_uploads to 1, setting my max_upload_rate to -1, --minport to 6881 -- and nothing! this thing still crawls! 

network-wise, there no diff btw the 2 boxes. it's on the same subnet as my windows box here, and the windows box has no special port forwarding/NAT/DMZ foo set up in my Netgear DSL router.

any help would certainly be appreciated. :)

---

### Post by Law506 on 2007-12-10
I was having similar problems with slow speeds till a friend came over.

First, I recommend you set up your router (If you have one) to port forward to you and match your torrent client to that port.  If not router, then disregard.

Also, I have tried numerous clients and the best thus far I have used is Deluge.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

Download for the right version of linux your on and install.  I have gotten my fastest speeds with this client and it is very user friendly.

---

### Post by nutter78 on 2007-12-12
try rtorrent - probably the best client there is:)

The port forwarding is a good idea, but also some "torrent servers" dislike certain clients, which can drastically reduce your speeds. rtorrent can masquerade as other clients :) :KS :)

Give it a go - u won't be disappointed

---

