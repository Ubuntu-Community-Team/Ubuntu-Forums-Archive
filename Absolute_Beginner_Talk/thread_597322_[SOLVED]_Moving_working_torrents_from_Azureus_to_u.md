---
title: "[SOLVED] Moving working torrents from Azureus to uTorrent"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-10-30
I have been using Azureus in the past. And it works extremely bad for what it should do. After that I moved to a testing period with uTorrent and I don't want to go back. Now I have to move the torrents I have - both working and seeding - to uTorrent without breaking something. What is there to do?

Cheers,
Sidd

---

### Post by rahimveron on 2007-10-30
1st thing would be to backup, just in case,; in Windows i had no problem migrating. Just open the torrents file again & redirect to the previous download folder(where your files are) & it will check for iths completeness and take over.
Again i mention just backup. And try this method with just one torrent to test if it works.

---

### Post by maybeway36 on 2007-10-30
Thats what I did with KTorrent when I installed Gutsy. (I delete my hidden settings when upgrading my distro, so I can get the full effect.)

---

### Post by juantovarm on 2007-10-30
Regarding the working torrents, just by opening the torrent file with uTorrent should be enough -i have done it but from the default gnome torrent application to ktorrent and had no problems whatsoever.

As for the uploading ones, i don't know

Hope it helps

Juan

---

### Post by siddartha on 2007-11-03
It works like a charm.

So
1. Stop the old (former) torrent application
2. If you keep the same directory structure from one torrent application to another just jump to step number 5
3. Move the working torrent files to the working torrent directory keeping the directory substructure
4. Move the torrents that are done (seeding) to the directory were the torents should be moved when you start seeding
5. If you set your former torrent application to add a suffix (extension) to the working files in order to avoid opening by the associated apps, than erase that by hand
6. Start the new torrent client
7. Load the associated .torrent files
... and everything is ok. You will lose the counters, as they get reset.

---

