---
title: "Old World Mac-DVD Player"
date: 2006-07-30
forum: Apple PPC Users
---

### Post by Uta on 2006-07-30
I have an old world mac running the latest Dapper kernel and the system is stable. I used Easy Ubuntu to install the needed multimedia files. I have Real Player audio working (no video, probably not possible?) but my question is about playing a DVD movie. I installed an Apple DVD player which is recognised by the system, I installed Dapper with it, it plays audio CDs, but ran into major issues when I first tried to play a DVD movie. The DVD opens Totem player which messes up the over-all display, menu bars turn yellow, the background color shifts and it can't play the DVD(this only happens with Totem with a movie dvd, not an audio cd)... so I installed Kaffeine-xine, and so now both players are trying to play the DVD. How do I set which player opens and #2, is it even possible to play DVDs (film) on an OWM.
Thanks!

---

### Post by Uta on 2006-08-01
I have answered a few of my own questions and created new ones. Yes it is possible to play DVD movies with an OWM and the discoloration I was getting when a disc was inserted was due to not having loaded the right modules for for ATI Rage 128 card at boot.This post helped me: [http://www.ubuntuforums.org/showpost.php?p=1280246&postcount=19](http://www.ubuntuforums.org/showpost.php?p=1280246&postcount=19)
I also solved the default app to open upon a DVD insertion, so now the issue I have is a weird one. I have an internal DVD player via an IDE/PCI connect and a DVD Player in an external FW box. The FW box DVD Player works fine but the DVD internal player has permission issues. Everytime a DVD is mounted (via the internal DVD Player) it thinks it's own by root, therefore the internal drive can't play it but when the DVD is insert via the FW box DVD player, (the permissions on the same disc) are for my user (and it's able to play the disc)? Strange. How do I sort this out? Thanks!

---

