---
title: "[SOLVED] Are incremental Backups possible using &amp;quot;Simple Backup&amp;quot;?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-29
I use Feisty 7.04, and have started doing periodic backups to an external hard drive, of my home directory and a few other folders, using the Simple Backup utility. I do it in manual mode, as I prefer to do the backups at my own convenience when I feel like hooking up the hard drive. 

Up till now, to me it looks like you have to do a full backup from scratch every time you run it.

Is there some way to configure the backup procedure so it will see what you backed up last time, and only update those files which have been changed since the last backup? 

This would be quite handy and time-saving. No need to keep recopying the majority of the files, which remain exactly the same as they were at the previous backup.

If Simple Backup cannot do this, then can you recommend another backup utility which can do this? Thanks! :)

---

### Post by Bothered on 2007-09-29
Simple backup uses incremental backups by default. Check your backup drive - you should find that most backups are small and there is one large backup (the first). You can configure which backups should be purged in the simple backup configuration.

---

### Post by swarup on 2007-09-29
> **Bothered said:**
> Simple backup uses incremental backups by default. Check your backup drive - you should find that most backups are small and there is one large backup (the first). You can configure which backups should be purged in the simple backup configuration.

I see. That is great. 

I have actually only done one backup so far, and wanted to set it to incremental before doing more. But I couldn't find anywhere to set it to "incremental" in the Sbackup configuration. 

Well, if it is incremental by default, then I do have one follow-up question:

If every time you do a backup, it only backs up the files that have changed, then let's say after doing around 5 or 6 backups, one day you need to restore a particular file to your internal drive because the internal drive's version of it went bad for some reason. Of the 5 or 6 backup archives you have, how will you know in which *that* file is located? Each backup archive will have only an incomplete set of files in it-- those which were changed since the previous backup. It seems like it may be difficult in that setting to locate the file you need to restore.

---

### Post by por100pre1 on 2007-09-29
You can try copying your files with Grsync to another hdd. You can set it up to remove in destination any files are no longer in source, and it update the used and modified files only. The files will be easy to look, drag and drop. After the first use, the backup will be real quick.

---

### Post by swarup on 2007-09-29
> **por100pre1 said:**
> You can try copying your files with Grsync to another hdd. You can set it up to remove in destination any files are no longer in source, and it update the used and modified files only. The files will be easy to look, drag and drop. After the first use, the backup will be real quick.

I see. Are you saying that Grsync will work better than Sbackup for the scenario I described? If so, I could install Grsync and try that one instead.

---

### Post by swarup on 2007-09-29
I have the following question about doing backups using the Simple Backup utility:

If every time you do a backup, it only backs up the files that have changed (since the previous backup), then let's say after doing around 5 or 6 backups, one day you need to restore a particular file to your internal drive because the internal drive's version of it went bad for some reason. Of the 5 or 6 backup archives you have, how will you know in which that file is located? Each backup archive will have only an incomplete set of files in it-- those which were changed since the previous backup. It seems like it may be difficult in that setting to locate the file you need to restore.

---

### Post by por100pre1 on 2007-09-29
> **swarup said:**
> I see. Are you saying that Grsync will work better than Sbackup for the scenario I described? If so, I could install Grsync and try that one instead.

It is possible, specially if you want to be able to access the backed up files with any file browser.

```
sudo aptitude install grsync
```

It will appear in "Internet". Hope it helps. :)

---

### Post by swarup on 2007-09-29
I installed Grsync per your instruction. 

Two questions:

1. It seems that I do not have the permissions set up properly in the external hard drive to be able to write to it. I tried to do a backup using Grsync, but all the file copy transfers failed and gave the error message, "permission denied". So I did gksudo nautilus and directed nautilus to the external hard drive, then went to "properties">permissions and I changed the owner from "root" to me. And made "access" set for "read and write files". But it didn't make any difference. The Grsync execute order still fails with "permission denied".

2. Is it the case that Grsync can only back up one folder at a time? Or can I designate multiple folders that I want it to backup, and have it remember this so every time I click "execute", it will back up that pre-designated set of folders.

---

### Post by por100pre1 on 2007-09-29
Please read [this]("http://ubuntuforums.org/showthread.php?t=484553"). Which file system are you using? IMHO, NTFS is NOT a convenient alternative... :-k

EDIT: Try making a folder with your user name in the external hdd. Then use it as destination folder. [Here]("http://ubuntuforums.org/showpost.php?p=3448164&postcount=2") I posted some settings to use.

---

### Post by swarup on 2007-09-29
> **por100pre1 said:**
> Please read [this]("http://ubuntuforums.org/showthread.php?t=484553"). Which file system are you using? IMHO, NTFS is NOT a convenient alternative... :-k

