---
title: "best way to mirror a hard drive in ubuntu"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-27
Looking for software that will automatically once a night make sure files one 1 hard drive are the same on another hard drive.. Currently using 1 250 gig hard just for mp3's and digital photos.. I have another 300 gig hard drive that i would like to use to mirror the 250 gig drive in case the 250 one would fail..Hopefully something with a gui interface

---

### Post by encompass on 2006-06-28
[QUOTE=lime4x4]Looking for software that will automatically once a night make sure files one 1 hard drive are the same on another hard drive.. Currently using 1 250 gig hard just for mp3's and digital photos.. I have another 300 gig hard drive that i would like to use to mirror the 250 gig drive in case the 250 one would fail..Hopefully something with a gui interface[/QUOTE]
well, not sure I can get you a gui... but don't worry, it is easy than you think to make a little program that can do it all for you.
The program I would recommend is called rsync. use man rsync to get the VERY long details about how it works.  or...
hmm let me see here... (googling...)
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/) mgiht be a help... you don't have to go over the net jsut to another mounted drive.  Nor do you have to start your own server.
```
rsync --verbose  --progress --stats --compress --recursive --times --perms --links /original_dir/* /sourc_dir/
```
Then just add the --delete so that it will delete anything that has been deleted on the source.  You don't want the delete first encase you make a big boobo and then suddenly delete all your files.
All the options with the "--" things can be shorted when you figure out how it all works.
Next you can make a script to have ti run with as little as a click of the mouse.
And after that? well I can show you how to make it run every night.
Tell me when your ready.

---

### Post by encompass on 2006-06-28
oh yeah... for got to tell you... rsync is cool cause it only makes the changes rather then ruin your drive with a hard copy.  Saves a pile of time too.

---

### Post by cssutto on 2006-06-30
I am very interested in what you have to say about rsync as I am working on how to back up my system and have not hit on exactly the right combination yet.

I have a dual boot and want to back up everything on my hard drive (laptop) to a USB Maxtor drive.

I have learned how to rsync a file or a directory, but I don't know exactly how to rsync the entire system without rsyncing the Maxtor onto itself.

