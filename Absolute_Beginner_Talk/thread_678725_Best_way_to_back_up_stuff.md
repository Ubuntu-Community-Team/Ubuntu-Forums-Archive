---
title: "Best way to back up stuff"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by alecspoons on 2008-01-26
Hi there

As a newcomer to Ubuntu and an obsessive when it comes to backing up my work, I'm looking for the best way to back up files and folders.

Before moving over to Ubuntu, I always did a regular backup using a program called 'AllwaySync' which very quickly synchronised my documents to another computer I kept specially for the purpose. 

I'm looking to do the same with Ubuntu. Could anyone suggest the best way to synchronise several individual folders to a networked machine? I don't need to back up my entire 'Home' folder, but I do want to back up several folders within 'Home'. 

I'm trying to find the fastest and easiest method, because I know that if it's too difficult, I probably won't back up as frequently as I should!

Many thanks

---

### Post by lswest on 2008-01-26
personally i think [this method]("http://ubuntuforums.org/showthread.php?t=564836") works best, and it is explained well.  Should be just what you need^^

---

### Post by alecspoons on 2008-01-26
Much thanks for the swift reply, Iswest.

I will take time to study that thread with care - thanks for the tip.

Meantime, I'd love to read other suggestions as well. Are any of the backup programs in the 'Add/Remove' bit any good? What are people's experiences? Has anyone tried 'Unison' for backup?

Thanks again

---

### Post by perixx on 2008-01-26
In case you like a graphical GUI: 
**SBackup** will perhaps satisfy your needs.
[http://wiki.ubuntuusers.de/sbackup]("http://wiki.ubuntuusers.de/sbackup")

or **HUbackup** (link at the bottom of that page)

If you like the command line, here's my preferred command (keeping all permissions + doing incremental backups):
> rsync -au --append /SOURCE/PATHORFILE /DESTINATION/FOLDER
If you want to backup sth. outside of your home folder, you'll need to have a 'sudo' in front of the command, of course.

**Hint:** regardless of where you backup to (if it's onto HDD) - it's best not to use the System-partition (root). If this one's running full during the backup, you can end up with a corrupted System.

perixx

---

### Post by alenis on 2008-01-26
I keep my data on a nas device. Periodically I backup all the data (currently about 19 GB) using 7za, which compresses the data to about 10GB. 

I use this command

7za u destination -up0q0r2x1y2z1w2 source/* -ms=off 

for each "source" that I want to store in a separate archive.

This command is supposed to update the archives without creating them from scratch everytime I issue it.
7za should provide  a better compression with respect to tar, bzip or gzip.
Then I burn everything on DVDs or copy it to an external hard disk.
Using an external hard disk, of course, also allows you to backup your data easily without compressing them. The best tool I know to accomplish this is Grsyng (gui for rsync).

---

### Post by alecspoons on 2008-01-27
Thanks for these tips.
I'll try them out.

I suppose I'd prefer to use a graphical GUI where I could, but I am not adverse to using the terminal if it does a better job. I'd just be stepping outside my comfort zone a little more - not necessarily a bad thing, of course.

I still might give Unison a try as well, as I have seen someone make a direct comparison between Unison and AllwaySync elsewhere.

Anyone any thoughts about Unison in this context?

---

### Post by Ub1476 on 2008-01-27
I suggest [QuickStart]("http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart")

Sbackup is alright, but I had problems retrieving the backed up files so..

---

### Post by shashank on 2008-01-27
NOW STOP READING :popcorn:EVERY THING ABOVE OR BELOW THIS POST...
JUST LISTEN
DOWNLOAD A NORTON GHOST 11 PORTABLE FROM RAPIDSHARE.COM
U KNOW HOW 
GOTO GOOGLE.COM
SEARCH: "NORTON GHOST 11 RAPIDSHARE.COM"
MAKE A BOOTABLE ISO FROM NERO AND COPY THE NORTON GHOST 11 IN IT

WHEN EVER U WANNA BACKUP AND RESTORE JUST INSERT THAT CD AND DO WHAT EVER U WANT...
WORKS EVEN AFTER FULL SYSTEM CRACK ..
ITS LIKE THAT AUTO COMPLETE RECOVERY BUTTON WHICH BIG COMPANIES GIVE FOR FREE IN THERE PCS...
U WILL SAY I DONT USE FREE STUFF..
PIRACY HELPS MAKING FREE  HA HA HA HA HA HA:lolflag:

---

### Post by shashank on 2008-01-27
JUST TO SUPPOORT UT UR FREE...THING 

USE PARTIMAGE...:guitar:

---

### Post by paul.matthijsse on 2008-01-27
Hello, I use rdiff-backup for that. I made a crontab of the process, so it automatically - and incrementally - backups my home dir (or whatever dirs you like) to another disk, two times a day. Works like a charm.

---

### Post by alecspoons on 2008-02-05
Thanks to everyone for their thoughts.

I tried everything without much luck, mainly because I couldn't get anything to work with a networked drive. No doubt because of my inexperience, I'm sure.

I did loads of hunting about for other ideas, and finally came to this article:

[http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html](http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html)

This describes how to use 'Conduit' which I have now got set up and is at this very moment synchronising my documents folder.

After lots of mucking about with other solutions, Conduit was the first and only that did exactly what I wanted straight away! It didn't blink at my networked drive (which I've got set up as SSH).

I like Conduit!

:)

---

