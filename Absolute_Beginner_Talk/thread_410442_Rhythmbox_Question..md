---
title: "Rhythmbox Question."
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-04-15
Hello all again, another question about Ubuntu. I am planning on reconfiguring my partitions on my drives and doing clean installs of both Ubuntu and XP (still need it for just a few last things...) and I am curious is there a way to export my play lists from rhythmbox? is there an xml or other file somewhere? Easy question this time :P.

---

### Post by starcraft.man on 2007-04-16
Ummmmm no one have an answer?

---

### Post by gh0st on 2007-04-16
I'm not an expert on this but I've just had a look to see if I can work it out. There is definitely an option to "load playlist from file" on the menu but I can't see an option of export to file anywhere. I had a look through the hidden directories under "/home" thinking there would be one called ".rhythmbox" but there isn't. Rhythmbox must store the playlists somewhere though so I suppose it's just a matter of finding it and copying the files. Then using "import from file" to get them back in.

I'm not sure of this I'm only hypothesizing here but I think the logic is sound :)

If I can find a location for the files I'll let you know.

---

### Post by gh0st on 2007-04-16
No wait I found it :D I was over complicating the problem.

If you highlight a playlist then go to "Music / Playlist" on the menu is has an option to "save to file". It's not there when you don't have the playlist highlighted, I was looking for a context menu or something. It's a bit confusing. could maybe do with some work by the developers so you can right-click a playlist and export to file. That would make a lot more sense.

It works for me and I can export to M3U or PLS. Hope that solves the issue for you, good luck :D

---

### Post by starcraft.man on 2007-04-16
Thanks very much gh0st, geez, I was looking all over for that... guess I'm kinda used to it being a main option in file the way firefox exports and imports bookmarks. Now I'm happy I don't have to remake my 40 or so playlists. 

I hope Feisty is released on time, I am eagerly awaiting it to repartition all of my drives.

---

### Post by gh0st on 2007-04-16
No worries man, I thought it would be on the "file" menu myself, just under "import" would be the obvious place but it wasn't that easy. They need to sort that out, finding the feature isn't easy at all. I took me ages to work out, things shouldn't be that difficult.

Glad I could help :D

---

### Post by hagfish on 2007-12-19
In answer to the question, "where is my rhythmbox playlist?" You can find the file "playlists.xml" at:
/home/yourUserName/.gnome2/rhythmbox/

---

