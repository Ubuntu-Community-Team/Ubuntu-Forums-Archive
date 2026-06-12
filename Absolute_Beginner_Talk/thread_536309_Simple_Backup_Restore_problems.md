---
title: "Simple Backup Restore problems"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by n1418 on 2007-08-27
Hi, I've set up a weekly backup to another computer on my network.  

The first scheduled backup went well, as far as I can tell, and I can see the backed up files on the other machine.

However, whenever I try to restore one of the files in the backup, all that happens is a little dialog box pops up that says "Restoring..."  Even leaving the computer alone for hours does nothing.  The file doesn't restore, and the dialog box never goes away.

Anybody have any idea what's going on here?

BTW, I'm running Feisty x86.  The backup files are located on an XP machine downstairs, FAT32 partition (if it matters)

---

### Post by Duck2006 on 2007-08-27
What size is the backup file?

---

### Post by n1418 on 2007-08-27
2.5 mb for the full backup.  That seems awful small, but I get a full list of the contents when running Simple Backup Restore.  I'm a fairly recent windows convert, so I'm not real sure how efficient the compression is in this utility.  There are also some incremental backups in there, but they don't list the file I'm trying to get at.

I'm just trying to restore one file that I accidentally overwrote.  That file size should be around 125kb (word document).

On a second note, I can forgo the whole backup if anyone knows how to restore an overwritten file.  I have a ton of great programs to do it, but they're all windows unfortunately (including Ontrack).

---

### Post by beercz on 2007-08-27
Have a look at[ rsnapshot]("http://rsnapshot.org")

Uses rsync to backup only changed and new files.

Bit fiddly to set up, but once done, use crontab to schedule backups.

I backup every day, works like a charm :-)

---

### Post by n1418 on 2007-08-27
It just occurred to me that the file in question was on an ntfs external drive I have hooked up. 

I'm going to hook it up to my Win x64 laptop, and see what I can pull up.

---

