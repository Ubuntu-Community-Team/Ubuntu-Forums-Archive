---
title: "rsync help?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-25
I've been looking for a way to back up my linux partition weekly or so.  I was told by somebody to use dd, which is still a feasible option.

My friend, though told me he uses rsync, though info seems to be pretty vague about it.  Is there anything anybody can tell me about it?  It seems like it needs to back itself up on another UNIX system (which I don't have).  

I know this question is vague as hell - but can somebody throw me some info on it?  Good?  Bad?

---

### Post by glennric on 2008-02-25
You could always read the man page.  Type "man rsync". 
You could also look at the following link:
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by Sam Lars on 2008-02-25
I love it, it's great.  It's just command line, but it does what I want it to.
But, yes, it's only Linux to Linux, they both have to be running it.  Unless you can find some Windows utility for it out there.

---

### Post by glennric on 2008-02-25
> **Sam Lars said:**
> I love it, it's great.  It's just command line, but it does what I want it to.
But, yes, it's only Linux to Linux, they both have to be running it.  Unless you can find some Windows utility for it out there.

Can you use rsync to backup to the same computer?  Perhaps to another harddrive?

---

### Post by Sam Lars on 2008-02-25
Yes you can, you can point it to wherever you want it to synchronize the files.

---

### Post by glennric on 2008-02-25
> **Sam Lars said:**
> Yes you can, you can point it to wherever you want it to synchronize the files.

I was actually looking into this some time ago, and did find a way to do it, but not particularly satisfactory.  I had to ssh back into the same computer using the command on the link I posted above.  Is there a more direct way to do this?

---

### Post by jcwmoore on 2008-02-25
> Can you use rsync to backup to the same computer? Perhaps to another harddrive?

sure, use 

```
rsync SOURCE DEST
```

the source can be just about any thing your want, so if you want to back up or HD to an exteral, do something like this...

```
rsync -r / /media/disk/backup
```

that will take everything in the root folder (including things in the /medai/disk folder) and copy them to the backup folder of the external drive.  you need to do a little research to figure out exactly how to back up exactly what you want to backup...

---

### Post by glennric on 2008-02-25
I guess I didn't try the obvious.  One thing I can't seem to get to work is the --delete option.  It is supposed to delete extraneous files in the destination directory, but doesn't seem to.

Edit:  Nevermind, I got it to work.  It doesn't seem to like wildcards.

---

### Post by Sam Lars on 2008-02-25
You mean wildcards for --delete?
What are you doing when you SSH back in?  You can use rsync the other way to restore...

---

### Post by glennric on 2008-02-26
I mean if you type 
```
rsync --delete -a /path/to/directory/* /path/to/backupdir/
```
it will not delete extraneous files.  However it works if you drop the *.
I was backing up from one drive to another.  I dropped the ssh after I realized that the obvious syntax similar to cp worked.

---

### Post by Sam Lars on 2008-02-26
The * is not necessary.  By doing -a you imply, among other options, -r, for recursive, so...
```
rsync --delete -a /path/to/directory /path/to/backupdir
```
Will put "directory" in "backupdir"

---

### Post by Syndacate on 2008-02-28
Thanks all.

Sorry for the long response time, finals week just ended (trimester schedule here :().

There seems to be a lot of different input about this, obviously it's used a lot.

I'm looking to back my entire filesystem to an external.

Like a hard drive image, like Norton Ghost does, not just re-saving my files in a different place.

Though I can't format the external and it's NTFS.  So can I still back up there or no?  It seems like it needs a UNIX machine as the receptor.

---

### Post by adrien214 on 2008-02-28
I don't know much about making images-backup of a partition, if that's what you mean, but is it really required ? I mean, if your linux system is not recoverable, you'd better start from a fresh install and get your saved files from your external hdd.

Give [flyback ]("http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10")a try. it's a GUI using rsync. I am using it and I am very happy.

I would be careful about backing up to NTFS though, I did this and I ended up with several files that were unreadable, while others were just okay.

Why can't you format your external HDD ? You have something else on it ? I'd make another ext3 partition and backup to it... you shouldn't backup to a single ntfs partition to which both windows and linux have access, it can be costly.

---

### Post by Syndacate on 2008-02-28
> **adrien214 said:**
> I don't know much about making images-backup of a partition, if that's what you mean, but is it really required ? I mean, if your linux system is not recoverable, you'd better start from a fresh install and get your saved files from your external hdd.

Give [flyback ]("http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10")a try. it's a GUI using rsync. I am using it and I am very happy.

I would be careful about backing up to NTFS though, I did this and I ended up with several files that were unreadable, while others were just okay.

Why can't you format your external HDD ? You have something else on it ? I'd make another ext3 partition and backup to it... you shouldn't backup to a single ntfs partition to which both windows and linux have access, it can be costly.

It shouldn't be costly, XP can't even read NTFS unless you install a plugin, but it recognizes that something else is using the space.  Yes, there is a lot of other stuff on it, which is why I can't afford to reformat the entire drive.  Then if I did, I'd have to make it all EXT3 which isn't readable by NTFS systems which denies access from all XP machines from remoting into my computer unless I install a EXT3/2 reader on it which makes things real redundant, real fast.

Yes, it's really required, that's why I'm looking into doing it.

If my old *** 5 year old drive takes a crap, I don't want to be "well at least I got this" or "well I still have that" - I need to back up everything, so I can buy a new drive load up the image, and be on my way.  A)  I can't afford down time, B)  I can't afford file loss.

I'm not afraid of Linux "going bad" or anything of the sort, I'm afraid about drive failure and losing everything.

---

