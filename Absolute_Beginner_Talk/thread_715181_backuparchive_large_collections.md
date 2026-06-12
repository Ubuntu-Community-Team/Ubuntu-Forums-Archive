---
title: "backup/archive large collections"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Ndyanabo on 2008-03-04
Hey,

I'm looking for a backup/archive program for large collections of files.

I have several large collections -- photos, and music -- in the 100s of gigabites. I'd like some software to manage backups of this stuff, to prepare for when HDs fail. I guess that means backing up to DVD.

Is there any simple backup program that will help me? I guess it would monitor a set of directories, and keep a database of what has been backed up, what hasn't, and where (ie, DVD # 1, etc). Ideally, it would handle the burning, and maybe even do some compression.

Most of the backup utilities I've seen are more for system back up or file versioning, and don't seem ideal for large and growing collections of static files across multiple HDs.

thanks!

---

### Post by herbster on 2008-03-04
Rsync would do the job, but not the burning. Are you really burning 100's of GB of data to DVDs? :D

I use rsync to backup everything to external drives and a server. You can make a backup script then add a cronjob which will have it run whenever you like. Tell me if this sounds like what you want.

---

### Post by Ndyanabo on 2008-03-04
I have no doubt that rsync could do what I want, but it seems like that's not really it's strength. Rsync seems like it's good at setting up periodic synchronizations or mirroring, usually to a HD or network server. If it wouldn't do the burning, what exactly would it do for me? 

Would rsync keep a database of what 's been synced?

Also, rsync is command line, right? I'm envisioning something with a gui.This isn't something that I want to think about every day, and if I go for a couple of months without using it, then I'd have to relearn the commands.

I don't really want to back up to DVD, but it seems like the cheapest option. Seems like overkill to buy HDs. DVDs are cheap and apparently durable.  If there are any other suggestions, I'd be open to that. I mean, what else is there?

---

### Post by wednesday allfather on 2008-03-04
I think backup-manager can do that.

I use it to upload to backup site.  I'm pretty sure you can change the config to burn to a disc.  Seems like I read that...

Worth checking out, anyway.  Good luck!

---

### Post by northern lights on 2008-03-04
Check out this [forum post]("http://ubuntuforums.org/showthread.php?t=35087").

---

### Post by herbster on 2008-03-04
> **Ndyanabo said:**
> I have no doubt that rsync could do what I want, but it seems like that's not really it's strength. Rsync seems like it's good at setting up periodic synchronizations or mirroring, usually to a HD or network server. If it wouldn't do the burning, what exactly would it do for me? 

Would rsync keep a database of what 's been synced?

Also, rsync is command line, right? I'm envisioning something with a gui.This isn't something that I want to think about every day, and if I go for a couple of months without using it, then I'd have to relearn the commands.

I don't really want to back up to DVD, but it seems like the cheapest option. Seems like overkill to buy HDs. DVDs are cheap and apparently durable.  If there are any other suggestions, I'd be open to that. I mean, what else is there?

Rsync can backup your data, and you can export every rsync to a logfile. It will do everything you need with regards to the backing up of data/logging of said backups. Yes, rsync is command line, but there's a program called Sbackup (pretty sure "sudo apt-get install sbackup" would do it) that is a nice GUI front-end combining rsync and cron, so you can set your backup conditions as well as set the time, and boom it will run in the background as a daemon everytime it's scheduled.

Yes, rsync alone is CLI, and there's really nothing to remember. "rsync -avz --delete /backup/from /backup/to" Diggity done :)

As for DVD vs HD, it is more dependent on your time. I don't have nor want to spare the time to sit around burning by the 4.5gb or whatever. I spent a few mins creating some scripts that now execute an rsync of all my backups regularly and I never have to think about it.

---

### Post by Ndyanabo on 2008-03-04
I take it that rsync is more powerful than sbackup. I just installed sbackup, and it's not immediately apparent to me how to output to, say, a DVD5 sized tar file. Looks like it just backs up to another directory.

ok, let's say I go the rsync route. I have, eg 500 gig that I want to back up to 110 DVDs. I set it up to create and log archives of 4.5 gig, which I will then burn to DVD. I tell it to output the archive files, right onto my desktop, so I can burn them and then trash them. But, I don't want to do all 110 DVDs at once, needless to say. Can I set it up to say, output 10 (out of 110 total) DVD sized tar files? Then, the next time I'm in a back up mood, I have it archive the next 10 DVDs? and so on. It would have to keep track itself of  how much progress has been made on the directory, such that it doesn't rearchive the same stuff over and over again.

So, it  what it would mean is that at any given sync moment, it wouldn't backup everything, but just a small portion of it.

What I'm saying is that it's not just a matter of outputting to a disc, or even a DVD sized file, but managing the whole situation.

As I see it, these programs are good at syncing entire directories over and over again, but as I say, don't seem as good at dealing with larger collections. If it's possible to do with rsync, it seems to me like it would be beyond my scripting powers.

thanks for all the feedback.

---

### Post by herbster on 2008-03-05
> **Ndyanabo said:**
> I take it that rsync is more powerful than sbackup. I just installed sbackup, and it's not immediately apparent to me how to output to, say, a DVD5 sized tar file. Looks like it just backs up to another directory.

Rsync = sbackup. Sbackup is just a GUI front-end for rsync, so there's no burning option. It's the same program :)

> **Ndyanabo said:**
> ok, let's say I go the rsync route. I have, eg 500 gig that I want to back up to 110 DVDs. I set it up to create and log archives of 4.5 gig, which I will then burn to DVD. I tell it to output the archive files, right onto my desktop, so I can burn them and then trash them. But, I don't want to do all 110 DVDs at once, needless to say. Can I set it up to say, output 10 (out of 110 total) DVD sized tar files? Then, the next time I'm in a back up mood, I have it archive the next 10 DVDs? and so on. It would have to keep track itself of  how much progress has been made on the directory, such that it doesn't rearchive the same stuff over and over again.

So, it  what it would mean is that at any given sync moment, it wouldn't backup everything, but just a small portion of it.

What I'm saying is that it's not just a matter of outputting to a disc, or even a DVD sized file, but managing the whole situation.

As I see it, these programs are good at syncing entire directories over and over again, but as I say, don't seem as good at dealing with larger collections. If it's possible to do with rsync, it seems to me like it would be beyond my scripting powers.

thanks for all the feedback.

Rsync is good at everything, from what I have experienced. I use it to back up over a terabyte, so you should be fine-- what else is backing up in the most basic form other than having a mirror of your stuff? Also, you must understand that to automate the process, it's a matter of having your rsync command set, making a token script and adding a cronjob to schedule it. This would take care of everything. But you want to burn dozens of DVDs, which of course will require you being present for that part.

What you could do to make DVD5-sized files is use split. So basically, let's say you have your 500gb. Depending on how it's distributed (separate partitions/folders/etc.) it will become a bit more detailed but to give you a simple example, let's say I have 500gb in one directory with subdirectories. I could compress it into one giant archive and then split it into 4.5gb volumes, then burn. Of course this will take some time, but you could run tar and leave it compressing overnight or something (and really, if you're willing to burn 110 freakin' DVDs, I can't see some more hours leaving it compressing on its own to be an issue ;)).

Obviously, make sure you're running this command from a location with at least as much free space as you want to backup:

```
tar cjf backup.tar.bz2 /path/to/stuff/to/backup
```

Once she's done, we split into volumes:

```
split -b 4500000000 backup.tar.bz2 backup
```

This will split the archive into DVD5-sized volumes, named backupa, backupb, etc. which you can burn accordingly.

---

