---
title: "Backup Drive Whats The Best Way"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by billmik on 2008-02-11
Whats the best way or program to back up my ubuntu linux HD. I use driveimage xml for windows back up but it doesnt see my linux hd.

---

### Post by julian67 on 2008-02-11
If you want to clone the drive then clonezilla live is excellent. You end up with a disk image from which you can restore the whole disk, or partitions, also the MBR. If you want to back up particular folders/files and be able to access those back ups via your file manager/terminal then you might want to try rsync on the command line or grsync if you prefer a gui, though rsync is surprisingly simple to use in the terminal after reading the excellent man page which includes several examples.

---

### Post by lespaul_rentals on 2008-02-11
```
cp -r / <destination>
```

julian67's idea was better, though.

---

### Post by ajgreeny on 2008-02-11
Just use grsync to backup **/home** and also perhaps **/var/cache/apt/archives** and your **sources.list** file to the external drive and a reinstall will be so simple that it is hardly worth cloning the whole disk.

---

### Post by billmik on 2008-02-11
> **ajgreeny said:**
> Just use grsync to backup **/home** and also perhaps **/var/cache/apt/archives** and your **sources.list** file to the external drive and a reinstall will be so simple that it is hardly worth cloning the whole disk.

Is there a guide somewhere to do this?

---

### Post by julian67 on 2008-02-12
[http://www.opbyte.it/grsync/]("http://www.opbyte.it/grsync/")

lots of links to articles/guides on the author's page.

also read man rsync to get an idea of what the gui is doing.  To be honest it isn't complex in practise, chances are once you've used it a few times you'll find the command line client just as easy.

---

### Post by hyper_ch on 2008-02-12
How do you want to backup?

Do you want to make in image so that you just can put back the image?

Do you want to make frequent backups and keep older versions?

---

### Post by kpkeerthi on 2008-02-12
I have separate root and home partitions. My backup disk is mounted as /backup. 
With a cron job set to run once in two weeks,

1. / partition is backed up to /backup as a tar.gz file. You can choose to do incremental backups with tar to save some space. But my / partition is about 3 GB and when tarred it is usually around 1 GB only. So I do full backups. And the old backup file is automatically removed.

2. /home is rsync'ed to /backup/home. I've got tonnes of music/movies/pics so I choose NOT to tar /home as it would simply slow down the operation offering no real space benefits. rsync is way faster as it would copy only the files that has changed since the last backup.

3. Optionally you can tar or rsync the /etc and its sub-folders so it is easier to restore critical system-wide config files should you break something . I don't do this as I can always restore from the tar I created in step 1 without doing a full restore.

**Advantages:**
1. Cron friendly. Backup process runs transparently behind the scenes. No need to boot off a Live CD and the manual step is eliminated.
2. It is easier to clone your setup using the tar of / partition. No need to reinstall the packages and customize again. All settings are preserved. To restore /home, just reverse rysnc the home folder. 
3. It is easier to restore a specific file from a tar than from a disk image.

---

### Post by billgoldberg on 2008-02-12
I just copy the home documents/picture/music/video folder to an external harddrive every week or so.

Reinstalling the OS only takes 15 min and then simple copy the files back.

There is a program called quickstart that allows for automatic back-up (not cloning), lnik:
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by billmik on 2008-02-12
> **billgoldberg said:**
> I just copy the home documents/picture/music/video folder to an external harddrive every week or so.

Reinstalling the OS only takes 15 min and then simple copy the files back.

There is a program called quickstart that allows for automatic back-up (not cloning), lnik:
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

I really dont care which way i back up just so i can get back to what i have right now with ubuntu incase i mess something up lol. This quick start sounds interesting ill give it a try thanks all

---

