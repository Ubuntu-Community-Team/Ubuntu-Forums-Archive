---
title: "Bittorrent file extentions"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by groping_blindly on 2008-01-20
Silly question time again . . .  I'm playing with Bittorrent under Feisty, and am having trouble with restarting torrents.  Bittorrent will only allow me to restart files with a *.torrent extension, but so far all the torrents I've tried downloading have been *.zip or occasionally *.rar files.  When I search for half-finished downloads on my system, the app doesn't see these files and won't let me use them to continue to the download.

Meanwhile, I haven't even seen a torrent the has a *.torrent extension.  What's going on?

I want to check out Deluge too, but I keep getting bad or unverifiable .debs.  :(  Is it  in the repositories?

---

### Post by RomeReactor on 2008-01-20
Hi. Resuming from half-finished torrents with th default BitTorrent client requires a **.torrent** file to continue. If you don't have that file, try downloading it from wherever you originally started the download. Once you get the .torrent file, just double-click on it and it will ask you if you want to resume the download.

Deluge is not available from the repositories yet; get it [here]("http://download.deluge-torrent.org/index.php?dir=ubuntu/gutsy/0.5.8.1/&file=deluge-torrent_0.5.8.1-1_i386.gutsy.deb").

---

### Post by groping_blindly on 2008-01-20
Hey, that was quick.  Thanks.

Ok, that makes sense.  So do I need to do something special to make sure I'm downloading a *.torrent?  So far, I've got various compressed files, and a couple of the torents turned into whole directories, but no nice simple torrent files.   Everything I've got so far is useless, I think.

---

### Post by shirilover on 2008-01-20
A .torrent file is just a small file containing meta-data and hashes of the file(s) to be downloaded. Most .torrent files are typically <50 kiB in size depending on the size of the file(s) hashed and the piece size.

---

