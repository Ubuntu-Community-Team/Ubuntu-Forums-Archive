---
title: "What are torrents? What do I need to download one?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-01-08
Moderators, if I have posted in the wrong forum, please do excuse me and move it to the appropriate one. 

My friend wanted a copy of Ubuntu, and as I didn't have one handy, I wanted to download the .iso file. However, for some reason all the mirrors weren't giving me a good speed. 

I saw .iso.torrent file. What is that? Do I just download it? How do I get an .iso file out of it to burn into the CD?

I know Ubuntu is free, but are torrents legal? I don't want to get involved with legal issues downloading torrents, so I wanted to make sure here with everyone. 

If I can not simply download a .torrent file, what do I need? Is there something on the command line that would help me? I prefer command line, since the computer is connected through the wired connection in my house (the one that acts as a server) has no GUI and everything is managed through SSH and/or web interface only.

So are there any CLI/web interface based .torrent downloaders? (Some equivalent of wget perhaps? Or can wget itself do it?) What do I do once I have it? 

Also, can somebody explain in general what torrents are? And what else I can use them for? 

(Remember, it has to be command line ! Thanks a lot !) 

Hari .S

---

### Post by earobinson on 2006-01-08
this should give you all the info on torrents you need [http://en.wikipedia.org/wiki/Bittorrent](http://en.wikipedia.org/wiki/Bittorrent)

cant seem to find a bit torrent command line program ill keep looking

---

### Post by UphillSkier on 2006-01-08
[QUOTE=earobinson] <snip>

cant seem to find a bit torrent command line program ill keep looking[/QUOTE]


Try  
```

man bittorrent-downloader
```
 in a terminal for a description of command line tools and a pointer to more webpages.

best wishes

---

### Post by super on 2006-01-08
try giving ctorrent a try. i've never used it before so if you decide to use it and it works well, let me know. you need gcc and openssl to run it (both available in repos).

EDIT: dang! forgot the link. [here you go]("http://ctorrent.sourceforge.net/?action=what")!

---

