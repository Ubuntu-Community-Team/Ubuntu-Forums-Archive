---
title: "Q: keeping two directories synced"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by aleska on 2007-05-02
Is there a straightforward way, say with a bash script and cron, to keep the contents of two directories synced?  I'm looking to keep my home directory (and subdirectories') contents synced with a directory (and respective subdirectories) on a mounted network attached storage device (NAS).  I want it so that if I add a file to either location, it adds it to the other (not necessarily an instantaneous sync - but once a day thing).  If I change/edit/update a file in one, it recognizes which version was edited most recently and updates the other directory accordingly.  I don't envision edits occurring on the same doc in both locations simultaneously...so no sophisticated document versioning required, nor document locking.  

I'll be satisfied with the sync occurring each day, once a day.  The result should be a mirror.  What's in the local directory has an exact copy backup on the NAS, and vice versa.  

I would be interested is learning how scripting can be used to do this; but if there is an application I should be using, I'd love to learn about that too.  I'd love to learn about the various options for doing this.  

Many thanks in advance!

---

### Post by lamalex on 2007-05-02
maybe check out this? [http://www.conduit-project.org/](http://www.conduit-project.org/) I've never used it but it might suit your needs.

---

### Post by starcraft.man on 2007-05-02
I'm not sure as I haven't done this myself, but I think you may be looking for one of these programs.

[Here!]("http://linuxappfinder.com/backupandrecovery/filesynchronizing")

LinuxAppFinder always has a solution when its a program you need :)

---

### Post by aleska on 2007-05-02
Awesome, I will definitely check out those sites to see what programs they recommend.  

While I'll probably go with one of those apps, is there anyone who's bash savvy, that might have some ideas on the bash scripting approach to doing this?  I know "find" for instance has options such as "-mtime _n_" to find files modified within _n_days ago.  It also has option "-newer _file_" where file found was modified more recently than _file_.  Unfortunately, I'm just learning about piping and grep and find and everything else command line.  

Even if I wind up going with one of the applications that have been created for this, I think it would be extremely good for learning to see how this could be done with commands and scripting.  For me, at least, this is how I learn best (in this case, seeing how commands and scripting can be used to tackle a real world problem).

Anyone want to share their mad skillz, and educate us?  :)

---

### Post by compmodder26 on 2007-05-02
The rsync command is what you want.  Type "man rsync" in a terminal to view the manual for it.

---

### Post by rhodry on 2007-05-02
I think 'rsync' could be close to the command you are after. There is a good 'man' page and there are plenty of good tutorials on the web - just google for 'rsync tutorial'.

Just to give you some feel for how it works:

I have the line below, as well as a similar line for a number of other key folders in my home folder, included in a bash script. The script is set by cron to run every night. It is a simple backup methodology for me.

 rsync -azv --progress --delete /home/paul/public /media/disk/backup/feisty

The /media/disk/backup folders are on an external usb hard drive that is more or less permanently mounted.

CAVEAT - you need to understand the rsync parameters before using them! eg the lack of a / at the end of folder definitions is very important. The use of the --delete option is important to understand.

This will give you one-way sync. In this scenario, files are only created on the main machine and the 'sync' is a one-way backup. If you are going to allow the files to be  edited on the backup drive from other sources then this command (with --delete) will be a problem. There is another program called 'unison' that may be better suited.

I suggest you read up on both (they are both in repos) and post back with any detailed questions.

Hope this helps, cheers,
Paul.

---

