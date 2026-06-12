---
title: "Folder Sync"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by bertlacy on 2007-08-27
Hey All,

I was wondering what was the best app for synci'n folders in Ubuntu.

I have a Music folder on one Hard drive and I want to sync that folder to another hard drive on the same machine.

---

### Post by Inxsible on 2007-08-27
Do you mean backup ?

Have a look at SBackup. Its in the repos.

---

### Post by bertlacy on 2007-08-27
> **Inxsible said:**
> Do you mean backup ?

Have a look at SBackup. Its in the repos.

I don't really want to 'backup' the data...

I just want each folder to mirror the other automatically when i drag a new file/folder to one of the directories, ie /home/user/Music

Make sense???

---

### Post by qpieus on 2007-08-27
If you like a gui, try unison. Or, if you want a command line app, use rsync. I don't think either of them will automatically sync 2 folders immediately after you add files though. I use rsync and make it sync periodically using cron. It's awesome, I sync the folders everyday automatically without even thinking about it.

---

### Post by por100pre1 on 2007-08-27
Grsync will do the job:

```
sudo apt-get install grsync
```

---

### Post by scxtt on 2007-08-27
cp -ur <source_folder> <destination_folder>

u = update "copy only when the SOURCE file is  newer  than  the  destination file or when the destination file is missing"
r = recursive

---

