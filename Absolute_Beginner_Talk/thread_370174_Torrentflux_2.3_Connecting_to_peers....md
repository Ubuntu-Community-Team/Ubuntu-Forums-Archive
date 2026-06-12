---
title: "Torrentflux 2.3: Connecting to peers..."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-02-25
Hi there,
i recently installed Torrenflux 2.3 and i downloaded a couple of torrents quite quick.
The problem is, after yesterday it doesn't download anymore. It stays at "connecting to peers" forever. I didn't change anything of settings (ports 49160-49300 are forwarded).

Does anyone know what could be the problem?


Iarwain

---

### Post by tribble222 on 2007-02-25
Do the torrents work in other torrent programs?

---

### Post by Iarwain ben-adar on 2007-02-26
Yes they do:
having around 500 seeders is working in azureus and deluge.


Strange thing is: i removed the torrent, searched for another, and it started.
I'll test if the previous torrent works or not as well..

EDIT: the previous one doesn't start in TorrentFlux..


Iarwain

---

### Post by Iarwain ben-adar on 2007-02-27
Bump:

I can download certain torrents (torrents from [this](http://lesbianocracy.com:54321/) tracker)

But torrents from other trackers are impossible, they stay on "connecting to peers" like with [this](http://inferno.demonoid.com:3391/announce) tracker.

I suggest this being something about my cookies..

P.S. Mods: if you feel that the linking is inappropriate, please delete them.


Iarwain

---

### Post by detectiveinspekta on 2007-03-30
I'm using TF, downloading at 0KB/s, while azureus is going at 100KB/s on a single port. I have opened up ports 65500 to 65534 dedicated to TF. No luck for me.

---

### Post by Iarwain ben-adar on 2007-03-31
Hi there,

My stuff works like this:

download the .torrent via the pc, and then choose 'upload' on your TF-page.

This way they all work for me


Iarwain

---

### Post by detectiveinspekta on 2007-03-31
I am having a problem with the torrents working, it's happy to sit there on 0KB/s. Azureus gives aobut 100KB/s, where is the problem.

Also when you look at the deatails of the torrent it says
Seeds:6+0.642, Peers 3, what is the 0.642 supposed to mean and shouldn't it be making around 300 connections in total.

---

### Post by Iarwain ben-adar on 2007-03-31
Well, i don't know much about TF,
but for the 0.642 part, that's the amount of the file available by peers i think.

Why don't you try the forums there?


Iarwain

---

### Post by detectiveinspekta on 2007-04-01
Solved my problem. Router wasn't correctly forwarding ports so I had to make a few individual port forwarding rules.

Next problem: The torrent dies randomly. Green light still showing it goes from 20KB/s (normal for particular torrent, tested with azureus) to 0KB/s. I think it has to do with the connection reseting because when I restart the torrent it works again. But shouldn't TorrentFlux be able to handle such a thing occuring!

---

### Post by Iarwain ben-adar on 2007-04-01
Well, i read something about that on their forums, and they said it was something about Apache resetting.. Try a search, it should pop-up some nice results ;)


Iarwain

---

