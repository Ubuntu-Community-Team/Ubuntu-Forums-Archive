---
title: "Seriously: How does rsync work"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-28
Hi this is my first time using rsync, and im using it to make backup over ssh.
I using this script to make my backups of the home directory every day (70GB)
```
ssh rudolf@192.168.0.124 rm -rf /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.6 /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.5 /media/Backup_200GB/Home_Backup/backup.6
mv /media/Backup_200GB/Home_Backup/backup.4 /media/Backup_200GB/Home_Backup/backup.5
mv /media/Backup_200GB/Home_Backup/backup.3 /media/Backup_200GB/Home_Backup/backup.4
mv /media/Backup_200GB/Home_Backup/backup.2 /media/Backup_200GB/Home_Backup/backup.3
mv /media/Backup_200GB/Home_Backup/backup.1 /media/Backup_200GB/Home_Backup/backup.2
mv /media/Backup_200GB/Home_Backup/backup.0 /media/Backup_200GB/Home_Backup/backup.1
rsync -e ssh -a --delete --log-format="%%o %%t %%f" --link-dest=/media/Backup_200GB/Home_Backup/backup.1 rudolf@192.168.0.149:/home/rudolf/ /media/Backup_200GB/Home_Backup/backup.0/ > /media/Backup_200GB/Home_Backup/rsync.log
```
It seems like rsync runs forever even though no files have actually changed since the last backup I did.

Im thinking does this mean that rsync is going through the folders as if were to copy all files but then only copies over the changed files? meaning that every backup takes equal amount of time no matter how much data is tranfered

EDIT: Actually i think the scrip I use is wrong it seems like its copying everything over and not linking anything. If anyone can see whats wrong please tell me :)

---

### Post by tehet on 2007-09-28
```
mv /media/Backup_200GB/Home_Backup/backup.0 /media/Backup_200GB/Home_Backup/backup.1
```
makes you end up with no more bachup.0 because its moved to backup.1 So yeah rsync will have to start all over again.

---

### Post by kasperbs on 2007-09-28
Ok I thought that was what the:
> --link-dest=/media/Backup_200GB/Home_Backup/backup.1
was for, but apparently not..

thanks for your answer

---

### Post by Insightfill on 2007-09-28
Seems like you've already gotten your answer.  However, it still means you have to make a cp of the whole structure to keep rolling backups.  Check out the following links for some neater ways.

I came across [this article]("http://www.mikerubel.org/computers/rsync_snapshots/") a few months ago that was pretty good - it mentioned how to keep rolling snapshots that are built up from hardlinks to original files.

Also: [rsnapshot]("http://www.rsnapshot.org/") is a perl based utility that does all of the above, packaged in a pretty form.

Finally, [backuppc]("http://backuppc.sourceforge.net/") is a pretty slick mass-backup utility with snapshots, and is cross-platform (but Unix based).  The front-end is all browser-based.

Personally, I had set up a DOS batch file using cygwin utilities to back up my dad's windows PC across ADSL.  Pretty fun building it.

---

