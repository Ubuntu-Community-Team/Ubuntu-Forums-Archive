---
title: "bittorrent troubles"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by struess on 2006-07-08
hey guys,
just installed ubuntu a couple days ago and have been tinkering just about non-stop.  despite best efforts, i can't seem to get bittorrent programs (tried bittornado and azureus) to download files.. i can open the .torrent files with them, but the download refuses to start.  sometimes the program gives a "rejected by tracker" error, sometimes it doesn't -- but the file never starts downloading.  i'm using firestarter as a firewall, and i allowed ports 6881-6889 (the default when you create a rule for BitTorrent).. but no soup for me. 
in the windows bittorrent client i had, it required at least one file to be shared in order for you to start downloading.  is this the case here?  ..or something far more sinister...?

thanks for the help :)

---

### Post by catlett on 2006-07-09
I never had an issue with linux and bittorrents. But to make sure go to a bittorrent site and download something that is listed with lots of seeders. This way you wil know if your earlier attempts were because of no seeders or because something is configures incorrectly.

In ny Daper install, I download a torrent, I let the downloader open it and bittorrent automatically starts and handles the download.

---

### Post by struess on 2006-07-09
yeah, there were 26 seeders on the torrent i was downloading, but still no luck.  i did pretty much the same thing as you... download the torrent, open it with the program, and watch.  what program were you using, outta curiosity?  thanks for the good word.

---

### Post by catlett on 2006-07-09
Just bittorrent that is installed by default in Dapper.


Did you  try disabling the firewall altogether and see what happens?

---

### Post by struess on 2006-07-09
w00t!  disabled the firewall, and that produced a new error... i kept getting rejected by trackers for some reason.  soooo i kept trying different torrents (still using bittornado), finally one just clicked.  thanks for the help.

---