The external hard drive is ext3. So is my internal HD (it's Feisty).

I'll go take a look at the site you are referencing now.

---

### Post by swarup on 2007-09-29
[EDIT] There is one piece of information I want to give first of all here: I am able to do backups just fine using the "Simple Backup" utility. And I am writing the  backup to the same external hdd as I am trying to do below with the Grsync utility. So when Simple Backup does it just fine, then why is Grsync denying permission? In this situation, it does not seem to be a problem with the external hdd or its settings.

> **por100pre1 said:**
> Please read [this]("http://ubuntuforums.org/showthread.php?t=484553"). Which file system are you using? IMHO, NTFS is NOT a convenient alternative... :-k

1. the external hdd is ext 3
2. earlier today I went to the external hdd using sudo gksudo nautilus and changed the owner of the partition from root to swarup. So now I can create and delete folders as I like there. I also changed "access" to "read and write"-- but it does not stick. When I checked again now, it has returned to its former setting as "--". Is this the problem?
3. I went to the thread you referenced on your latest post. There they give instructions for using a chown command to get the external hdd to be able to be written to. I tried this (see below), but it does not work. Can you tell me why?

```
swarup@swarup-laptop:~$ sudo chown swarup:swarup /media/disk-1
Password:
sudo: cho: command not found
swarup@swarup-laptop:~$ 
```


> **por100pre1 said:**
> EDIT: Try making a folder with your user name in the external hdd. Then use it as destination folder. [Here]("http://ubuntuforums.org/showpost.php?p=3448164&postcount=2") I posted some settings to use.
I made a folder on the external hdd. The folder is not *called* my user name though. It is called, "Discourse Files". Isn't that ok?

Here is what I set as the "source directory" in Grsync: /home/swarup/Discourse Files/
Here is what I set as the "destination directory" in Grsync: /media/disk-1/Discourse Files/

These are the exact file pathways of the folders referenced.

And here is the error message I get when I run "execute" in Grsync:

```
rsync: failed to set times on "/media/disk-1/Discourse Files/.": Operation not permitted (1)
rsync: mkstemp "/media/disk-1/Discourse Files/.0-0-70.odt.GOfu8D" failed: Permission denied (13)
rsync: mkstemp "/media/disk-1/Discourse Files/.0-0-71.odt.FsIaN2" failed: Permission denied (13)
rsync: failed to set times on "/media/disk-1/Discourse Files/.": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
```

Any suggestion for why it is still telling me "permission denied"?

---

### Post by por100pre1 on 2007-09-29
Try this:

```
sudo su -c 'chown -R swarup:swarup /media/disk-1'
```

The source and destination folders should be fine. Here are mine:

[IMG]http://img237.imageshack.us/img237/1563/grsyncco4.png[/IMG]

---

### Post by swarup on 2007-09-29
> **por100pre1 said:**
> Try this:

```
sudo su -c 'chown -R swarup:swarup /media/disk-1'
```

The source and destination folders should be fine. Here are mine:

It worked. I don't know what the above command means or what it did, but it worked. Either that, or it may be because this time I checked "Delete on destination". I was a little afraid to check that box before because it says "delete...", but this time I did check it. So I don't know whether it worked this time because of doing the "chown...." command, or because of checking "delete on destination", or both?

Anyhow, thank you. Now I can play with both Simple Backup and Grsync, and see which one I like better.:)

---

### Post by por100pre1 on 2007-09-29
> **swarup said:**
> It worked. I don't know what the above command means or what it did, but it worked. Either that, or it may be because this time I checked "Delete on destination". I was a little afraid to check that box before because it says "delete...", but this time I did check it. So I don't know whether it worked this time because of doing the "chown...." command, or because of checking "delete on destination", or both?

Anyhow, thank you. Now I can play with both Simple Backup and Grsync, and see which one I like better.:)

The sudo su -c command makes you become root (su) for just one command (-c) the command is covered with ''. Sometimes you need to be root for some commands, sometimes sudo is not enough. That command needs to be used with caution. Delete on destination removes everything in destination folder that is no longer in the original folder. You can disable it if you want. Glad to help. 8)

---

### Post by Bothered on 2007-09-30
I have once used sbackup to restore files, but I only had two backup points and so could use the archives created by sbackup directly. I believe the restore utility can be used to recover files from the last restore point to a target directory, but I'm not sure if all files (including those left unchanged from previous backups) or just the more recent incremental backup are recovered. You might want to experiment a bit to find out for yourself.

---

### Post by swarup on 2007-09-30
> **Bothered said:**
> I have once used sbackup to restore files, but I only had two backup points and so could use the archives created by sbackup directly. I believe the restore utility can be used to recover files from the last restore point to a target directory, but I'm not sure if all files (including those left unchanged from previous backups) or just the more recent incremental backup are recovered. You might want to experiment a bit to find out for yourself.