In the code you give as an example, must source directory list each and every directory to be rsynced, or is there a shortcut like maybe ./* that would rsync the laptop drive to the Maxtor?

Your help will be much appreciated.

CSSJR

---

### Post by encompass on 2006-06-30
rsync does a pile of things... I thinkthey even have a front end for it... grsync or something like that search for it in synaptic.  But to be honest stay in the console when working with suck power.
Take this rsync a little further... once you have the backing up perfect to the way you want.  Tell me and I can show you how to put it in a script.  Then we can run it with something called cron.

---

### Post by cssutto on 2006-07-04
[QUOTE=encompass]well, not sure I can get you a gui... but don't worry, it is easy than you think to make a little program that can do it all for you.
The program I would recommend is called rsync. use man rsync to get the VERY long details about how it works.  or...
hmm let me see here... (googling...)
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/) mgiht be a help... you don't have to go over the net jsut to another mounted drive.  Nor do you have to start your own server.
```
rsync --verbose  --progress --stats --compress --recursive --times --perms --links /original_dir/* /sourc_dir/
```
Then just add the --delete so that it will delete anything that has been deleted on the source.  You don't want the delete first encase you make a big boobo and then suddenly delete all your files.
All the options with the "--" things can be shorted when you figure out how it all works.
Next you can make a script to have ti run with as little as a click of the mouse.
And after that? well I can show you how to make it run every night.
Tell me when your ready.[/QUOTE]

encompass:

My object is to copy my entire laptop hard drive to an external Maxtor drive.

The laptop is dual boot Ubuntu/W2K.

I want everything that is on the laptop in a directory which I named linuxbackup because I also have a backup utility that I run in W2K that backs up W2K into a separate partition.  I hope to do away with that when I get rsync where I want it.

So here is my question, which I hope you can help me with.

I took your command and modified it to what I thought would work on my system.

As follows:
rsync --verbose  --progress --stats --compress --recursive --times --perms --links //* --exclude=/media/*  --delete /media/LOCAL DISK-1/linuxbackup 

I have not yet run it with the --delete option.  That scares me.

Ubuntu named my exteral Maxtor, which has three partitions, LOCAL DISK, LOCAL DISK-1 and H: -1.

The command line I have tried rsyncs everything to the linuxbackup folder.  In other words, it rsyncs LOCAL DISK-1 onto itself.

As the Maxtor drive and its partitions are listed in the file browser as /media/LOCAL DISK-1, etc., I thought I could prevent that with --exclude=/media/*, but that is not working.

I also get many many folders in the linuxbackup folder that have only numbers for names, starting with the number 1.  These folders all have 17 files and all of them are exactly the same.  A few of thess folders are:attr, fd, task, etc.

Why do these repeat over and over?

Many questions, I know, but I am new to Ubuntu, only 60 dyas or so, and I want to get this rsync thing right so a crash does not make me have to reconstruct my system from scratch.

Help would be appreciated.

CSSJR

---

### Post by aysiu on 2006-07-04
There's a GUI for *rsync* called *grsync*.

*kdar* will also do differential backups.

---

### Post by cssutto on 2006-07-04
grsync does not enable you to exclude files, or at least I know not how, and it does the same thing.  It copies the external disk over itself

---

### Post by aysiu on 2006-07-04
[QUOTE=cssutto]grsync does not enable you to exclude files, or at least I know not how, and it does the same thing.  It copies the external disk over itself[/QUOTE]
So what? [quote=OP]hopefully something with a gui interface[/quote] There's no mention about the need to exclude files.

---

### Post by cssutto on 2006-07-04
Yes, I did specifically mention excluding files.

I also mentioned that not excluding files will cause the external Maxtor to be copied over itself because when you rsync /*, you are rsyncing everything in your system and everything connected to it unless you exclude.

Or at least that is what is happening to my system.

CSSJR

---

### Post by aysiu on 2006-07-04
I was referring to the original post-er (OP), lime4x4, not you. I thought you were offering help, not asking for it...?

---

### Post by cssutto on 2006-07-04
It appears that I had the  exclude in the wrong place.

rsync --verbose  --progress --stats --compress --recursive --times --perms --links --exclude=/media/* //*  /media/LOCAL DISK-1/linuxbackup 

seems to work.  It is running in another window now and so far, no copying the external drive over itself.

I would still appreciate any comments encompass might have on my command line.

CSSJR

---

### Post by lime4x4 on 2006-07-04
grsync works for me esp since i only want to backup 2 ot 3 folders onto another drive

---

### Post by cssutto on 2006-07-04
Well, that one did not copy the W2K files because they were in /media/*

So this looks more like it:

  sudo rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/* --exclude=/media/LOCAL\ DISK/* --exclude=/media/H_\ \ \ \ ~1/* //*  /media/LOCAL\ DISK-1/linuxbackup


This is running now in a command line window and appears to be copying W2K files as well as linux files from the hard drive in my lap top to the external Maxtor without copying the Maxtor over itself.

CSSJR

---

### Post by aysiu on 2006-07-04
By the way, people may already know this, but I found out the hard way today that *rsync* does not work with FAT32.

I was trying to set up an easy backup for my wife's Powerbook, and I was banging my head trying to figure out why it wasn't working.

Formatted her external hard drive to HFS+, and now everything's hunky dory.

---

### Post by nanotube on 2006-07-05
might also want to look at rdiff-backup ([http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) and also available in repositories). handy and powerful backup software.

---

### Post by cssutto on 2006-07-05
[QUOTE=aysiu]I was referring to the original post-er (OP), lime4x4, not you. I thought you were offering help, not asking for it...?[/QUOTE]


Well, I need help as much as anyone.

My last attempt copied all linux stuff.

It copied some W2K stuff from hda1, nothing from hda2 or hda6.

CSSJR

---

