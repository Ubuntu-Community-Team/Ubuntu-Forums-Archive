---
title: "rsync - OS X &amp; Ubuntu"
date: 2010-10-19
forum: Apple Hardware Users
---

### Post by kpholmes on 2010-10-19
i want to mirror the itunes media folder on my imac to the music directory on my ubuntu server that runs subsonic (a music media server). my rsync version has been updated to 3.0.7 on the mac and the linux box. ive also done lots of searching on google and came out with this command which executes from the mac with ssh keys installed and working 
```

rsync -r  -e ssh --delete  "/Users/kevin/Music/iTunes/iTunes-Media" kevin@atom:/home/kevin/Music
```

on the remote server i get all the folders inside the iTunes-Media folder but none of the mp3 files.

suggestions?

---

### Post by conundrumx on 2010-10-19
Well you probably didn't need to bring rsync all the way up to 3.0.7, and this isn't actually an OSX/Apple specific question...

All that being said, try throwing the -v (verbose) option on and see if that helps any.

---

