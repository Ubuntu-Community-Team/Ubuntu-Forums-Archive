---
title: "making backups"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by jonpon on 2007-11-02
Hi folks, Is it possible to backup my entire system on my external hard drive **without ** compressing it? Space is not an issue.
I tried the "HOWTO back up and restore system" way using the backup .tgz but when I tried to restore it failed and now all is lost!

---

### Post by ddrichardson on 2007-11-02
Yes using dd from the command line ([here]("http://blog.lynxworks.eu/?p=12")) or partimage. I'm sure there are GUI ones too.

---

### Post by jonpon on 2007-11-02
WoW That looks simple enough thank you!

---

### Post by mivo on 2007-11-02
If you only want to back up some folders, or make a total backup and then only transfer the files that have changed since the last backup (and/or remove files in the destination that were removed in the source location), rsync is a pretty good tool. I use the GTK frontend [Grsync]("http://www.opbyte.it/grsync/") for super-easy control. (I keep a backup on another machine that I sync daily)

---

### Post by newlinux on 2007-11-02
I second rsync. I use a cron job with rsync to back up all the necessities. Before that I used grsync. I know you are steering away from compression, but sbackup is a simple to use back tool as well, and restores should be pretty easy. I used to use sbackup until I wanted more control with my own scripts...

---

### Post by newlinux on 2007-11-02
a good link for backups:

[http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup)

---

### Post by Insightfill on 2007-11-05
Also look into "BackupPC" and "rsnapshot".

---

