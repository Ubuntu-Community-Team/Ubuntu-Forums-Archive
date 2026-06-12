---
title: "Let's make Time Machine"
date: 2012-01-06
forum: Apple Hardware Users
---

### Post by Q-collective on 2012-01-06
I've done some searching recently regarding *userfriendly* backup applications. Deja-Dup, the current favorite of Ubuntu, earns karma points for simplicity. But it's still not there yet.

Anyone who ever used OS X and its Time Machine backup mechanism, knows that there is nothing quite like it in the other Unix variations. Even stronger: Time Machine pretty much leaves anything else behind it by *lightyears* in terms of simplicity, yet at the same time being extremely effective in restoring single files if needed.

So, let's start a little community fundraiser here, because no one has felt the urge otherwise to write a Time Machine clone in the past 5 years.

I'm putting down &#8364;50 for a community effort. You're welcome to respond if you either want to put in money too or perhaps take up the challenge and start coding.

Discuss.

---

### Post by Q-collective on 2012-01-08
So, over 100 views, but no reply?

I was kinda hoping for some feedback, both from users chipping in with modest amounts of cash and developers interested in making this a reality.

Given to how important backups are and to how subpar the current solutions are in terms of usability, I was expecting some responses by now.

---

### Post by Wolfador on 2012-01-08
Have you checked out [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

I don't think backups of a system are as important now as most of us are using "cloud" storage for all of our files.

---

### Post by Wolfador on 2012-01-08
you can also checkout [https://launchpad.net/backintime](https://launchpad.net/backintime)

sudo apt-get install backintime-common backintime-gnome

you can also mount your Airport Extreme / Time Capsule using [http://blog.geekliketodd.com/archives/900](http://blog.geekliketodd.com/archives/900)

---

### Post by Q-collective on 2012-01-10
> **Wolfador said:**
> I don't think backups of a system are as important now as most of us are using "cloud" storage for all of our files.
Clouds are a nice addon, but for the present time impractical to be used as backup because of the sheer size of the data involved (and therefore the costs) and because it is relatively slow to transmit large amounts of data over the internet (slower than, say, on a USB mounted external HDD).

I'm currently using backintime btw, which isn't too bad I guess.

---

### Post by Q-collective on 2012-01-15
Today, I've found out about [Redo Backup & Restore](http://redobackup.org/), which is a livecd that simply clones your hard drive to another drive. It is simple and restoring is also pretty straightforward. But I don't believe it is incremental, so it'll just clone your entire drive every time, wasting huge amounts of space on your backup drive. Also, rebooting for a restore is a very good idea, but I'm not too sure about the need for rebooting just to make a backup...

BackInTime meanwhile for some reason does no backups at all on my machine. It pretty much completes the backup and then it simply gives an error that it has failed to backup and cleans the backup again. I wasted hours with that today and I just uninstalled it in the end.

Deja-Dup meanwhile just isn't capable (apparently, please correct me if I'm wrong) to backup your entire drive, in the background, without asking for your password every backup cycle.

So, I still believe there is plenty of room for improvement. Although I was rather impressed by the idea of Redo to simply use a livecd to restore your data. Brilliant in its simplicity. Much easier and more fail safe to do than Migration Assistant in OS X even :)

---

### Post by Cpierce on 2012-01-15
+1 for redo and also CloneZilla

---

### Post by BDNiner on 2012-01-17
Are you looking for an application that has a similar or innovative interface or a comparable backup solution. I used rsync for the longest time with a script, and fwbackups isn't too bad. 

[http://www.diffingo.com/oss/](http://www.diffingo.com/oss/)

I don't thinkfwbackups has been updated in while.

---

### Post by Q-collective on 2012-01-17
> **BDNiner said:**
> Are you looking for an application that has a similar or innovative interface or a comparable backup solution.
Yes. Backing up should happen in the background, restoring should be easy.

> I used rsync for the longest time with a script, and fwbackups isn't too bad. 

[http://www.diffingo.com/oss/](http://www.diffingo.com/oss/)

I don't thinkfwbackups has been updated in while.

Perhaps I overlooked it, but how do you restore with fwbackups?

---

### Post by Tony Flury on 2012-01-17
> **Q-collective said:**
> 
So, let's start a little community fundraiser here, because no one has felt the urge otherwise to write a Time Machine clone in the past 5 years.



Um - I disagree - I started writing a Time Machine clone, complete with plans to add a time slider into Nautilus if a backup existed on a given folder hierarchy. I stopped after my laptop was stolen, and I realised I did not have a backup of my code to date (oh the irony).

I will start re-writing it pretty soon - I don't need donations (although they would be nice) - but I would need help to do all the change management stuff - I used to be able to wrap my head around it - but it confuses the hell out of me now.

Basic specs (as identified by me) : 

1) real time identification of changes (new files, sub-directories, deletions, permission changes) on monitored directories, and config tool to support this.
2) Permanent recorded queue mechanism so that changes are still actioned even over a system shutdown.
3) Backups that are in train when system shutdown are automatically restarted. Simple system to prevent loss of old data on crashes.
4) Discrete compressed backups for each file - not one big archive per system - easy restore and less risk of corruption.
5) Command line queue monitor for admin
6) Command line tools to suspend/restart backups, queueing etc.
7) Panel icon to show status etc.
8) Integration with Nautilus (if possible) to show a "time slider" when backups exist.
9) GUI based config tool.

