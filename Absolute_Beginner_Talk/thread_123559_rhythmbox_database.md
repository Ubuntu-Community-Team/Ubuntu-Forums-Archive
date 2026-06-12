---
title: "rhythmbox database"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by jthirt on 2006-01-30
I am new to linux/ubuntu but I really like it. I work in IT and I'm a bit sick & tired of MS. So discovering ubuntu has been a real refreshment. 

I have so far installed a few Pcs with ubuntu, including a fairly old laptop that I use as a jukebox playing music off from a DVD or internet radio stations. 

I'd like to know if there is any way to access the rhythmbox database with a text editor or some other tool ? For example I would like to export and/or add radio stations and it's a bit of a pain to do that manually on each Pc for every station.

Also, I would like to amend some of the Albums, Artists, Titles quickly or in batch but I haven't been able to find anything that looked like it stores the rhythmbox data. Now that music is burned on a DVD I cannot amend the mp3 TAGs. But If I could amend the database pointing at them, that would do the trick for me. 

Help would be appreciated.

---

### Post by Gustav on 2006-01-30
I think it's in ~/.gnome2/rhythmbox/rhythmdb.xml

---

### Post by doclivingston on 2006-01-30
As Gustav said, the database and playlist files are stored in ~/.gnome2/rhythmbox/.

One things to watch out for, is that Rhythmbox will re-scan the file and overwrite the metadata in the database if the file changes. If the file's modification timestamp is newer than the "mtime" timestamp in the db, then you will lose your manual changes.

---

### Post by jthirt on 2006-02-01
Thanks guys. 

I had tried to find this but I was obviously not looking in the right place or didn't include hidden files so I missed it. 

That should do the job just fine.

---

