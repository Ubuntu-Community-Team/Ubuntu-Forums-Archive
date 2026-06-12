---
title: "Using Backup Restore"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Ric95 on 2007-03-25
I just noticed Edgy has the "Simple Backup Suite". Cool. That was the one feature I like about Windoze :)
So I made a backup, but the only trouble I've had with Ubuntu is loosing X after updating. ( I guess the Nvid driver gets updated at different times than the kernel.:( ) 
Anyhow, if I loose video, how can I restore to the backup?

---

### Post by aysiu on 2007-03-25
According to [this page](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html), it seems you need X in order to use Simple Backup Restore.

---

### Post by Ric95 on 2007-03-25
I hope not. A simple terminal command could be a necessity for this.

---

### Post by Ric95 on 2007-04-01
Some progress. 
I broke Edgy. Now I'm trying to restore it from command prompt.:(
I read the directory with: dir /var/backup
it read a long name with date and username. I should have renamed it something short....bob?
the command to restore is srestore/backup file path & name/ target location. Like this:
 > sudo srestore.py/var/backup/[ mybackupsfilename]/ home/username-desktop/old
I had to tweak it a lot to get anything happening, but I still get an error about some file missing. 
has anyone succeded doing this?

---