I have designs for 1 to 5 - and I had working code fragments for 1,2,4 and 5. 6 should be easy. 7 should be too. No idea where to start on 8 - but it was not in my top priority list.

My language of choice for all of this (certainly 1 to 6) was python - it is a language I know and has easy to use libraries for all of the above.

---

### Post by BDNiner on 2012-01-17
There is a restore Tab in the application. That you can use to restore specific files. I have never actually had to restore a backup though. So how it works in practice I don't know.

---

### Post by BDNiner on 2012-01-17
> **Tony Flury said:**
> Um - I disagree - I started writing a Time Machine clone, complete with plans to add a time slider into Nautilus if a backup existed on a given folder hierarchy. I stopped after my laptop was stolen, and I realised I did not have a backup of my code to date (oh the irony).

I will start re-writing it pretty soon - I don't need donations (although they would be nice) - but I would need help to do all the change management stuff - I used to be able to wrap my head around it - but it confuses the hell out of me now.


Do keep us informed. I am also interested in this since it doesn't look like fwbackups is being developed anymore.

---

### Post by Silverflyer on 2012-01-17
Backintime works pretty well once set up.

---

### Post by Q-collective on 2012-01-17
> **Tony Flury said:**
> Um - I disagree - I started writing a Time Machine clone, complete with plans to add a time slider into Nautilus if a backup existed on a given folder hierarchy. I stopped after my laptop was stolen, and I realised I did not have a backup of my code to date (oh the irony).

I will start re-writing it pretty soon
Yes, please keep us posted. Your specs sound pretty good!

> I don't need donations (although they would be nice)
I keep my 50 euro's in check :)

> but I would need help to do all the change management stuff - I used to be able to wrap my head around it - but it confuses the hell out of me now.
What concretely do you need?

Also, do you consider rsync as a backend? Using its differences function would make any backup app very efficient on disk space as it would only store the differences that are made on the files and directories.

---

### Post by Tony Flury on 2012-01-18
> **Q-collective said:**
> Yes, please keep us posted. Your specs sound pretty good!

I keep my 50 euro's in check :)

What concretely do you need?

I need someone to guide me through setting up an easy to use environment where I (and eventually others) can check files in and out etc. As I say I used to know my way around sccs, but I know stuff has moved on considerably and I will need to create project files etc online.

> 
Also, do you consider rsync as a backend? Using its differences function would make any backup app very efficient on disk space as it would only store the differences that are made on the files and directories.
I was thinking about using a zip file backend - every backed up file will have it's own zip file at the backup destination. I definitiely did not want to be backing up entire folders on the fly. My idea is when I need to back up a file :  

```

1) Grab entry from the queue and identify the zip file.
2) Rename old zip file to a backup version
3) Copy backup file back to correct version
4) Add file to be backuped up zip file - with the time stamp as the file name in the zip file.
5) remove the backup
6) Mark the queue entry as closed

```
Thus any interruption between 1 and 4 would result in a still open queue entry and a intact backup version - i.e. a failsafe version.
An interruption between 5 & 6 would result in an open queue item but with no backup (again easily detectable and resolvable).
I am assuming that file renames are atomic (i.e. a simple change to a directory and therefore high unlikely to be interrupted). The long bits of the process are items 3 and 4.

---

### Post by markbl on 2012-01-18
I've been using rsnapshot for a couple of years to backup my linux pc and my wife's windows pc. Simple and works really well.

---

### Post by Tony Flury on 2012-01-18
> **markbl said:**
> I've been using rsnapshot for a couple of years to backup my linux pc and my wife's windows pc. Simple and works really well.

The problem with rsnapshot is that it can take a long while to do a full backup (specially over a network), and then you end up with a massive archive which is almost impossible to open. Also any interruption (power, network etc) corrupts your backup arhcive and wastes all of that time.
I was using a similar tool - and ended up having to leave my laptop on for over 24 hours to do the initial backup, only to end up with archive I could not restore anything from, because it was too big to open across the network.
The rationale for what I was trying to write was to end up with much smaller archives, and to only ever do incremental backups, and crucially build in protection from interruptions. With my scheme the backups run in the background, but if i shutdown for the night - at most I end up with one or two partial backup files which can be recovered (deleted and re-built). If my network dies (for instance a power cut), again i would loose the backup for one or two files, not my whole archive. Restoring becomes easier due to the need to restore one file from a small archive, rather than one file from thousands in a massive archive.

---

### Post by canhoto on 2012-01-18
> **Q-collective said:**
> Today, I've found out about [Redo Backup & Restore]("http://redobackup.org/"), which is a livecd that simply clones your hard drive to another drive. It is simple and restoring is also pretty straightforward. But I don't believe it is incremental, so it'll just clone your entire drive every time, wasting huge amounts of space on your backup drive. Also, rebooting for a restore is a very good idea, but I'm not too sure about the need for rebooting just to make a backup...



Unfortunately it doesn't run on ppc, apparently.

---

### Post by canhoto on 2012-01-22
> **Silverflyer said:**
> Backintime works pretty well once set up.

Yes, I'm using Backintime.

However, I've found two problems:

- It takes a long time to make each new snapshot

- It doesn't run by itself. I have to launch it if I want it to run the scheduled backups. Once set up, it should run by itself, I souldn't care about it. At least that's how Time Machine works.

I can always make it launch when I start up the computer, of course. But I still have the slow snapshot's issue.

---

