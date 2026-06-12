---
title: "Accessing Time Machine Data"
date: 2009-12-25
forum: Apple Hardware Users
---

### Post by Epamek on 2009-12-25
Is it possible to access files (specifically mp3s) from a time machine backup in Ubuntu?

All I can find are blank documents under user>myname>music for all of my backups.

---

### Post by Epamek on 2009-12-27
Very sorry to bump this, but I've revised my question and I desperately need help with this.

---

### Post by tom4everitt on 2009-12-28
Okay, so not being an expert on time machine, I suppose that it stores your files in some sort of database. Since you can't see your files directly, I think it might be hard to actually retrieve any of them without using time machine.

What I would do is to get to an osx system, choose restore from time machine backup somewhere (I think /Applications/Utilities/Migration Assistant or something). Perhaps you can choose to just restore your music folder. 

Once retrieved you shouldn't use time machine no more. Personally I don't because of exactly this problem. Instead you should read this guide:

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

which enables you to make several snapshots of your system (say one every last three weeks), with a minimum of copying and disk space usage. It will show all files perfectly in the open, and you will be in complete control. It will also give you some insight on how the file system works (the backup technique works for both os x and linux, and requires only built-in core utilities).

---

