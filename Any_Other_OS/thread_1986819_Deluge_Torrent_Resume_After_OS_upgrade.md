---
title: "Deluge Torrent Resume After OS upgrade"
date: 2012-05-25
forum: Any Other OS
---

### Post by sites on 2012-05-25
I just upgraded to Mint 13, Maya, with cinnamon.  Before doing so I had a few torrents in Deluge that were nearing completion.  Now that I have all files transferred to a new home directory, I'd like to resume those downloads where they left off.  I pulled in the config folder from the old home directory, but all the torrents started over from the beginning.  How can I get them to resume using the previously downloaded files?

---

### Post by rai4shu2 on 2012-05-25
If you overwrite your new partial files with your old partials (you did backup your old files, right?), then that should allow any client to resume your download as that is built in to the protocol for bittorrent.

---

### Post by sites on 2012-05-25
Yes, I moved the contents of my old home directory over to the new home directory.  But the transferrs stared over again anyway.  The old files that were downloaded are still there, but the file sizes are a bit odd.  For example, one file shows up as a 648mb total download in Deluge, but the same file in ~/Downloads shows a file size that is larger than that.  It's confusing, because previously completed downloads are showing several MB larger sizes in Nautilus than they should.

---

### Post by rai4shu2 on 2012-05-25
Going by file size isn't really a good idea with torrents. You should trust what your client is telling you, not your file manager.

---

### Post by Perfect Storm on 2012-05-26
Moved to Other OS/Distro Talk.

---

### Post by sites on 2012-05-26
> **rai4shu2 said:**
> Going by file size isn't really a good idea with torrents. You should trust what your client is telling you, not your file manager.

Either way, it's not really the issue.  After saving the partially downloaded files and copying the deluge config folder over, the torrents are in Deluge but they are all restarting the downloads.  They are not picking up where they left off.  That's the problem.  One of my torrents is a large collection of maps for gps that doesn't have many seeders.  It took a couple of weeks to get it up to 90-something percent & I'd rather it pick up at 90-something percent instead of starting all over again.

---

### Post by rai4shu2 on 2012-05-26
If it's restarting at 0%, you need to *completely* quit out of Deluge, then delete the new partials, replacing them with your old partials. If it then persists in restarting at 0%, then it's a bug in Deluge.

---

### Post by sites on 2012-05-29
Figured it out.  After copying the Deluge config folder over to my new home directory Deluge was downloading to my old home directory.  Since I had already moved the contents of old-home Downloads, the torrents started all over.  Not a bug, just an oversight on my part.

---

