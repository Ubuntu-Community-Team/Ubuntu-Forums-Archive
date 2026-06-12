---
title: "backup and restoring home directories with nautilus"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Roger D on 2008-02-07
Hi

I'm trying to develop a really simple, scrpt-free, way of being able to save and restore my home directory.

The idea is to be able to restore most of my existing system in the event of a major failure, like a hard disk crash. I envisage that, should this happen, I'd replace the hard disk, do a new system install, during which I'd create a home directory for roger (that's me). I then envisage replacing this new roger directory, with my old roger directory, which I'll have archived on an external hard disk. I hope, somebody tell me if I'm wrong please, that this approach will restore all my existing email files and contact list in Evolution.

Using Nautilus, it's dead easy to archive my home directory. I just right click on roger in the home directory, select create archive, and then select my external hard disk as the destination. The trouble occurs when I try and go the other way. I really just don't know what to do. I've tried copying the archive file into the home directory, but my system won't let me do this.

Any ideas, anybody?

Roger D

---

### Post by emarkd on 2008-02-07
Check this out:  [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)  You should be able to modify it to suit your needs.  Yes, you'll probably want to write it into a script, but it'll be simple ;)

---

### Post by mikeyphi on 2008-02-07
OR you could try the Simple Backup package available through Synaptic (sbackup)

That program will allow you to regularly back up whatever you want - there is a simple GUI to help!!
Reinstalling is also via a simple GUI....and you can choose what you want to restore.

---

### Post by Roger D on 2008-02-07
Appreciate the advice, but backup is an absolutely critical function, and users need to have total confidence in the tools they're using so:

I don't want to use a complex script  I don't understand - what do I do if it doesn't work? Also, I tried simple backup, and I'm not happy with that either. The GUI is not esecially intuitive - just try selecting a specific directory, and, even when I do that, and manage to saving something to my external hard disk (I've no idea what this is, as it doesn't appear to be related to the directory I'm trying to archive) my hard disk refuses to eject. So, sorry, I don't think Simple Backup is the answer either.

Roger D

---

### Post by wickstopher on 2008-02-07
I use kdar, which is a KDE graphical frontend for dar (disk archiver).  Very easy, works just fine in GNOME or KDE, and allows for differential backups, i.e. once you have made the initial backup archive, when you want to do a new backup it will create a new file with only those files that have changed or are new since your last backup.  It's also a very simple interface for restoring the archives that you've created.  It's not in the gutsy repos (for some reason, they took it out for Feisty), but it's very simple to download the .deb packages from the website.

here are the links you'll need:


libdar3c2a (pre-requisite for installing the kdar package):
[http://packages.ubuntu.com/dapper/libs/libdar3c2a]("http://packages.ubuntu.com/dapper/libs/libdar3c2a")

kdar:
[http://packages.ubuntu.com/dapper/kde/kdar]("http://packages.ubuntu.com/dapper/kde/kdar")

hope this helps!

---

### Post by emarkd on 2008-02-07
Did you check out the [link]("http://ubuntuforums.org/showthread.php?t=35087") I provided?  There's no script there, just a few commands with descriptions so you'll be able to understand them.  Just an option...

---

### Post by Roger D on 2008-02-07
The Kdar documentation certainly looks impressive - I'll have a careful look through it. But this is all a long way from my original simple request - I can easily create an archive of my home directory using nautilus - is there an equally easy way I can use this archive file to restore my home directory?

Sorry to be banging on about this - I'm committed to using Linux/Ubuntu, but there's a crying need for backup tools that match those available in on, dare I say it, more mainstream desktop systems.

Roger D

---

### Post by wickstopher on 2008-02-07
Well, using the method you're using, all you have to do is move/copy the archive wherever you would like it to go, right click on it, and select the option to "extract here."  Easy enough.  If you're restoring a home directory, you'd have to run nautilus with root permissions.  This is assuming that your HD failed and you have to reinstall the OS, with the archive backed up on an external drive.

from a terminal:
```
sudo nautilus &
```

then remove the home directory that was installed with the operating system, copy your archive into the root directory, and extract.

Is this what you were looking for?

I'd still recommend kdar over this option.  It is far more flexible.  You can break the archive into slices (for burning to disc, or if your storage device is using a filesystem with a filesize cap a la fat32).  You can choose various methods of compression.  I go with the no compression option, as it is much quicker to backup and restore, and the difference in the archive size is negligible.  And you can do differential backups without having to back everything up all over again.  It took a few minutes to figure everything out, but it's really quite simple and highly flexible.

---

### Post by fiddledd on 2008-02-07
Simple answer to your original question is yes. But it involves copy/pasting, not sure exaclty what you are looking for but:

**sudo tar cvfzp Path_To_Archive/Name_Of_Archive.tar /home/roger**

will back up your Home folder with all permissions intact and all files/folders

and:

**sudo tar xvf <name_of_archive>.tar**

will restore All the Files/folders

Wait for someone else to confirn this is OK first as I haven't used Ubuntu (or Linux) for many months :)

---

### Post by philinux on 2008-02-07
I prefer the differential backup as it takes less time after the initial backup. Try grsync it's in synaptic.

---

### Post by Roger D on 2008-02-07
Thanks everybody. You've all given me some really helpful advice. I'll experiment with the various suggestions, and have a good look at grsynce.

Roger D

---

### Post by jevidl on 2008-02-07
Just a note on diffs... 

Diffs are quite useful, and can certainly help keep your backups a manageable size. Just makes sure that you keep in mind you'll need the original full backup to restore as well as the diff. Generally the process is something like Restore Full > Restore Diff... the diff backup (usually) only backs up files that have changed *since the last backup*

---

