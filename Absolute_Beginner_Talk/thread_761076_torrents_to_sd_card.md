---
title: "torrents to sd card"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by gnomes11 on 2008-04-20
i am new to linux and use Xubuntu and would like to have my torrents download to my sd card  i have rtorrent and couldnt find out how to do it i need some one to help me do it on rtorrent or tell me what program can do it and how

---

### Post by joshrobinson on 2008-04-20
when you put in your sd card, it should mount to a folder in /media
so when your saving your torrent, browse to /media and find what one is your sdcard and save there

---

### Post by Iandefor on 2008-04-20
joshrobinson, that won't work, since gnomes11 is using rtorrent. No UI to browse in.

The rtorrent [manpage]("http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html") says that you should pass -d [directory] on the command line to set the default download directory to [directory]. You can also hit control-O before activating the torrent to change the download directory.

---

### Post by joshrobinson on 2008-04-20
> **Iandefor said:**
> joshrobinson, that won't work, since gnomes11 is using rtorrent. No UI to browse in.

The rtorrent [manpage]("http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html") says that you should pass -d [directory] on the command line to set the default download directory to [directory]. You can also hit control-O before activating the torrent to change the download directory.

sorry didnt know rtorrent was a command line torrent client, i assumed it was a regular old client

---

