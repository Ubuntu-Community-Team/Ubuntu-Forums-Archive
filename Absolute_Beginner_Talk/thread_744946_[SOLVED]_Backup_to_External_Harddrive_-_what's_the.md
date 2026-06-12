---
title: "[SOLVED] Backup to External Harddrive - what's the best program?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by viiv on 2008-04-04
I've tried out a bunch of programs, including *Simple Backup* and none of them are able to see my external drive. It's definitely not a problem with the drive because thunar finds the external drive easily.

Anyone know a good GUI program that manages backups and is able to send the backup directly to an external HD?

It is not possible to backup locally and then move the backup file. I don't have a lot of drive space. The last time I tried that, using a command line tool, it filled up my whole drive so that my system crashed and I wasn't able to start the windows manager. I had to search around, using terminal, to find the massive backup file and delete it! (don't want to have to do that again)

ps. I'm using gutsy/xfce

---

### Post by brian_p on 2008-04-04
> **viiv said:**
> I've tried out a bunch of programs, including *Simple Backup* and none of them are able to see my external drive. It's definitely not a problem with the drive because thunar finds the external drive easily.

Anyone know a good GUI program that manages backups and is able to send the backup directly to an external HD?

It is not possible to backup locally and then move the backup file. I don't have a lot of drive space. The last time I tried that, using a command line tool, it filled up my whole drive so that my system crashed and I wasn't able to start the windows manager. I had to search around, using terminal, to find the massive backup file and delete it! (don't want to have to do that again)

ps. I'm using gutsy/xfce

rsync is command line but it is as simple as

rsync from_here to_there

grsync is a gui front end.

---

### Post by misfitpierce on 2008-04-04
And to think... I do mine manually by drag and drop :( lol

---

### Post by joshrobinson on 2008-04-04
> **misfitpierce said:**
> And to think... I do mine manually by drag and drop :( lol
i keep everything important on a separate partition, and just be very careful when making partition table changes, i have too much data, and nowhere to put it :-(

---

### Post by brian_p on 2008-04-04
> **misfitpierce said:**
> And to think... I do mine manually by drag and drop :( lol

Look! No hands. A cron job.

viiv might be interested to know the program you use.

---

### Post by bwallum on 2008-04-04
Hi

Simple backup should work. I can use it on a USB memory stick for example. However you have to make sure the drive is mounted first. (Places>Computer, right click on drive and 'Mount').

Good luck
Bob

---

### Post by kpkeerthi on 2008-04-04
For / (root) partition, I prefer to [backup with tar]("http://linuxmint.com/forum/viewtopic.php?t=3969")

For /home partition, I use rsync
```

rsync -a /home/ /media/backup/home

```

tar and rsync are unobtrusive methods I could suggest - Setup once and automate with a cron job and they do their job in the background.

Of course, there is  [partimage]("http://www.psychocats.net/ubuntu/partimage"), [clonezilla]("http://clonezilla.sourceforge.net/") & [remastersys]("http://www.remastersys.klikit.org/"). But they require you to 'manually' do it everytime.

---

### Post by Tews on 2008-04-04
The best program that Ive found to do backups is Quick-Start.  I use it to back up my system to an external 500Gb drive. You can do full/partial backups, Schedule backups etc.  See pic ...

[IMG]http://www.libertymanor.org/menu.png[/IMG]

You can read about it/get it here ===> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by viiv on 2008-04-07
Thanks to everyone who posted a response. Sorry for my taking so long to reply. Life is chaotic.

Brian:
I installed grsync. It looks like a nice program. Initially it had the same problem as simple-backup. It would not recognize my external drive, thus I couldn't backup to it. Then, for some reason I created a menu shortcut to the external drive which did show up in the grsync dialogue box. I haven't run a full job yet, but it looks like it will work. Thanks. 
ps. From the name and some of the layout, this program looks like a synchronization program. Does this mean that it could possibly overwrite filed on my local drive if somehow I changed a file on the external drive?

Joshrobinson:
Good point. I have all my personal files in a separate partition also. It helps if I ever want to change distros.


kpkeerthi:
Thanks for the other suggestions. I'll look into those.

Tews:
That looks like a nice program too. I'd like to check it out. That link you included sent me to some sore of sign in screen (?)  I tried ```
sudo apt-get install quick-start
``` but it couldn't find the package. Does it have another name?

---

### Post by brian_p on 2008-04-07
> **viiv said:**
> 
Brian:
I installed grsync. It looks like a nice program. Initially it had the same problem as simple-backup. It would not recognize my external drive, thus I couldn't backup to it. Then, for some reason I created a menu shortcut to the external drive which did show up in the grsync dialogue box. I haven't run a full job yet, but it looks like it will work. Thanks. 
ps. From the name and some of the layout, this program looks like a synchronization program. Does this mean that it could possibly overwrite filed on my local drive if somehow I changed a file on the external drive?


viiv, I use rsync directly and not grsync. I mentioned the program because you wanted a gui interface. rsync copies files and differences between files to and from remote machines. grsync is a front end for it but without all the bells and whistles.

What you are concerned about may be the case but I don't really know. rsync knows what it has copied to the external drive so if you alter a file on there it may complain.

Your may better understand what grsync does by looking at how rsync does its job. This is a very readable article:

[http://linuxplanet.com/linuxplanet/tutorials/6435/1/](http://linuxplanet.com/linuxplanet/tutorials/6435/1/)

---

### Post by Tews on 2008-04-07
Im such a klutz !  Link Fixed!!  :lolflag:

---

### Post by viiv on 2008-04-07
Thanks Brian. I'll check it out

---

### Post by viiv on 2008-04-14
Thanks everyone
I've got Rsync and Simple Backup working now.
I appreciate all your input.
:)

---

