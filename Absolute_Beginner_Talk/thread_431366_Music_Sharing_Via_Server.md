---
title: "Music Sharing Via Server?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by mlissner on 2007-05-03
Hi, software choice question for you all:
I've got an extra computer in my house, and I want it to serve up and share my music with my roomies. So far, I've figured out how to set up apache and just serve the directories, but it's a pretty lame method of sharing.

Is there a CMS, or something similar into which one can upload their music and then it will sort it by id3 tags and serve it up all pretty-like?

The other problem is deleting duplicate files. If I upload my files and my roomie does, the ideal program would make removing the duplicates easy. Also, if it had a feature that would allow me to upload my whole music directory, and have it know which new files needed to be uploaded, that would be incredible.

Any thoughts out there? Thanks all.

---

### Post by HornedBeast on 2007-05-03
I dont know of any CMS's... but you could try running SAMBA (smb server) and sharing a dir on your Ubuntu machine so other computers can see it.

I beleive Samba can be installed by the default Ubuntu repository using the Synaptic Package Manger.

That would make more sense than sharing using Apache

That way the client machines could organise the MP3's using whatever software they wanted.

---

### Post by mlissner on 2007-05-04
SAMBA is a thought, but I'm looking for something much less like a file server, and more like a web interface music browser. A major part of the problem is that the song information is all stored in id3 tags, not the filename itself. This works great in a music browser, but not so great in a file browser.

---

