---
title: "locate mix up?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by bobbyw on 2006-08-22
I type locate "prison" and it should show all files with "prison" in it on my system, right?

then what is this?


meathead@quack:/box/user$ locate prison
/box/.torrents/prison.break.201.hdtv_lol.avi.torrent
/box/.torrents/prison_break_201_hdtv_lol_avi.stat
meathead@quack:/box/user$ locate prison.break.201.hdtv-lol.avi
meathead@quack:/box/user$ ls
prison.break.201.hdtv-lol.avi
meathead@quack:/box/user$ locate prison.break.201.hdtv-lol.avi
meathead@quack:/box/user$ ls
prison.break.201.hdtv-lol.avi
meathead@quack:/box/user$

---

### Post by Major_Stitch on 2006-08-22
As far as I'm aware, locate uses an index like Goole Desktop, MSN Desktop Search, etc. which has to be made through work and time. I'm not sure but using, or modifying a file adds it to index.

---

### Post by mcduck on 2006-08-22
locate indeed uses a database instead of actually searching through your harddisk when you run it. So if you have recently added files to your system locate won't find them.

To update locate's database run this command: 'sudo updatedb', and after that locate should find your files.

If you want normal search, use 'find' instead of locate. But locate is way faster than find..

---

