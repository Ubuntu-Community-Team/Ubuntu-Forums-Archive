---
title: "terminal bittorrent?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-03-28
hi,

download bittorent via apt-get install bittorrent.

how do i run it?

I DON'T want any GUI, just text, and to download to a folder i choose.

ive sshed into this machine and want it to download some stuff via bit torrrent.

but there's no syntax or anything anywhere? everyone uses GUI's.

---

### Post by Bachstelze on 2007-03-28
```
btdownloadcurses file.torrent
```

man btdoxnloadcurses for the list of available options.

---

### Post by cyberdork33 on 2007-03-28
You might want to use screen with this. That will allow you to logout, and then log back in to check on the torrent later.

---

### Post by 13ojo on 2007-03-28
im using screen and a (python? bittorrent-curses)


how do i open ip table ports?.

ill set up everything (router) to work with this, cause ive manged to get a download going in screen etc (though i never trust that its workinG).

but im getting real slow downloads and no uploads as of now. though the torrent isnt very spectucular

---

### Post by 13ojo on 2007-03-31
thought id mention.

btdownloadcurses is not a command in the terminal.

and sudo apt-get install btdownloadcurses fails.


*shrugs*. is bittorrent-curses the same? or do i have an older verion, cause it seems to lock up the server a bit.

---

