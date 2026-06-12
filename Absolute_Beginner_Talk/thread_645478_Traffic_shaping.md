---
title: "Traffic shaping"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-12-20
howdy.

I'm looking for a really simple way of shaping my uploads on a ubuntu box.

I pretty much want to limit the upload to 4kb/s or around that area.

Currently im not fussed at all about specific packets and all that. If the max outbound speed is 4kb/s i'll be fine.

So how would i do this?. It's really confusing...

---

### Post by candtalan on 2007-12-20
I have been using ktorrent. It is a little heavyweight, but I have found it to be easy, excellent, and a pleasure to use. I happen to use kubuntu mostly, so if you install itinto ubuntu via say- synaptic you can expect a bunch of kde libraries to come too. good luck

---

### Post by 13ojo on 2007-12-21
ahh well it's a GUI-less server box.

Mainly for torrents it's seeds via torrentflux b4rt.

I just want to make sure the upload is capped globally on the box (torrentflux uses bittornado) which means i can only control each individual torrent.

I almost want to trick it to believe that it's net connection's upload is just 4kb/s

---

### Post by tab80 on 2008-01-08
Hi

in that case you should use rtorrent
[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

or Enhanced cTorrent with CTorrent Control Server
[http://www.rahul.net/dholmes/ctorrent/ctcs.html](http://www.rahul.net/dholmes/ctorrent/ctcs.html)

Both have upload/download limiting capabilities.

---

