---
title: "torrent slave"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-02-11
okay since i download alot of torrents legal torrents of distros trying to build it back up is there anyway can i turn my old server into a torrent slave like where do i start at? ssh is already installed and configured and NFS so i can get to the torrents where else should i start?

---

### Post by p_quarles on 2008-02-11
Have you tried rtorrent? It's a command line client, and has all the features of any other client.

---

### Post by fedex1993 on 2008-02-11
yeah i have used rtorrent the problem is that i want to be downloading 24/7 but i want the bandwith or what ever sends out like how much of the speed limit or how much it is aloud so i doesnt rase my ping on my network

---

### Post by p_quarles on 2008-02-11
You can put a speedlimit on it by changing the download_rate = setting in ~/.rtorrent.rc.

---

### Post by fedex1993 on 2008-02-11
eww i can? thats cool i wonder like what are the variables

---

### Post by p_quarles on 2008-02-11
There's a full list of variables in the rtorrent man page. Everything you can do with something like Azureus or Deluge, you can also set with the rc file.

---

### Post by fedex1993 on 2008-02-11
thats pretty cool i like that alot torrent rocks :)

---

### Post by fedex1993 on 2008-02-11
oh but the only problem is says can not read rtorrent.rc in ~/

---

### Post by kaiju on 2008-02-11
you might have to create that file first. here is a sample from the rtorrent website:
[http://libtorrent.rakshasa.no/attachment/ticket/682/rtorrent.rc?format=raw](http://libtorrent.rakshasa.no/attachment/ticket/682/rtorrent.rc?format=raw)

you should save that to ~/.rtorrent.rc and then edit it with your favorite text editor (note that it will be a hidden file because of the dot in front).

---

### Post by kaiju on 2008-02-11
oh, and another thing. you'll find some info on scheduling download rates here:
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

---

### Post by il-luzhin on 2008-06-09
hey folks,

while building a torrent slave I thought I'd put the app launch in /etc/rc.local of my slave machine (8.04 server).

How do I recall this app to the fg terminal with a PID?

---