Thank you very much for your reply. Yes, There is the restore utility too-- I had forgotten about that. My guess is that it must have some way of accessing the several archive files that could potentially exist, to allow one to sift through and find one's file. 

Now, just to try out what you said about the default setup of SBackup to do incremental backups, I did a second backup yesterday. The first archive file made by Sbackup around 1 week ago, was 330 MB. Yesterday, according to your explanation I was expecting the next archive file to be much smaller. All I've done in the last week is to add some text files to my home directory. --But when I did the backup, then to my surprise the size of the new backup archive turned out to be 380 MB, which is even larger than the first archive I did a week ago. So are you sure the default is for incremental backup only?

==> One thing I am wondering in this regard. I had set the configuration to "manual backups only". This is because I am backing up to an external hdd and I want to be able to do the backup when it is convenient for me to hook up the hard drive. So when I do a backup, I just open "Simple Backup Config" and click on "back up now". But I think that doing it in this way, it is not going to work in the incremental fashion. It just does a brand new full backup when you give this command. I think if you want the incremental option, then you need to set Simple Backup Config to "Recommended", or "Custom"-- rather than "Manual Backups Only". In my case, perhaps I should select "Custom" and just change the "destination" to my external hard drive. I could set the time to weekly, and when it comes time to do the backup, Simple Backup will probably give me some kind of notice that it wants to do the backup. And then I can connect the external hdd and it will do its work. Is my thinking correct?

When you say you get "incremental backups", which setting do you have Simple Backup Config set to-- "Recommended", "Custom", or "Manual"?

---

### Post by Bothered on 2007-09-30
Which directories have you included to back up ("Include" tab in the config GUI)? I can't remember which directories are backed up by default, but if you've included the /var directory or /usr directory, then installed software over the week, then there could be quite a large amount of new data to be backed up. If you only want your home directory backed up then remove the other directories from the list and check (on the "Exclude" tab) that important directories aren't being excluded - in particular I uncheck the Exclude->Max Size check box.

I use "Manual Backups Only", with "Do backups" on the "Time" tab set to "Never", so that backups are only created when I click the "Backup Now!" button.

---

### Post by swarup on 2007-09-30
> **Bothered said:**
> Which directories have you included to back up ("Include" tab in the config GUI)? I can't remember which directories are backed up by default, but if you've included the /var directory or /usr directory, then installed software over the week, then there could be quite a large amount of new data to be backed up. If you only want your home directory backed up then remove the other directories from the list and check (on the "Exclude" tab) that important directories aren't being excluded - in particular I uncheck the Exclude->Max Size check box.

I have accepted the default settings for the "include" tab. That is:  /var/, /home/, /usr/local/, and /etc/. I did install GrSync yesterday, as well as yes I installed OO 2.3 as well a few days ago.

I don't know whether the software I load in the computer is included in one of those above folders. I hope not, because all I want to backup are my personal data files. I know my main data files are in the /home/ directory. But it seemed like some of my personal settings might have been kept in those other three directories. It is not in my mind just now exactly what settings those were, but I thought it was like that. If there is nothing personal in any of those other three directories, then I would just do the /home/ directory.

> **Bothered said:**
> I use "Manual Backups Only", with "Do backups" on the "Time" tab set to "Never", so that backups are only created when I click the "Backup Now!" button.

You use the "Manual" option, and still you find that it does incremental backups for you? 

Well, I went to one website earlier today-- a HowTo for the use of "Simple Backup":

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

And there, it says that when Simple Backup does an incremental backup, it will implement the incremental changes in the *original* backup archive it created on the first backup. So, one should not be getting a new archive file when one does a backup. If you get a new archive file in your backup drive, it means incremental backups are not being done. As far as I have understood, an "incremental backup" means the changes will be implemented in the *original* archive file. And that has definitely not happened with me.

---

### Post by Bothered on 2007-10-01
> **swarup said:**
> I have accepted the default settings for the "include" tab. That is:  /var/, /home/, /usr/local/, and /etc/. I did install GrSync yesterday, as well as yes I installed OO 2.3 as well a few days ago.

I think you only really need /var if you run your computer as a server and /usr/local if you manually install software (I believe, but I'm not certain on either of these). /home stores your personal files and /etc stores system settings, so you probably want both of these.

> **swarup said:**
> And there, it says that when Simple Backup does an incremental backup, it will implement the incremental changes in the *original* backup archive it created on the first backup. So, one should not be getting a new archive file when one does a backup. If you get a new archive file in your backup drive, it means incremental backups are not being done. As far as I have understood, an "incremental backup" means the changes will be implemented in the *original* archive file. And that has definitely not happened with me.

That's odd. I use manual backups only and get multiple archives in different folders - one big one and then smaller incremental ones.

---

