---
title: "[SOLVED] Trouble Creating a Torrent with Deluge"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ghindo on 2007-11-15
I wasn't too sure where to put this topic.

I've been trying to use Deluge as my default BitTorrent client, but have run into a problem - I don't seem to be creating torrent files properly.  I've installed the "Torrent Creator" plugin, know how to select the folder I want, etc., but when I finish making the torrent, the status shows up as "Downloading," not "Seeding."  What gives?

---

### Post by jw5801 on 2007-11-15
Check that the "download location" of the torrent is set to whatever folder you made the torrent from. Otherwise it'll look for the files it's expecting in whatever the default download folder is.

---

### Post by ghindo on 2007-11-15
> **jw5801 said:**
> Check that the "download location" of the torrent is set to whatever folder you made the torrent from. Otherwise it'll look for the files it's expecting in whatever the default download folder is.Thank you for the response, but when I do that the same thing happens - the torrent shows up as Downloading, not Seeding.

---

### Post by jw5801 on 2007-11-15
hmm... I've never created a torrent with Deluge (I use kTorrent myself). Hang on and I'll give it a shot and report back.

---

### Post by jw5801 on 2007-11-15
Ok, many reasons I don't use Deluge! You can't tell it to store downloaded files in different directories, so you'll need to set the default download location to somewhere convenient (via edit > preferences) and copy the file/folder that makes up the torrent to this location. Secondly there doesn't appear to be any way to tell it to manually rehash the downloaded data. So after you do this you'll need to delete the torrent and readd it. After you add it, it should check through the already "downloaded" data and find 100% of it.

---

